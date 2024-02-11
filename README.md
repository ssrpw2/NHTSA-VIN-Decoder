# VIN Decode SQL Database and Excel Processing Tool

This repository contains a comprehensive setup for VIN decoding. The databse is NHTSA's standalone database, from year 2022. An updated version that works with NHTSA's 2024 database is in the works. 
## Getting Started
- **Database Import:** Begin by importing the `.bak` file into SQL Server Management Studio to set up the VIN Decode database. [Download the SQL database backup here](https://github.com/ssrpw2/NHTSA-VIN-Decoder/releases/tag/v1.0)
Instructions are provided in the Word document.
- **VIN Decoding:** Use the SQL script to decode VINs. Follow the instructions to execute the script within SQL Server Management Studio.
- **Data Processing:** After decoding, use the provided Excel form to process and manage the output data.
  
## Installation
1. Import the `.bak` file into your SQL Server instance.
2. Implement the stored procedure using the provided SQL script.
3. Open the Excel form and configure it to connect to your SQL database.

## Usage
- Detailed step-by-step instructions for each part of the process are included in the Word document. Refer to it for setting up, decoding, and processing your VIN data.
- The Excel form is for use with the SQL database output.
- The Excel form was originally made for a research project where the electrification level was needed for vehicles, so that battery electric vehicles (BEVs) and hybrid electric vehicles (HEVs) could be identified.
