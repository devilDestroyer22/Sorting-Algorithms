Important! Please read before experimentation.

Selection Sort: It is an algorithm responsible for finding the minimum element within an array and sorting it from the beginning. It is then sorted accordingly and arranged in a particular manner.  

Insertion Sort: It is a sorting algorithm that is responsible for building the final array one item at a time. The items within the array or list are compared against one another and arranged in a particular manner. Either from ascending to descending; vice versa.  

Bubble Sort: It is an algorithm, responsible for comparing the adjacent element and swapping them, should they be in an incorrect order, and the items are checked and swapped within the list until they are in a correct order.  

These three algorithms were used and compared them to each other, and since they have the same time complexity, it was easier to compare the algorithm and their time complexity is O(n^2). Despite being aware of each resilience, through actual experimentation would I be able to check whether each algorithm is prone to SDC errors, or which ends up crashing or which ends up becoming the most resilient of them all.  

Instructions to run the code: 

1.) Open Ubuntu Virtual Machine and open the terminal

2.) Type: git clone https://github.com/devilDestroyer22/Sorting-Algorithms.git 
Once cloned, the repository shows up in the terminl. (use ls to find it, and cd to change to the respective directory). Use cd to navigate through randomFI, to run a random fault injection. (Make sure to change the trials to 1000 in input.yaml using vim, and the timeout to 10 seconds). 

3.) To run fault injections on the three sorting algorithms: 
Compile insertion-sort.c, selection-sort.c and bubble-sort.c to readable IR:
clang -emit-llvm -S *.c (Repleace the *.c with one of the three .c algorithm files).

4.) Once compiled, a .ll file is produced, so use lli use one of the .ll files to see if the results were produced sucessfully. 
Upon doing so, use Instrument IR-level codes to readable IR:
instrument --readable insertion-sort.ll to run and so and so forth for the remaining two algorithm files. 

5.) Next, Run a fault-free IR:
profile ./llfi/sqrt-profiling.exe

6.) In order to run the random fault injections: 
Fault Injection: run a fault-injected IR:

injectfault ./llfi/sqrt-faultinjection.exe

This would run a series of 1000 trials and determine whether the errors and resilience within the algorithm. 

7.) Finally, after successfully running the fault injection, we use:
Analyze FI results:
python3 measure.py

This would produce the overall results of benign count, crash count and SDC count. Through this, we can determin the resiliency and vulnerabilities of a sorting algorithm, and comapre the probability over a 1000 trials to the other respective algorithms. 

In order to do the same for other algorithms, use rm -rf llfi* results.txt to remove the results of insertion sort and repeat the steps above to check the fault injection trials and results for each sorting algorithm. 

The sorting algorithm code was was written by DaniloNovakovic and only using it for running faultinjections, and is only being referenced and tested for my final project. Thanks. 

