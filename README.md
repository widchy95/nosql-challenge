# UK Food Establishment Analysis

## Project Overview

This project involves querying and analyzing data from a MongoDB database containing records of UK food establishments. The database includes information such as business names, hygiene scores, geolocation data, and ratings. Key tasks include querying, updating, and aggregating data, as well as performing proximity-based searches and converting the results into Pandas DataFrames for further analysis.

---

## Key Steps

### 1. MongoDB Setup
- **Database**: The database `uk_food` is assigned, with the collection `establishments` containing the food establishment records.
- **Libraries Used**: 
  - `pymongo` for interacting with MongoDB.
  - `pandas` for data manipulation.
  - `pprint` for pretty-printing query results.

### 2. Querying Establishments with Hygiene Score of 20
- **Objective**: Find all establishments that have a hygiene score of `20` and convert the results into a Pandas DataFrame.
- **Steps**:
  - Use MongoDB's `find` method with a query matching the hygiene score of 20.
  - Convert the query result into a Pandas DataFrame.
  - Output the number of documents and display the first 10 rows of the DataFrame.

### 3. Querying London Establishments with RatingValue >= 4
- **Objective**: Identify establishments located in London with a `RatingValue` greater than or equal to `4`.
- **Steps**:
  - Use `find` with a query that filters by `LocalAuthorityName: "London"` and `RatingValue: {"$gte": 4}`.
  - Convert the results to a Pandas DataFrame and display the first 10 rows.
  - Count and display the number of matching documents.

### 4. Finding Top 5 Establishments Near "Penang Flavours"
- **Objective**: Search for the top 5 establishments with a `RatingValue` of `5` and sort them by the lowest hygiene score. The search is limited to establishments near the coordinates of the new restaurant, "Penang Flavours".
- **Steps**:
  - Use a proximity search based on latitude and longitude within 0.01 degrees.
  - Filter by `RatingValue: 5` and sort by `Hygiene` scores in ascending order.
  - Limit the results to the top 5 establishments.
  - Convert the results to a Pandas DataFrame and print the output.

### 5. Aggregation Pipeline for Hygiene Score of 0
- **Objective**: Identify establishments with a hygiene score of `0` and group them by local authority, sorted in descending order by the number of establishments per authority.
- **Steps**:
  - Use an aggregation pipeline to:
    1. Match establishments with `scores.Hygiene: 0`.
    2. Group them by `LocalAuthorityName` and count the number of establishments in each group.
    3. Sort the groups by count in descending order.
  - Convert the aggregation result to a Pandas DataFrame and display the first 10 rows.

### 6. Data Type Conversion for Coordinates and Ratings
- **Objective**: Convert some string fields (like `longitude`, `latitude`, and `RatingValue`) to their appropriate numerical types.
- **Steps**:
  - Use `update_many` to:
    - Convert the string representations of `longitude` and `latitude` to decimal values.
    - Convert the string `RatingValue` to integers.
    - For invalid ratings like `"AwaitingInspection"`, set the `RatingValue` to `null`.

---

## Tools & Technologies
- **MongoDB**: For data storage and querying.
- **PyMongo**: To interact with the MongoDB database.
- **Pandas**: For data analysis and manipulation.
- **Python**: Core programming language used in the project.

---
