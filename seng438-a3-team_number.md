**SENG 438 - Software Testing, Reliability, and Quality**

**Lab. Report #3 – Code Coverage, Adequacy Criteria and Test Case Correlation**

| Group \#:      |     |
| -------------- | --- |
| Student Names: | Aayush Dahal    |
|                | Justin Kuhn    |
|                | Sheroze Nasir    |

(Note that some labs require individual reports while others require one report
for each group. Please see each lab document for details.)

# 1 Introduction

White box testing is a widely used software testing technique that is used to create and improve upon test suites using a testing framework of choice. It is different from Black box testing, in that Black Box testing only considers the external behavior of a system, while White box testing does not. With White box testing, the internal workings of the system are visible to the testers, and the source code can be directly analyzed and used to create high quality unit tests. In this lab, we will use JUnit 4 to improve upon our test suite from the previous lab, as well as EclEmma to measure the coverage of the unit tests we develop.

Another objective of this lab is to apply various coverage techniques of White box testing to further improve our code. These techniques are line coverage, branch coverage and method coverage. Line coverage means writing tests to cover all the lines of source code in the SUT, branch coverage means writing tests to cover all the possible branches in the SUT, and method coverage means writing tests to cover all of the methods present in the SUT.  Through combining these three techniques, we will be able to develop a stronger test suite, and account for most of the coverage faults that slipped through our first round of testing.

By the end of this lab, we will have gained experience with a coverage tool, and be able to apply concepts of White box testing to future software projects. We will be able to measure control and data flow coverage, and analyze source code to effectively design unit tests. Ultimately, this lab will increase our experience with software testing, teamwork, group management and peer programming.


# 2 Manual data-flow coverage calculations for X and Y methods

Text…

# 3 A detailed description of the testing strategy for the new unit test

Our first step was to run our old test suite (RangeTest & DataUtilitiesTest) from A2 with EclEmma to see the coverage percentage of Statement, Branch and Method in the Range and DataUtilities class respectively. Our old coverage percentages for Range are the following; 33.6% statement, 24.4% branch and 60% method. Our old coverage for DataUtilities are the following;  48.7% statement, 32.8% branch and 60% method. We designed a test plan to improve Statement, Branch, and Method coverages in both Range and DataUtilities class utilizing white box testing principles. The first step before starting to write tests was to familiarize ourselves with the code of Range and DataUtilities classes. This gave us a solid understanding of implementation of all methods that we intend to test, this allowed us to design test cases based on implementation details which is the intended goal of white box testing. 

## Range

Our plan was to take note of all the yellow and red highlighted areas on the Range.java file that were revealed with EclEmma. Then we would add a plethora of new test cases that would be able to access all the previous lines that were not previously touched. We repeated this process until we had suitable test coverage for a statement percentage of 92.4%. To increase the branch coverage, we wrote additional test cases tackling all branches of the methods until we had a suitable branch percentage of 92.7%. We also added test cases to test previously untouched methods such as Scale, GetLowerBound, etc. which helped our method coverage percentage rise to 100%.

## DataUtilities

Similar to the Range testing strategy, our first step was to test the coverage of the old DataUtilities test suit that made use of black box testing. We checked the statement, branch, and line coverage of the DataUtilities class with the old test suite. We observed the yellow and red highlighting on DataUtilities.java that indicate uncovered lines, as well as the red dots that indicate not all paths of a branch (not all cases of a conditional) are covered. To get higher coverage, we wrote test cases for methods in DataUtilities that weren’t tested in assignment 2 and we made sure to test all methods in DataUtilities to maximize coverage. While writing test cases, we kept in mind that we ideally want to reach all statements/instructions and we focused on covering both branches of every conditional. For instance, for a conditional ``if(a==null)`` we would make sure to write test cases that cover both branches of the conditional, one that covers the case ``a==null`` and another one that covers the case ``a!=null``. 


# 4 A high level description of five selected test cases you have designed using coverage information, and how they have increased code coverage

2 test cases from DataUtilitiesTest and 3 test cases from RangeTest have been selected.

## DataUtilitiesTest

