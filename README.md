# HASTIE_Corrected_HitRate_vs_Sensitivity

HASTIE is the file obtained through the procedure described in
 https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_hastie_10_2.html, it is suitable for testing AI algorithms, due to its simplicity and a number of registers that allows its use with low-performance computers.

However, it is observed that many records do not fulfill the condition of formation of the file:
y [i] = 1 if np.sum (X [i] ** 2)> 9.34 else -1. Taking into account that the accuracy of statistical results depend on the accuracy of the input data, not only on the algorithm, a Hastie file has been created in which all the records have the correct class assigned
and tests of hit rates and sensitivity have been carried out

Resources: Java 8 and Spyder 4.

Functioning:

The attached file Hastie10_2_20Corrected.txt is downloaded to disk C :, which will be the input for the tests (this file is the result of applying to the original HASTIE file: Hastie10_2.csv, which is attached, the program
HASTIE_sklearn_corrected.py, attached)

The application is going to be tested in Java, downloadable from https://github.com/ablanco1950/HASTIE_NAIVEBAYES.
Once the application is downloaded, you have to change the executable file Hastie_NaiveBayes.bat so that the only line it contains is

java -jar Hastie_NaiveBayes.jar C:\Hastie10_2Corrected.txt C:\Hastie10_2Corrected.txt 0.0 9600.0 9601.0 12000.0
In other words, the assignment to the Hastie10_2.csv file is changed to Hastie10_2Corrected.txt.

We will also test the HASTIE_sklearn_with_test_out_train.py program that presents the results of the SKLEARN classifiers: KNeighbors, GaussianNB (naive Bayes), RandomForestClassifier, AdaBoostClassifier and GradientBoostingClassifier.

The hit rate exceeds 99% in all cases.

To test the sensitivity, download the file C:\Hastie10_2_20Corrected.txt wich is formed with the last 20 records of C:\Hastie10_2Corrected.txt

The executable Hastie_NaiveBayes.bat is modified so that it refers to the new test file and the margins are adjusted,

java -jar Hastie_NaiveBayes.jar C:\Hastie10_2Corrected.txt C:\Hastie10_2_20Corrected.txt 0.0 11980.0 0.0 20.0

Set line 16 of HASTIE_sklearn_with_test_out_train.py so that it points to the new test file C:\Hastie10_2_20Corrected.txt

It is observed that all the procedures indicate 20 successes and 0 failures.

If the class of the first 5 records of C:\Hastie10_2_20Corrected.txt is changed, the error rate should give 15 hits and 5 misses, so all, but sklearn GaussianNB (Naive Bayes) gives 14 hits and 5 misses and RandomForest 16 hits and 4 failures.

If the class of the first 10 records of C:\Hastie10_2_20Corrected.txt is changed, it should give an error rate of 10 hits and 10 misses, that  the Java program gives when executing Hastie_NaiveBayes.bat and also all sklearn clasifiers except GaussianNB (Naive Bayes) that give 9 hits and 11 misses

If the class of the first 15 records of C:\Hastie10_2_20Corrected.txt is changed, it should give an error rate of 5 hits and 15 failures that gives the Java program  when executing Hastie_NaiveBayes.bat, KNeighbors, Adaboost and GradientBoost

sklearn GaussianNB gives 7 hits and 13 misses
sklearn RandomForest gives 6 hits and 14 misses

If the class of the 20 records of C:\Hastie10_2_20Corrected.txt is changed, it should give an error rate of 0 hits and 20 failures that  the Java program gives when executing Hastie_NaiveBayes.bat, KNeighbors,  Adaboost and GradientBoost, the rest gives the following values:

sklearn GaussianNB: 2 hits and 18 misses
sklearn RandomForest: 1 hits and 19 misses

Therefore, except for errors or omissions, and pending parametrizations of the sklearn classifiers, since the simplest version has been used, reduced to only three instructions to implement each classifier, an irregular behavior is observed in the sensitivity of GaussianNB and RandomForest clasifiers.

References:

https://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_hastie_10_2.html

Implementation of AdaBoost classifier

https://github.com/jaimeps/adaboost-implementation
