# Cleaning Data in SQL

This project involves cleaning and standardizing the `NashvilleHousing` dataset using SQL queries. The focus is on improving data quality by performing tasks like standardizing date formats, splitting address fields, updating missing values, removing duplicates, and deleting unnecessary columns. Below is an overview of the steps and transformations applied:

---

## Steps Performed

### 1. **Standardizing Date Formats**
- Added a new column `SaleDateConverted` to store the standardized date.
- Converted the `SaleDate` column to a proper `Date` format using the `CONVERT` function.

### 2. **Filling Missing Property Addresses**
- Identified records with null values in the `PropertyAddress` column.
- Used a self-join on `ParcelID` to populate missing `PropertyAddress` values with matching records.

### 3. **Splitting Address Fields**
- Split `PropertyAddress` into `PropertySplitAddress` (street) and `PropertySplitCity` (city).
- Similarly, split `OwnerAddress` into `OwnerSplitAddress` (street), `OwnerSplitCity` (city), and `OwnerSplitState` (state).

### 4. **Standardizing "Sold as Vacant" Field**
- Converted values in the `SoldAsVacant` column from `Y`/`N` to `Yes`/`No` for better readability.

### 5. **Removing Duplicates**
- Used a Common Table Expression (CTE) with `ROW_NUMBER()` to identify and delete duplicate rows based on key fields (`ParcelID`, `PropertyAddress`, `SalePrice`, `SaleDate`, `LegalReference`).

### 6. **Deleting Unused Columns**
- Dropped unnecessary columns, including `OwnerAddress`, `TaxDistrict`, `PropertyAddress`, and `SaleDate`, to streamline the dataset.

---

## SQL Highlights
- **Self-Join for Missing Data**:
  Populated missing addresses by joining the table on `ParcelID` and excluding rows with the same `UniqueID`.

- **String Parsing**:
  Used functions like `SUBSTRING`, `CHARINDEX`, and `PARSENAME` to extract specific parts of address fields.

- **Data Deduplication**:
  Applied a `ROW_NUMBER()` approach with a `PARTITION BY` clause to identify duplicate entries efficiently.

- **Conditional Updates**:
  Standardized categorical fields using `CASE` statements.

---

## How to Run
1. Ensure the `NashvilleHousing` table is available in your SQL Server database.
2. Execute the SQL queries step by step, ensuring the transformations are applied in the correct sequence.
3. Verify the output of each step before proceeding to the next.

---

## Possible Enhancements
- Implement data validation checks to ensure consistent results.
- Automate the cleaning process using stored procedures or scripts for repeated use.
- Incorporate error handling for edge cases, such as invalid or missing data formats.

---

## Conclusion
This project showcases foundational data cleaning techniques using SQL. By improving data quality, it lays the groundwork for more accurate analysis and reporting.

---

## Files Included
- SQL Script: `SQL Portfolio Data Cleaning.sql`
- Sample Dataset: `Nashville Housing Data for Data Cleaning.xls` 

---

For more details or to collaborate, feel free to reach out or submit issues via the GitHub repository!

