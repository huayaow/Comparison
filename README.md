# An Empirical Comparison of CT, RT, and ART

This repository is supplementary to the following paper **"An Empirical Comparison of Combinatorial Testing, RandomTesting and Adaptive Random Testing"** submitted to TSE.



### Abstract

We present an empirical comparison of three test generation techniques, namely, combinatorial testing (CT), random testing (RT) and adaptive random testing (ART), under different test scenarios. This is the first study in the literature to account for the (more realistic) testing setting in which the tester may not have complete information about the parameters and constraints that pertain to the system, and to account for the challenge posed by faults (in terms of failure rate). Our study was conducted on nine real-world programs under a total of 1683 test scenarios (combinations of available parameter and constraint information and failure rate). The results show significant differences in the techniques’ fault detection ability when faults are harder to detect (failure rates are relatively low). CT performs best overall; no worse than any other in 98% of scenarios studied. ART enhances RT, and is comparable to CT in 96% of scenarios, but its execution cost can be up to 3.5 times higher than CT when the program is highly constrained. Additionally, when constraint information is unavailable for a highly constrained program, a large random test suite is as effective as CT or ART, yet the test generation cost is significantly lower than that of other techniques.



### Subjects

We use six programs from the [Software Infrastructure Repository (SIR)](http://sir.unl.edu/portal/index.php): FLEX, GREP, GZIP, SED, MAKE and NANOXML [[Petke 2015\]](http://ieeexplore.ieee.org/document/7081752/); and three highly-configurable programs: DRUPAL [[Sanchez 2017\]](https://link.springer.com/article/10.1007/s10270-015-0459-z), BUSYBOX and LINUX [[Medeiros 2016\]](https://dl.acm.org/citation.cfm?doid=2884781.2884793).

For each program we provide:

- **Test model**, **[NAME].model** (the `subject` directory): the test model of a program, including all relevant parameters, values and constraints.
- **Corpus of fault**, **[NAME].bug** (the `subject-bugs` directory): the fault triggering test cases or parameter-value combinations of each fault.
- **Test Scenario**, **[NAME].scenario** (the `scenario` directory): all combinations of PARA, CONS and RATE of a program, and the set of detectable faults for each choice of RATE (these faults have the same failure rate).
- **Test suite**, **[NAME]/[PARA_CONS_STRENGTH_TECHNIQUE].ca** (the `testsuites` directory): test suites generated by a particular testing technique, where {0, 1, ..., m-1} is used to represent m values of a parameter.

A more through explanation of the above files can be found [here](DETAILS.md).



### Data

The data obtained with respect to each test scenario, i.e. each combination of **<PARA, CONS, RATE>**, can be found in the `all-data` directory. In each **[NAME].all.data **file, each row gives the result of a test scenario: the first four numbers are the covering strength and the choices of PARA, CONS and RATE; the next three numbers are the average proportion of faults detected by CT, RT and ART; the last is the group of favorable techniques determined by Tukey’s HSD test. 

The Figures and Tables, with respect to each subject program, for answering research questions can be found in the `figures` directory.



### Code

The source code (Java, IDEA project) for test suite generation and evaluation can be found in the `src` directory.

To generate test suites of CT, RT and ART for a program, run

```
java -jar generation.java [NAME] [STRENGTH]
```

To evaluate the fault detection ability of CT, RT and ART for a program, run

```
java -jar evaluation.java [NAME] [STRENGTH]
```
