Part 1: Explore the Data
1. The Python notebooks contain the code for exploratory analysis and some insights related to the data quality
2. The Data Updated folder contains the updated data files (from above Python exploratrory analysis)
   	a. These updated data files were used for SQL Analysis
  	b. Added a Google Drive link as well for all the data files (since some files are > 25 MB)

Part 2: SQL Analysis
1. The SQL files contain the code for the analysis
		a. Top_5_Brands_By_Receipt.sql - What are the top 5 brands by receipts scanned among users 21 and over?
		b. Top_5_Brands_By_Sale.sql - What are the top 5 brands by sales among users that have had their account for at least six months?
		c. YoY_Growth.sql - At what percent has Fetch grown year over year?

Part 3: Communicate with Stakeholders
1. Present in the 'Communicate with Stakeholders.pdf'
2. Some high priority data issues that need to be addressed:
	1.	Only ~0.5% of users in the Transaction data were mapped to the User data
			i.	This limits the insights we can generate related to users (age/joining date/demographic)
			ii.	Needed: Improved mapping of the user data to generate useful user level insights
	2.	Transaction data with missing Barcodes
			i.	~10% of transactions do not have a barcode
			ii.	Needed: Improved mapping of Barcodes to generate product level insights
	3.	Barcodes in the Transaction and Product data are stored as integers and are of varying length
			i.	This creates an issue, since any barcode with zero as the first digit(s) might get dropped while being transferred from/to a csv file
			ii.	Solution: Resolved by converting Barcodes to string and making it a string of length 14
	4.	Missing Brand and Manufacturer information in Product data
			i.	~26% of products are missing the brand and manufacturer information
			ii.	Needed: Get Brand and Manufacturer information for the missing products 
	5.	In Transaction data, we have some duplicate records where the combination of Receipt ID and Barcode appears more than once. Specifically, in these cases:
			i.	The Final Sale is missing
			ii.	The Final Volume is zero
			iii.	Solution: Resolved by dropping the duplicate rows
