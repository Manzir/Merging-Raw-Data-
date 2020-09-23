# Merging-Raw-Data-
Meging NSSO Raw Data
One of the ways we can combine multiple data sets is merging them
But before we merge we must know the structure of data we are working on and the type of merge that we want to do
There are 4 types of merges that we can use to combine our data sets  and depending upon the required data sets we combine them.
In NSSO We have commonly two types of files  HH that is HH (1) Containing HH information and Individuals  (M) that is the many persons from whom information about different issues is collected
So to combine them we can use the follwoing commands in Stata depending on the files we are using 
Using HH 1:m Unique ID using "Ind File"
Using IND m:1 Unique ID using "HH File"
*HH IS Household file is the file containing HH characteristics of many Individuals.
#in the first file we are using HH as primary file that we first open in stata
*IND is many information about the individual belonging to their particular HH
* Unique ID is the ID that we use as a ID VARIABLE to combine the the HH and IND data sets.
Example 
Level 1 = HH data
Level 2 = Ind Data
HHID Unique ID in both files 
Remember HHID ID must be unique that is free from any duplicates
Steps 

* Open HH data 
Step 1
 **use "E:\sa\Level_1.dta", clear
 **isid HHID
 **sort HHID
 **save, replace
 Step 2
 **clear 
 **use "E:\sa\Level_2.dta", clear
 **isid HHID
 **sort HHID
 ** save, replace
 Step 3
 **use "E:\sa\Level_1.dta", clear
 **merge 1:m HHID using "E:\sa\level_2.dta"
 Your merging is done 
 To keep only the number of observations that you have in your ind file
 use the follwoing command 
 **keep if _merge==2
 You can apply this on any data set to merge them 
 Similarly we can merge the data while using other methods which will be shown in later
 For any queries mail datacomputics@gmail.com
 
