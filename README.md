Download Link: https://assignmentchef.com/product/solved-cs-550-assignment-5
<br>
Part I







<ol>

 <li>Compute the empirical distribution of the three types of irises in the iris dataset (see part II). Using the empirical distribution, compute the entropy of the iris species.</li>

 <li>Regularization is very likely to result in a learner not learning the training data as well, yet it is an important component of machine learning algorithms. What is regularization and why is it important?</li>

 <li>Assume the following knowledge base:</li>

</ol>

<em>nutrients</em>∧<em>water </em>∧ ⇒<em>sun  flower</em>

<em>flower </em>∧ <em>pollinator </em>⇒ <em>fruit</em>




<em>bat </em>∨<em>bird </em>∨ ⇒<em>bee           pollinator irrigation </em>⇒ <em>water </em>and the current set of facts:

<em>irrigation</em>∧<em>nutrients</em>∧ ∧<em>sun bat</em>

Without using the resolution rule, prove that fruit will be borne.

<ol start="4">

 <li>Given the wumpus world of Figure 7.2 from your book where position (x, y) denotes the cave in column x, row y (e.g. wumpus is at 1,3):</li>

</ol>







<ol>

 <li>What are the percepts for an agent at 2,3?</li>

 <li>Write a set of logical sentences (see section 7.4.3) that describe the predicates that can be inferred by percepts at 2,3. Do not include knowledge from any other position that could infer more details.</li>

</ol>

<ol start="5">

 <li>In addition to what we know about the starting conditions of a wumpus world, assume that a stench has been observed at locations (2,1) and (1,2). Write the knowledge base in conjunctive normal form and show whether or not the question W<sub>2,2</sub> (there is a wumpus at location 2,2) is entailed by the knowledge base using the resolution rule.</li>

</ol>

Part II:  Programming Assignment




The code package for this assignment on Blackboard contains a mostly complete implementation of several machine learning algorithms.  These algorithms are not implemented for speed and are only effective for toy problem sets.  If you want to use real-world machine learning problems after the course, there are more efficient libraries such as <a href="http://scikit-learn.org/">scikit-learn</a> which you will not be using here.




In module ml_lib.learning, you will find the following classes along with many classes that you do not need to worry about but are welcome to investigate:

<ul>

 <li>DataSet – Read a data set. Given the name argument, it will find the CSV data files that are located in ml_lib/aima_data.  Each data set has two files with different extensions: .txt – a description of the problem and data, .csv – the data in comma separated value format.  There are several datasets available: o abalone – 4,177 examples of attribute data to predict an abalone’s age from measurements taken from harvested (killed) abalone.

  <ul>

   <li>iris – 150 sets of measurements of characteristics of three species of iris plants, task is to predict the species: <em>Iris Setosa</em>, <em>Iris Versicolour</em>, or <em>Iris Virginica</em>.</li>

   <li>orings – Data from 23 NASA space shuttle launches prior to the Challenger crash. The task is to predict the number of o-rings that are likely to exhibit thermal stress.  Please note that unlike the other datasets, the attribute to predict is not the last one and you must use DataSet’s setproblem method identify the attribute to predict before calling the learning algorithm.  You might want to examine whether or not the mission number is relevant (not required for assignment).</li>

   <li>restaurant – Professor Russell’s restaurant waiting rules (no .txt file provided as the problem is explained in the book).</li>

   <li>zoo – 101 animals with numerical and boolean attributes, much like our flies/no flies example in class. Task is to predict broad classes of animals:</li>

  </ul></li>

</ul>

bird, fish, reptile, mammal, insect, amphibian, or shellfish.

<ul>

 <li>DecisionTreeLearner – Given a dataset, build a decision tree.</li>

 <li>NeuralNetLearner – Given a dataset, build a neural net. See caveats about the neural nets algorithm in the specification of driver.py</li>

 <li>cross_validation – Non-standard implementation of cross-validation. This one shuffles before each fold.   Takes a handle to a learning function, a DataSet, the number of folds k, and the number of times the cross validation is to be repeated.</li>

</ul>




Write the following:

<ul>

 <li>py – Write a standard cross_validation routine that has a similar interface to ml_lib.learner.cross_validation (feel free to reuse code). It differs as follows: o Return values are the mean error rate, the standard deviation of the error rate, a list containing the error rate for each fold, and a list of models trained.  Unlike the ml_lib package implementation, results on the training set are neither generated or returned (these usually aren’t all that useful other than as a sanity check).

  <ul>

   <li><em>Data are not shuffled</em>, resulting in every example being used N-1 times for training and 1 time for test.</li>

   <li>There is no trials parameter as running the same data multiple times would produce the same result.</li>

  </ul></li>

 <li>py – Write the following functions:

  <ul>

   <li>shuffle_data – Shuffles the example list.</li>

   <li>learn – Given a dataset, create a shuffled copy of the data. Run a 10 fold cross validation (std_cv.cross_validation) using decision trees and neural nets (DecisionTreeLearner and NeuralNetLearner).  The data are only shuffled once, so that std_cv.cross_validation will use the same exact training and test data on each of the folds for both learners.</li>

  </ul></li>

</ul>

Use the default options for NeurnalNetLearner, but you are welcome to explore if you are curious.  Hint:  The neural net implementation given does not work well on categorical data, DataSet.attributes_to_numbers will convert all categorical data to numbers.  Note that this is not always the best way to do this, sometimes we use so-called “one hot” vectors, a binary vector the length of the category list with a single bit set to one.  There are some advantages to this that are beyond the scope of this assignment.

Note that the abilone dataset is significantly longer than the other data sets, and you may omit running that one if you wish,

Sample output for one of the datasets.




<table width="819">

 <tbody>

  <tr>

   <td width="576">Mean StdDev Errors for each fold</td>

   <td width="96">Corpus</td>

   <td width="147">Learner</td>

  </tr>

  <tr>

   <td width="576">0.060 0.106 0.067,0.133,0.333,0.000,0.067,0.000,0.000,0.000,0.000,0.000</td>

   <td width="96">iris/75</td>

   <td width="147">DecisionTreeLearner</td>

  </tr>

  <tr>

   <td width="576">0.255 0.275 0.429,0.500,0.429,0.625,0.571,0.000,0.000,0.000,0.000,0.000</td>

   <td width="96">iris/75</td>

   <td width="147">NeuralNetLearner</td>

  </tr>

 </tbody>

</table>














