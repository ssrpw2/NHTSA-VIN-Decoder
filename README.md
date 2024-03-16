# VIN Decode SQL Database and Excel Processing Tool

This repository contains a comprehensive setup for VIN decoding. The database is NHTSA's standalone database, from year 2022.  
## Getting Started
- **Database Import:** Begin by importing the `.bak` file into SQL Server Management Studio to set up the VIN Decode database.Instructions are provided in the Word document.
- [Download the SQL database backup here](https://github.com/ssrpw2/NHTSA-VIN-Decoder/releases/tag/v1.0) .
- **VIN Decoding:** Use the SQL script to decode VINs. Follow the instructions to execute the script within SQL Server Management Studio.
- **Data Processing:** After decoding, use the provided Excel form to process and manage the output data.
  

## Usage
### General Information:

* Product Information Catalog and Vehicle Listing (vPIC) Analytical User's Manual 2020: [https://crashstats.nhtsa.dot.gov/Api/Public/ViewPublication/813252]
* Data will always export as a 2 row x 8 column table. This allows sorting in the Excel form that has been provided. 
* Columns A-F  will populate: VIN, Year, Make, Model, Body Style, HEV/BEV Label (in this order)
*	If error code #4 or #11 is associated with the VIN decode process from the SQL query, the cells will display `error`.




### Steps for Decoding
* Download the database from this repository
* Download Microsoft SQL Server Management Studio
* Run the SQL script to create a new stored procedure
* Use notepad++ to copy 10,000 records at a time into Microsoft SQL Server Management Studio 
	* Syntax is below. 
		* Replace `[VIN]` and `[YEAR]` with the VIN and the model year (if available)
		* Replace `[databaseName]` with the name of the database that was backed up.
* VINs should be able to be decoded at a minimum rate of 1000 VINs/minute. 
	* Process 10,000 VINs at a time to optimize speed. The excel sheet is set up to take a maximum of 10,000 records. 
* Query results will need to be set so that the output is to a bar “ | “ delimited file. This prevents problems with columns that are comma delimited (the output text can contain commas which causes issues in the alignment of the data)
```sql
	USE [databaseName]
	GO
	EXEC [dbo].[spVinDecode_v4] @v = [VIN], @year = [YEAR];
```
### Importing NHTSA's Database into SQL Server Management Studio
* After downloading the database from this repository, unzip the file and place in the C-drive
* Open SQL Server Management Studio. Right click `Databases` select `Restore Database...`
	* Under `Destination` name the database. 
* Select `device` and click `...`  then click `add`
* Locate the `.bak` file, select it, click `ok`

### Creating the Updated Stored Procedure 
* Right click on the database, select New Query
* Paste the SQL Code into the Query tab that opens
* Select execute
* The stored procedure is now available for decoding.

### SQL Code


SQL script to create a new stored procedure is linked below. This needs to be run in Microsoft SQL Server management Studio to create a new stored procedure that processes VINs properly. Use with the 2022 database located in this repository (not compatible with the newer versions from NHTSA).
* [spVinDecode_v3](https://github.com/ssrpw2/NHTSA-VIN-Decoder/blob/main/spVinDecode_v3.md) is the version with the most strict handling for error messages
* [spVinDecode_v4](https://github.com/ssrpw2/NHTSA-VIN-Decoder/blob/main/spVinDecode_v4.md) is a version that only produces an error in the decode results for codes #4, #11, and #8.
  



	
