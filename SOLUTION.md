# Lab 03: Task inputs comparison solution

## Steps
-----
1. **Which task(s) are cacheable but are still executed instead of being resolved from the cache?**

    The test task is cacheable, but experienced a cache miss.
2. **Which inputs are impacting task cacheability?**

    Starting with this comparison of the two examples.
    You will notice a task called `generateTimestampsProperties` contains a timestamp and therefore is not cacheable.

3. **How would you fix the timestamp problem? Apply those changes before moving forward.**
    You don't really need that task so remove it from the build.
      Don't forget to also remove the configuration that depends on `generateTimestampProperties`.
      For volatility that you can't just remove, use normalization as specified in the Gradle documentation: https://docs.gradle.org/current/userguide/more_about_tasks.html#sec:configure_input_normalization

4. **Are all cacheable tasks being resolved from the cache or does some volatility remain?**

    Yes, the volatility is gone and all the cacheable tasks now come from the cache.

5. **Are the avoidance savings for these builds better or worse than the builds that included timestamp files?**

    The avoidance savings is better for the fully cached build: 0.205s to 1.205s for the examples.
