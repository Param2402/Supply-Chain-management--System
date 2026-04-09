# Supply Chain Management
# Team : Apes 

Project Overview
The following paper is an account of a C#.Net console application that was created in imitation of the inventory management processes of a furnishing warehouse. The implementation depends on Binary Search Tree (BST) designed and built customly that acts as the key in-memory data storing and is connected to a Microsoft SQL Server database called SupplyChainDb to guarantee the presence of persistent data storage.

Key features:
 Identifier based retrieval of items, with average time complexity O (log n)
 Categorical retrieval of items.
 Production of a detailed inventory report in terms of ItemID.
New inventory records (this key is auto-generated in a SQL IDENTITY column)
Deletes of stock records.
Sales transactions
Recording of restocking operations (remained to the database)
Creation of a low-stock report.


Before carrying out the application, ensure that the following parts are installed:


Visual Studio 2022 (Community edition or greater)8.01.1421.387
.NET Framework  4.7.2 
SQL Server Express 2019 or 2022 
SQL Server Management Studio (SSMS) 



Database Setup

This step should be done before to the application is run.

1. Connected to-db: Right list of databases.
2. Connect to a local server instance
3. Select New Query
4. Run the entire contents of `Database/SupplyChainDb.sql`
5. To ensure that the updated message and that there are no errors, make sure that the message (20 rows affected) is displayed.

The script will:
Build the supplychaindb database.
Create the `Furniture` table
Note: Insert 20 sample furniture records (identifier values 10001-10020)

In case the database is present then the script will destroy the existing and create a clean database.


How to Compile and Run

Step 1 
1. Launch Visual Studio 2026
2. Click on file/open/ project solution.
3. Open from the project directory SupplyChainManagementSystem.sln

Step 2
1. Right tap the project SupplyChainManagementSystem in the Solution Explorer.
2. Select NuGet Packages Manager.
3. Click on Restore or go and search System.Data.SqlClient and install the package provided by Microsoft.

Clicking on the third step will prompt you to enter the Connection String (which may be nonexistent).
In case your SQL Server instance name is not the default one, open the Program.cs and change the line 

string connectionString = @"Server=.SQLEXPRESS; Database= SupplyChainDb;Trusted connection= True;


Step 4 
After selection you must press the button Ctrl+Shift+B or click the button Build  Build Solution. The output must show truth value of the succeeding of the build.

Step 5 
Press F5 (using debugger) or Ctrl+ F5 (no debugger). The console window will be displayed and it will give the main menu.


When starting up the system up-loads the 20 records of pre-populated furniture that are in the database into the BST by default. After that, the menu with the main items appears.

Option 1 
One can use a numerical Item ID (e.g. 10001) to access the full history of a single item, stock status, price, warehouse location and a cumulative sold/restocked count.

Option 2 
Click any category name and all the items will be listed. Valid categories are:
`Tables`, `Seating`, `Beds`, `Storage`

Case-insensitivity The category search is insensitive to case (e.g., case search allows tables, TABLES and Tables to be used interchangeably).

Option 3
View Full Inventory Report option will display every item located in the database

Option 4 
The user need to enter:
Item name
Category (`Tables`, `Seating` or `Beds and Storage`)
Price (in pounds sterling)
Initial stock level
Warehouse zone (e.g. Zone - Aisle 1)

Option 5 
Enter the Item ID to delete. There is a maintenance confirmation that comes before the deletion. The object is deleted on the BST and the data base.

Option 6 
Enter the ID of the item, and the quantity sold.
Exclude over the present inventory
Reduce StockLevel and raise the amount that is sold.
Then data into the database both.

Option 7
Enter the ID of the item and the amount to purchase. The system will:
Improve StockLevel and QuantityRestocked
Maintain the modified values to database

Option 8

Enter a stock limit number. Every item whose stocks have reached these levels are recorded. 

Option 9
the system exit 


Running Unit Tests

The solution has been integrated into a distinct MSTest unit-test project ( SupplyChain.Tests ) which has 18 test cases that check all BST functions and inventory management reasoning.

To run the tests
1. Make sure the solution is open in the Visual Studio.
2. Select Test → Run All Tests
3. All the 18 tests will be shown in the Test Explorer window and all will pass.

Test Cases
BSt insertion/ Search/ deletion (including leaf albums, nodes having two children, non-existed entries, and empty trees)
Furnitureitem Initially and initial value of the default property.
Stock selling and restocking incrementing logic.
Retrieval of maximum ItemID (GetMaxID) of a populated table and an empty table.
Stock specifications (maximum money to sell)