# Parallel Computing

## 1. Distrubuted Parallel Computing
* Architecture of the solution - The architecture of the solution we created consists of a main.c file that has the capabilities to multiply two given matrices via txt file, as well as the ability to multiply matrices from sizes 1-1000 and automatically output the results to a graph. Along with the normal way of multiplying matrices, we are able to multiply the matrices using SIMD, OMP, and MPI separately. This is done by having each separate way of multiplying the matrices either in their own files or functions.
* Variations of algorithm - We used four different types of algorithms for this project. They include normal mmult, SIMD (vectorized mmult) with and without optimization, OpenMP and MPI. 
Normal mmult - This matrix multiplication algorithm uses nested loop to multiply different values together. It adds up the multiplied values of first two matrices number of times for the output matrix to be completed.
SIMD - This is a vectorized mmult algorithm that uses SIMD that again uses nested loop with the difference from normal mmult where it sets the each value in output matrix to 0 and multliply the values in other matrices to the closer values in the machine. As seen this is faster than normal mmult, as it uses the values that are closer in the machine.
OpenMP - This algorithm uses multi-threading with abstraction. This is done by using the #pragma directive. In our case, we said shared(a, b, c, aRows, aCols, bRows, bCols) to let OMP know that we want these variables to be shared between threads and private(i, k, j) to tell OMP that we want these to be local variables per thread. Along with #pragma omp parallel to initialize a parallel region, then #pragma omp for to let OMP know that we want the multi-threading region to be within the for loop. Then it will take care of the mult-threading part for you as it does the mmult algorithm.
MPI - MPI mmult is implemented by using the Wolfgand cluster provided for us, it uses the different nodes in the cluster as different processes that can each do different actions. The basis of is shown by clarifying your master process and your slave processes. We then use the master process to send each slave process a row of data from a matrix to perform matrix multiplication on. Therefore, we can send different rows to different slave processes from the master process and compute faster than if we only had one process. The slaves then send back the computed data to the master process to be combined into one final output matrix.

## 2. Teamwork
* Anthena Evans - Fiddled with chinook the most probably. For the first day worked on accessing chinook and wolfgang cluster. For the first week, helped write the code for task 2, 3, and 4. Also madde the gnuplot graph for the first week. For the second and third week, debugged mmult_omp.c and explained the task to others. Also made resulting gnuplot graph.
* Hamsa Nandana Shaik - Took part of connecting our system to wolfgang cluster and task of first day. For the first week, did research on different approaches we use in this project and did the documentation part. In the later weeks, wrote the initial code and modifications for task 4 and task 5 and wrote most of the readME documentation
* Ronald Rajan - Took part in reviewing how to get onto the wolgang cluster. During the second week, wrote the code for task one and did testing. Then wrote code for task 2 and did more testing along with Athena. Contributed to the testing and coding of task 4 and 5. Wrote parts of the readME documentation.

We locked the master branch of this repository to block merging of code automatically which made us review each other's work. Each of our team members created our own branches to work on the tasks. We consistently kept informed on what work each of us had been doing through discord and informed when a work is done and pushed into their own branch of github so that other team members would review and discuss about them and move forward if not make modifications and resolve conflicts.

## 3. Full project life cycle

## Different models of Parallel Computing
* We used Trello board to plan and manage our project. We used it to first plan what we have to do this week and the other week for each person, in the beginning. Later in the week, we moved the tasks that we finished to the done column, the tasks we were working then currently to doing column and tasks that had to be done later in to do column. This is how we used the board to keep updating on the progress of the project. The link to our board is https://trello.com/b/fb8XKXnN/shaikevansrajancrazyparallel

* Yes, our cycle for this project was basically the usual writing code, compiling, running and testing the code. One of us used terminal from the IDE(intelliJ and VSCode) and connected to wolfgand cluster through it, but still the cycle was pretty much the same. The others used putty and command prompt to connected to the cluster

* The testing was to observe the observe the time taken taken per multiplication is increasing or decreasing as the size of the matrix gets bigger. The other testing observation was to compare the output of matrices by the multiplication using different algorithms. We think the basic mmult code given to us is with out flaws. But we had edit the code for the timing.

* We used the code given to us in the intitial commit to generate the random matrix or specific sizes. This was done with the gen_matrix(int n, int m) function found in the mat.c file. The specfic size for the matrix was passed to the function with the variables n and m for the rows and columns size. The function returned a dynamically-allocated array of doubles which could then be used for testing.  We verified that the matrices created were of the right size by using the print_matrix(double a, int n, int m) function which was also given in the mat.c file. Having this code given to us was very useful becasue it enabled us to spend time on testing rather than finding out if we had generated the correct type of matrix. 

* We did not have time to automate the graphing process. We instead had the various mmult c programs write to text files. This was compiled into a nicer format for the online gnuplot. The graphs and data.txt files were then saved and uploaded to this git repo.

* The proportion of time and tasks dedicated to writing variations of mmult and testing/reporting the multiplication was about even. As we added more variations of mmult, we realized that we needed to change how we tested/reported the information. Therefore, there was a large amount of time dedicated to both parts of the project.

This is the graph produced showing the different ways we ran the program from tasks 2 and 3 with the data from task 1.

![image](https://user-images.githubusercontent.com/78066498/158232302-d70db865-b748-41ec-97ca-517d683f1185.png)

This is the graph produced showing the different was we ran the program for with data from mmult_omp.c

![image](https://user-images.githubusercontent.com/70277494/160462726-a29a2411-7835-499c-af05-8e47130c1846.png)