- **public void testClone_noNullElements()** 
  - **Target method:** DataUtilities - public boolean clone(double[][] source)
  - **Coverage information:** Running our original test suite with EclEmma revealed that this method had 0% line coverage, branch coverage and method coverage. 
  - **How it has increased coverage:** This test case increases the statement coverage to 100%, branch coverage to 75%, and method coverage to 100% for this method. This test case tests the clone method with a valid 2D double array with no null values i.e, {{1.1, 1.2}, {2.1, 2.2}}. This test case increases the statement coverage to 100% because the parameter used in this test causes all lines of the method to be traversed. The test case increases the method coverage to 100% since we tested the method. The test case increased the branch coverage to 75% because all branches of the for loop in the method are reached, and one out of two branches of if (source[i] != null) is reached - source[i] != null is reached and source[i] == null isn’t reached. The branch coverage is 75% and not 100% because one branch of the if conditional is not reached, that branch being the case of a null value in the array (if source[i] == null). A test case with a null value in the 2D array like {null, {2.1, 2.2}} fulfills this other branch.

- **public void testCalculateColumnTotalArr_highValidRowsValue()** 
  - **Target method:** DataUtilities - public static double calculateColumnTotal(Values2D data, int column,  int[] validRows)
  - **Coverage information:** Running our original test suite with EclEmma revealed that this method had 0% line coverage, branch coverage and method coverage. 
  - **How it has increased coverage:** This test case increases the statement coverage to 95.3%, branch coverage to 75%, and method coverage to 100% for this method. This test case tests the calculateColumTotal method with a validRows array {0,1,5}. This test case increased the statement coverage to 95.3% as it reaches all lines of the method in-test besides one unreachable line . This test increases the branch coverage to 75% as one branch for if(total>0) is reached - total > 0 is reached and total < 0 isn’t reached, both branches for if(row<rowCount) is reached, and one branch for if(n!=null) is reached - n != null is reached and n == null isn’t reached.

## RangeTest

- **public void equalsComparingToIncompatibleObject()**
  - **Target method:** Range - public boolean equals(Object obj)
  - **Coverage information:** Running our original test suite with EclEmma revealed that this method had 0% line coverage, branch coverage and method coverage.
  - **How it has increased coverage:** This test case was designed to target the first branch in the equals() method, which checks if the passed-in object is an instance of Range. In this case we pass in null, and expect to receive false as the return value. By adding this test case, we increased the line coverage for this method to 75%, the branch coverage to 66.7% and the method coverage to 100%.

- **public void scaleWithNegativeFactor() throws IllegalArgumentException**
  - **Target method:** Range - public static Range scale(Range base, double factor)
  - **Coverage information:** Running our original test suite with EclEmma revealed that this method had 0% line coverage, branch coverage and method coverage.
  - **How it has increased coverage:** This test case was designed to target the first branch in the scale() method, which checks if the provided factor is negative. If it is, we expect an exception to be thrown. By adding this test case, we increased the line coverage for this method to 60%, the branch coverage to 50% and the method coverage to 100%.

- **public void public void isNanRangeNaNLowerBound()**
  - **Target method:** Range - public boolean isNaNRange()
  - **Coverage information:** Running our original test suite with EclEmma revealed that this method had 0% line coverage, branch coverage and method coverage.
  - **How it has increased coverage:** This test case was designed to target the first branch in the isNaNRange() method, which checks if the base Range’s lower and upper bound is NaN. In this case, we are only providing a NaN lower bound, so we expect false to be the output. By adding this test case, we increased the line coverage for this method to 100%, the branch coverage to 25% and the method coverage to 100%.

# 5 A detailed report of the coverage achieved of each class and method (a screen shot from the code cover results in green and red color would suffice)

Text…

# 6 Pros and Cons of coverage tools used and Metrics you report

We used Eclemma as our coverage tool. During our testing, Eclemma was already pre-installed with J-unit which made it convenient and allowed us to begin testing efficiently and as soon as possible. The integration was smooth and came with no problem. As a coverage tool, Eclemma was easy to read and understand as it has a very friendly user interface which is easy to access and observe the three required metric coverages; statement, branch and method. The coverage tool however, gave a coverage percentage of multiple different metrics on top of the three required metrics and highlighted each statement in the java file with either red, yellow or green. The highlighted colors are used to represent the coverage status of each line; with red being a line of code that has not been executed, yellow being a line that has partially been executed and green being a statement that has been fully and properly executed. The coverage tool also indicates if both branches of a conditional are met or not, making it easy to identify branch coverage; a red dot indicating that both branches aren’t covered, yellow indicating only one branch is covered, and green indicating both branches of a conditional are covered.  When using Eclemma we experienced no crashes or any technical or faulty problems with the coverage tool and found it to be a very powerful tool for whitebox testing. 

