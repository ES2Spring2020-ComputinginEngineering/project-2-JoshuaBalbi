This project is based on an example and dataset from Data Science course developed at Berkeley (Data8.org).
Joshua Balbi

File Overview

This code is rather straught forward to use. All you need to be able to do is to download a file whihc contains 2 parameters and 1 classification, of lengths of your choosing.

for part 2 of the code, all that is needed is an x list a y list and a p list and then new pair of points which can be what ever points you decide from 0-1 or even use the built in random point generator called tescase(). part two returns the nearest neighbor of the test case and its classification and graphs your random point as well as the color corresponding to the classification

for part 3 of the code, not much has changes with regaridng variables. the only thing that has changed is that k is the number of nearest neighbors that the point is looking for and will take choose the majority class of the odd number of nearest neighbors and its color will correspond to the chosen class.

for part 4 we still have x and y for list as well as the class p but we add on k which is how many clusters are desired and m how many times do we want the points to update. the goal of this code is to determine the k ammount clusters in the data set, without using classification. classification comes in handy when figuring out the sensitivity and the specificity of the graph.


Function overview

PART 2 functions:

	scale(l): scales any list to a 0-1 scale with parameters a specific list with 158 elements. the list is used for many other functions ahead
	
	color(Class): depends on the class whihc is a list of 1 and 0s reutrns a new list that replaces 0 with red and 1 with blue

	testcase(): takes no parameters and just returns two different random integers from 0-1
	
	DistanceArray(newpoint,x,y):takes the distance between a random point newpoint and x list and y list. it returns a list l with all the distances
	
	nearestneighborclassifier(newpoint,x,y): this function  uses the ditance array function to find to find the minimum distnace of the function, then find its index and use that index with the list p which is class and returns a 0 or 1
	
	newcolor(newpoint,x,y):has three parameters newpoint whihc is a list of 2 numbers and x and y which are lists that get converted with scale. it uses the parameters and the function nearestneighborclassifier to find whether it is 0 or 1 and with that information returns red if class=0 or blue if class=1.

	graphtestcase(newpoint,x,y): has three parameters. a list of two points called newpoints a list of x and a list of y. it scales x and y and graphs them. it uses the function color to determine the color of the point. then new point is also graphed and made clear with size 100 and color is made clear with the function newcolor.
	
PART 3 functions:

	scale(l): scales any list to a 0-1 scale with parameters a specific list with 158 elements. the list is used for many other functions ahead

	DistanceArray(x1,y1,x,y):takes the distance between a random point x1 and y1 and x list and y list. it returns a list l with all the distances

	kNearestNeighborClassifier(k,x1,y1,x,y): this function takes in 5 parameters k= how many neighbors x1 and y1 are Random point assigned by the user and x and y are lists used and scaled. it gets all the distances the previously named distance array and after it sorts them with their indices and gets the first k ammount of indices then with arithmetics it figures out if there are more 1 values or 0 values

PART 4 FUNCTIONS file contain all the function that part 4 is using:

	scale(l): scales any list to a 0-1 scale with parameters a specific list with 158 elements. the list is used for many other functions ahead
	
	select(k): function randomly selects values from 0-1 using a parameter k as in how many clusters are desired and it prints 2*k ammount of random points to have an x and y value for the centroid
	
	assign(k,v,x,y): takes on 4 variables, k= how many clusters desired, v=a list of integers 0-1 depending on the k using select(k) and x and y are lists the function makes a list of k empty lists and then appends to them if the index of the list matches the index of the closest centroid to a point afterwards it loops through the k ammount of lists made and attains the smallest distance and corresponding index which then is used to determine the color
	
	update(k,v,x,y): takes 4 parameters ammountof clusters=k v= the select(k) points x and y are the lists. what this function does is it takes v which would be the index list aquired from assign and would then append the corresponding points that are closets to it into a list that would be sumed up and divided by lenght to attain the mean or the new centroid and this would be done k amount of time
	
	iterate(k,m,x,y): takes 4 parameters k= ammount of clusters, m ammount of  times iterated x and y are the lists that need to be scaled. this basically just loops through m ammount of times to get the desired centroids=v color=c and index=a. it does this by going through assign and using assigns valuesn as variables for update and using updates return value as variable for assign. this does it m ammount of times and then returns a,c,v.
	
	new_pt_color(k): this prints out k ammount of colors for the centroids and is necesary for it to identify the centroids and their clusters
	
	sensitivity(I,C): produces the sensitivity of the graph by attaining the ammount of true positives and then attaining the ammount of all actaul positives and dividing the two the last if statement is because sometimes the data does not add up and 1's are actually supposed to be zeros 
	
	specificity(I,C): produces the specificity of the graph by attaining the ammount of true negatives and then attaining the ammount of all actaul negatives and dividing the two the last if statement is because sometimes the data does not add up and 1's are actually supposed to be zeros  
