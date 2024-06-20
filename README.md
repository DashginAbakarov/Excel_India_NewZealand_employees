# India_NewZealand_employees
-Short summary:

-- In my data task, I started by turning two sheets of messy data into tables named "India" and "New Zealand".
--After a quick look, I saw that I needed to clean the data. 
--I used Power Query to combine the tables and added a "country" column to each one. 
--I fixed missing gender values and date formats. 
--After cleaning, I analyzed the data to count employees and find averages for salary, age, and how long employees have been at the company.
--I also figured out the percentage of female employees. 
--I used formulas and Power Query to easily get and filter data, helping me understand specific departments and other details better.

-Detailed explanation:
--1. First, we had messy data. We selected all and used CTRL+T to make a table.

--2. Secondly, we had two Excel sheets in our file. It was hard to identify the tables we created for both.

--Therefore, we gave names to both tables as "India" and "New Zealand" (Table Design > Table Name).

--3. Thirdly, we did a quick analysis (count of rows, average salary, etc.). To find the average salary, we clicked on the last row of the salary column to calculate the number of rows.

--4. However, this analysis did not make sense because we had not cleaned the data. 
--To identify duplicates, we selected the column, went to Home > Conditional Formatting > Highlight Cell Rules > Duplicate Values.

--5. Before removing duplicates, we needed to combine both the India and New Zealand tables together. 
--We selected the India table, went to Data > Get Data > From Table/Range. Then, we duplicated our India table and changed the duplicated table to New Zealand. 
--In the Formula bar, we typed Excel.CurrentWorkbook(){[Name='New Zealand']}[Content] and pressed Enter.

--6. We also added an additional column named "Country" for each table, filling it with "India" and "New Zealand" values (Custom Column > Name: "Country", Custom Column > "India" and "New Zealand" accordingly).

--7. Now, since each table had a different column arrangement, we combined them using Home > Append as New > selected India and New Zealand, and named our appended table "India and New Zealand."

--8. We replaced null values with "Other" in the gender column using the Replace command (because we did not know the gender of those individuals).

--9. We also had a date column with unidentified numbers. We clicked on the column and chose Data Type > Date.

--10. We saved and closed Power Query and started our analysis. We quickly analyzed "count of employees, average salary, average age, average tenure (how long employees had been in the company), and female employee ratio."
--It was better to type the formula itself instead of choosing a column in the formula to count employees: =COUNTA(tableName[columnName]), =AVERAGE(tableName[columnName]), etc.

--11. To calculate tenure, we created a new column named Tenure. Then, we used =TODAY() - first cell of the date column and dragged it down to calculate the rest (essentially subtracting the start date of employment from today's date). 

--12. We could also divide all values by 365 to get years instead of days.

--13. We could also use the median (which is advantageous as it provides a median value to identify unnecessary outliers).

--14. To find the female ratio of employees, first, we counted female employees using =COUNTIFS(tableName[columnName], "Female").

--15. We also found out how many employees had a salary higher than 90000 using =COUNTIF(tableName[columnName], ">90000").

--16. To extract information about a particular employee, for example, Yagna Sujeev, we used =XLOOKUP(employeeName, tableName[nameColumn], tableName[[column2]:[lastColumn]]). 
-- This allowed us to take the name, look it up in the name column, and return all other columns except the name column. We could also use TRANSPOSE(XLOOKUP(..)) to get information vertically and then create a table. 
--The main advantage of XLOOKUP is its dynamic nature; when we change the name (input), it automatically finds the appropriate information.

--17. If we wanted to find all the information for only the "Sales department," we typed "Sales" into a cell and used =FILTER(tableName, tableName[departmentColumn] = cellWithSalesDepartment).
-- For example, if we wanted to choose specific columns (such as age, salary, and country) appropriate for the Finance department, we used =CHOOSECOLS(FILTER(tableName, tableName[departmentColumn] = cellWithFinanceDepartment), columnNumbersSeparatedByComma).

--18. We could also sort our information according to a particular column, for example, the Salary column: =SORT(CHOOSECOLS(FILTER(tableName, tableName[departmentColumn] = cellWithSalesDepartment), columnNumbersSeparatedByComma), salaryColumnNumber, -1), where -1 means descending order.

--original project:https://www.youtube.com/watch?v=H6k28jhclwI&t=4759s 
