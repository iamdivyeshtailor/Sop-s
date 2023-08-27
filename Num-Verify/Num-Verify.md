### Num-Verify

### step-1:- 
- Put Today excel file in new folder and name that folder with Todays's Date
- and also put converter (excel) file and the file in which you will add excel data 
#### Step-2:-
- Now open Today's excel file and converter file both
- Then first go to converter's file and Delete all the record from 1 column
- and now  select all data from today's excel file and paste it in converters's sheet
- now create new excel sheet in same folder and New.excel
- now copy second and third column ( EXTRACTED NUMBER AND EXTRACTED NAME ) from converters sheet
- and paste ( "PASTE AS VALUE  / DONT DO NORMAL PASTE " ) it in the New sheet 

- now select all and find duplicate and then filter them 
	- ( Go to Home -->  Conditional  Formating and then select --> Duplicates value )
	- and then apply Filter ( Go to data --> and then select Filter )
	- now apply filter
	- ### Now Find Duplicates value
		- and then click on filter by cell color 
		- now select the colored data ( which you get ) and now copy and paste it into a new sheet of a same excel file
				-   and also paste this data in INPUT DUPLICATES RECORS sheet in MAIN excel file
				- and also add numbers of data in the index sheet of main file in  (COUNT OF DUPLICATES NUMBER)
		- and then remove duplicates  from then ( Go to data --> and remove Duplicates)
		- only tick mark on ( EXTRACTED NUMBER ) and remove tick mark drom ( EXTRACTED NAME) and then click on okay
		- now remove filter
		- and do the same in sheet 1 


- Now close the Converters File and dont need to same ( Never Save the convertesr file )
- Now copy the new sheet data ( All Name and Number ) and paste it in a IP.excel sheet ( Dont Copy header)
- and then save as it as comma delimited csv 
- and then upload it to numverify.webcase.me 

Till this happes


- Delete old data from MAIN file like ( ALL INDIA  / GUJARAT /  LOCATION NOT FOUND ). Dont delete the header
- after you downloads the both files ( Phones-details-others / Phones-details-selected )  
- open both of this files and delete the date section from both. by selecting  date header and (Home --> Delete)
 
- Now Copy all data except header and put Phone-details-selected data in gujarat sheet / and Phone-details-others data in india sheet
- Now filter mumbai location data from india sheet and copy then from indian sheet and paste them in gujarat sheet and after paste delete those mumbai data (values) from india sheet.


	Now keep gujarat sheet as it is and go to india sheet
	- Now first find the count of all number without carrier 
	- And add filter in carrier sheet and select blank 
	- and count the no ( eg  20/ 30 )and add that value in index sheet of COUNT OF UNFOUND CARRIER .
	- now do the same for location Header ( add filter and select blank  )
		- and count the no ( eg  20/ 30 )and add that value in index sheet of COUNT OF UNFOUND LOCATION.
	- copy those data and paste in LOCATION NOT FOUND sheet in index
	- after that delete those data from all india sheet ( home--> delete )


NOW need to refresh ( Data --> Refresh all )


DONE