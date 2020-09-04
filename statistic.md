statistics
==========
- normal distribution test    
    - null hypothesis    
        The null hypothesis is target to test proving it is right.    

    - alternative hypothesis    
        Alternative hypothesis is the converse of null hypothesis. if it's probability of happen is low, null hypothesis' probability of happen is large.    

    - significance level            
        The significance level is a threshold of test for to reject the alternative hypothesis.    

    - significance probability    
        If a p-value lower than significance level, Null hypothesis has statistical significance. Because the probability of alternative hypothesis happen is lower than the significance level. So it is possible ignored.
    
    - Supremum
        The supremum (abbreviated sup; plural suprema) of a subset S of a partially ordered set T is the least element in T that is greater than or equal to all elements of S, if such an element exists. Consequently, the supremum is also referred to as the least upper bound (or LUB). (from [Infimum and supremum](https://en.wikipedia.org/wiki/Infimum_and_supremum))

    - Kolmogorov-Smirnov test    
        In statistics, the Kolmogorov–Smirnov test (K–S test or KS test) is a nonparametric test of the equality of continuous , one-dimensional probability distributions that can be used to compare a sample with a reference probability distribution (one-sample K–S test), or to compare two samples (two-sample K–S test). It is named after Andrey Kolmogorov and Nikolai Smirnov. (from [Kolmogorob-Smirnov test](https://en.wikipedia.org/wiki/Kolmogorov%E2%80%93Smirnov_test, 'Go wikipidia'))    
        K-S statistic seems like a distance of two distributions. So two distributions same each other when this value is small.    
        P-value is fitness of two distributions. So if p-value is small, the hypothesis reject.
        ```python
        import numpy as np
        from scipy.stats import ks_2samp
        d1 = np.random.normal(0, 1, 100)
        d2 = np.random.normal(5, 3, 100)
        d3 = np.random.normal(0.1, 1, 100)
        d4 = np.random.normal(0, 1, 100)
        print(ks_2samp(d1, d2))
        print(ks_2samp(d1, d3))
        print(ks_2samp(d1, d4))
        # Ks_2sampResult(statistic=0.78, pvalue=2.485563277850393e-30) two distribution isn't same
        # Ks_2sampResult(statistic=0.17, pvalue=0.11119526053829192) hard to reject hypothesis
        # Ks_2sampResult(statistic=0.09, pvalue=0.8154147124661313) hard to reject hypothesis
        ```

    - Anderson-Darling test    
        When applied to testing whether a normal distribution adequately describes a set of data, it is one of the most powerful statistical tools for detecting most departures from normality. K-sample Anderson–Darling tests are available for testing whether several collections of observations can be modelled as coming from a single population, where the distribution function does not have to be specified. (from [Anderson-Darling test](https://en.wikipedia.org/wiki/Anderson%E2%80%93Darling_test, 'Go wikipidia'))    
        ```python
        import numpy as np
        from scipy.stats import anderson
        d1 = np.random.normal(0, 1, 100)
        d2 = np.log(np.random.uniform(5, 10, 100))
        result1 = anderson(d1)
        result2 = anderson(d2)
        print(result1)
        print(result2)
        # AndersonResult(statistic=0.3570325666514407, critical_values=array([0.555, 0.632, 0.759, 0.885, 1.053]), significance_level=array([15. , 10. ,  5. ,  2.5,  1. ])) d1 is normal distribution
        # AndersonResult(statistic=1.2907562110531217, critical_values=array([0.555, 0.632, 0.759, 0.885, 1.053]), significance_level=array([15. , 10. ,  5. ,  2.5,  1. ])) d2 is not normal distribution
        ```    
        The critical values are threshold of p-values. So if statistic value exceeds critical values, then the hypothesis of normality is rejected with some significance level.
        
    - Skewness    
        Skewness is a measure of the asymmetry of the probability distribution of a real-valued random variable about its mean. (from [Skewness](https://en.wikipedia.org/wiki/Skewness, 'Go wikipidia'))
        ```python
        from scipy.stats import skew
        import numpy as np
        print(skew(np.random.normal(0, 1, 10000)))
        # -0.009365932076406375 
        ```
        If the skew value is positive, the right side by mean skew. Negative is opposite. The negative values is opposite.