Below is a table showing Eclemma’s pros and cons that we ran into while doing the assignment:

| Pros  | Cons |
| ------------- | ------------- |
| Provides different types of coverage percentage metrics  | Percentages can be difficult to interpret and may be misleading. A high percentage also doesn't always guarantee that the tests are effective.   |
| It helps identify different lines of code that need more testing or identify lines that are properly covered.  | The highlighted colored lines in the files do leave some ambiguity.  |
| Easy to use and has a user friendly interface  | Is limited when it comes to more complex testing.  |


# 7 A comparison on the advantages and disadvantages of requirements-based test generation and coverage-based test generation.

## Requirements-based test generation

**Pros**
- Have a predefined set of requirements to base your tests on.
- Simpler process since testing only requires understanding requirements and doesn’t require gaining an understanding of the implementation which can often be time consuming.
- Tests are less complex since they are designed based on requirements/user behavior rather than complex implementations.

**Cons**
- Can miss parts of the software design & implementation since there is no access to the implementation.
- It can be much harder to understand the root cause of an issue when there is a failure/error.
- Analyzing test coverage is infeasible.


## Coverage based test generation

**Pros**
- Provides an opportunity to view existing coverage and improve upon it based on testing goals.
- Helps to analyze program flow and to find bugs in program flow.

**Cons**
- Good coverage tools are hard to come across.
- Code coverage tools can be difficult to integrate into your project setup for your testing goals.


# 8 A discussion on how the team work/effort was divided and managed

- The entire team performed code coverage analysis on both Range & DataUtilities classes with the assignment 2 black box test suit. We decided to do this as a team so we could understand the code coverage percentages of black box testing. Analyzing code coverage as a group gives everyone a good understanding of an important learning objective -  how code coverages differ between black box and white box testing. 
- As for writing test cases, we decided to divide work by classes - 2 members were assigned white box testing of the Range class and one member was assigned white box testing of the DataUtilities class with the main goal of increasing code coverage. 
- Upon finishing our test cases for both classes, the whole team got together to demonstrate their new test cases and how it improved code coverage. During this stage, both groups verified each other's test cases and suggested further improvements and applied them. Doing this as a group gave us an opportunity to give feedback, improvise, and it showed us how code coverage in whitebox testing differs from blackbox testing. 


# 9 Any difficulties encountered, challenges overcome, and lessons learned from performing the lab

The main difficulty our group encountered in this lab was errors (not failures) in test cases from A2 that utilized JMock in DataUtilitesTest.java which weren’t errors in the assignment 2 project folder. Our group overcame this problem by asking the following question; why did the tests not error out on the assignment 2 project directory but are erroring out in the assignment 3 directory? This quickly gave us an idea that we are likely missing JARS or libraries in the assignment 3 directory which were imported in the assignment 2 directory, and that the mock tests are failing because JMock requires some library/JAR to be imported. Upon a quick cross check in the build path of a2 and a3 , we found out that we were missing 2 hamcrest JAR files in the assignment 3 directory that are needed to compile JMock mock tests (we missed these 2 JARS bc they weren’t a part of the given a3 jar files - see feedback for more info). Another difficulty we encountered was some of the branches being unreachable. Due to the way some conditions were designed, not every branch could be covered, which led to frustration as we tried to figure out how to access a certain branch. Eventually, we realized these were unreachable and moved on.

# 10 Comments/feedback on the lab itself

Overall, our group felt that this lab was a great introduction to Whitebox testing, and it was useful to get hands-on experience coding test cases. The lab gave us hands-on experience on how to use EclEmma to check for code coverage, how to analyze code coverage statistics and how to design test cases to improve code coverage. We enjoyed looking at the code coverage for our old test suite, then viewing the codebase and designing test cases to improvise coverage in our new test suite; it was a very intuitive and enjoyable process. However, there were two missing hamcrest libraries in the artifacts (from a2) which caused there to be a lot of errors in the DataUtilities unit tests. Next time, it would be beneficial to students to have all the required libraries included in the artifacts, as this would save a lot of time and confusion.
