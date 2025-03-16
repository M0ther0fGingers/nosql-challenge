# nosql-challenge
Module 12 Challenge

## Folder Structure
The nosql-challenge folder contains the jupyter notebook files for this challenge: NoSQL_analysis_starter.ipynb and NoSQL_setup_starter.ipynb. The setup file should be run first. The subfolder, Resources, contains the establishments.json databse to load. 

## NoSQL_setup_starter.ipynb
*Part 1*
 Import the data from establishments.json via terminal. The new database is named uk_food, collection establishments. 
   - Load dependencies and connect to port 27017
   - print databases to verify up_food was created and review the establishments. 

*Part 2*
1. Add new restaurant. 
   - New restaurant is Penang Flavours. Copied the values from the challenge 12 information and used an .insert_one function. 
   - Used a print statement to verify it was added successfully using 
2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen"
   - Wrote a query and limited to the BusinessTypeID and BusinessType fields.
   - used a .find on the establishments collection 
   - pprint the results.
3. Update the new restaurant with the BusinessTypeID
   -  use .update_one function on establishments to add the ID
   -  write a query to find Penang Flavours and pprint the resutls to verify the BusinessTypeID field was updated. 
4. Find and remove all the Dover restaurants. 
   - use .deletemany to find all resturants with LocalAuthoritName of Dover
   - Print the numer of documents deleted. 
   - Rerun the search for Dover restaurants to verify none remain. 
   - Use a .find_one to verify other documents remain. 
5. Convert data types
   - Change the lat and long to Decimals. Use an .update_many, $set, and $toDecimal to update all. Lat and long are in the geocode dictionary, call using geocode.longitude
   - Use a .find_one to verify datatypes changed.  
   - non_ratings list provided. Any ratings with text should be changed to null. Use .update_many $in non_ratings list, $set to None. 
   - Then update the datatype of RatingValue to in int. Use .update_many and $toInt. 
   - Write a for loop to print the fields and data types updated. Verify they are correct. 

## NoSQL_analysis_starter.ipynb
*Part 3*
Load dependencies and connect to the database. 
1. Find establishments with a hygiene score of 20
   - write a query to find scores.Hygiene of 20
   - count the results in establishments
   - use pprint to show 1 document
   - Convert the results to a pandas DataFrame. 
   - print the number or rows and a use a .head(10) to print 10 results.
2. Rating value greater or equal to 4
   - write a query using $regex to find anything with London in LocalAuthroityName
   - use an $and statement to filter by both conditions 
   - use count_documents to find the number of results. 
   - print the first result
   - Convert the results to a data frame and use .head(10)
3. Rating value of 5
   -  I did this section in 2 different ways. 
   -  First way: Searched for the lat and long in the database. Set the lat and long as variables and called those variables in the query. This way was easy and worked well, however, it's not easily updated. it's manual. 
   -  Alternative way: This way is more work. The degree_search needs to be converted to a float and the lat and long are called from the database, then converted to a float. Those variables are called int he query. This method is less work in the future because the find_lat and find_long variables can be updated with a new restaurant name rather than finding, copying and pasting new lat and long each time. 
   -  Converted the results to a pandas Data Frame. 
4. Count establishments with a Hygiene score of 0
   - Write a query to find Hygiene scores of 0
   - Group by the LocalAuthorityName
   - Sort by the count 
   - Set up a pipeline and print results. 
   - Convert to a DataFrame 
