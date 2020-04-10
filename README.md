This project is based on an example and dataset from a Data Science course developed at Berkeley (Data8.org).
Joshua Balbi

File Overview

This code is rather straIghtforward to use. All you need to be able to do is to download a file which contains 2 parameters and 1 classification, of lengths of your choosing.

For part 2 of the code, all that is needed is an x list, a list and a list and then a new pair of points which can be whatever points you decide from 0-1 or even use the built in random point generator called tescase(). part two returns the nearest neighbor of the test case and its classification and graphs your random point as well as the color corresponding to the classification

For part 3 of the code, not much has changed regarding variables. The only thing that has changed is that k is the number of nearest neighbors that the point is looking for and will choose the majority class of the odd number of nearest neighbors and its color will correspond to the chosen class.

For part 4 we still have x and y for the list as well as the class p but we add on k which is how many clusters are desired and m how many times do we want the points to update. The goal of this code is to determine the k amount clusters in the data set, without using classification. classification comes in handy when figuring out the sensitivity and the specificity of the graph.


Function overview

PART 2 functions:

	scale(l): scales any list to a 0-1 scale with parameters a specific list with 158 elements. the list is used for many other functions ahead
	
	color(Class): depends on the class which is a list of 1 and 0s returns a new list that replaces 0 with red and 1 with blue

	testcase(): takes no parameters and just returns two different random integers from 0-1
	
	DistanceArray(newpoint,x,y):takes the distance between a random point newpoint and x list and y list. it returns a list l with all the distances
	
	nearest neighbor classifier(newpoint,x,y): this function  uses the distance array function to find to find the minimum distance of the function, then find its index and use that index with the list p which is class and returns a 0 or 1
	
	newcolor(newpoint,x,y):has three parameters: newpoint which is a list of 2 numbers and x and y which are lists that get converted with scale. it uses the parameters and the function nearest neighbor classifier to find whether it is 0 or 1 and with that information returns red if class=0 or blue if class=1.

	graph testcase(newpoint,x,y): has three parameters. a list of two points called newpoints a list of x and a list of y. it scales x and y and graphs them. it uses the function color to determine the color of the point. the new point is also graphed and made clear with size 100 and color is made clear with the function newcolor.
	
PART 3 functions:

	scale(l): scales any list to a 0-1 scale with parameters a specific list with 158 elements. the list is used for many other functions ahead

	DistanceArray(newpoint,x,y):takes the distance between a random point newpoint and x list and y list. it returns a list l with all the distances

	kNearestNeighborClassifier(k,x1,y1,x,y): this function takes in 5 parameters k= how many neighbors nepoint list are 2 Random points assigned by the user and x and y are lists used and scaled. it gets all the distances the previously named distance array and after it sorts them with their indices and gets the first k amount of indices then with arithmetics it figures out if there are more 1 values or 0 values

PART 4 FUNCTIONS file contain all the function that part 4 is using:

	scale(l): scales any list to a 0-1 scale with parameters a specific list with 158 elements. the list is used for many other functions ahead
	
	select(k): function randomly selects values from 0-1 using a parameter k as in how many clusters are desired and it prints 2*k amount of random points to have an x and y value for the centroid
	
	assign(k,v,x,y): takes on 4 variables, k= how many clusters desired, v=a list of integers 0-1 depending on the k using select(k) and x and y are lists the function makes a list of k empty lists and then appends to them if the index of the list matches the index of the closest centroid to a point afterwards it loops through the k amount of lists made and attains the smallest distance and corresponding index which then is used to determine the color
	
	update(k,v,x,y): takes 4 parameters: amount of clusters=k v= indexlist attained from assign, points x and y are the lists. what this function does is it takes v which would be the index list acquired from assign and would then append the corresponding points that are closets to it into a list that would be summed up and divided by length to attain the mean or the new centroid and this would be done k amount of time
	
	iterate(k,m,x,y): takes 4 parameters k= amount of clusters, m amount of  times iterated x and y are the lists that need to be scaled. this basically just loops through m amount of times to get the desired centroids=v color=c and index=a. it does this by going through assign and using assigns values as variables for update and using updates return value as variable for assign. this does it m amount of times and then returns a,c,v.
	
	new_pt_color(k): this prints out k amount of colors for the centroids and is necessary for it to identify the centroids and their clusters
	
	sensitivity(I,C): produces the sensitivity of the graph by attaining the amount of true positives and then attaining the amount of all actual positives and dividing the two the last if statement is because sometimes the data does not add up and 1's are actually supposed to be zeros 
	
	specificity(I,C): produces the specificity of the graph by attaining the amount of true negatives and then obtaining the amount of all actual negatives and dividing the two the last if statement is because sometimes the data does not add up and 1's are actually supposed to be zeros  

