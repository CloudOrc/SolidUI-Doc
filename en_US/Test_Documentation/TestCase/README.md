SolidUI Test Case
-------------------------

## Modules

### Log in

| Test Scenario | Input | Expected Output |
| --- | --- | --- |
| Correct username and password | Correct username and password | Successful login |
| Incorrect username and password | Incorrect username and password | Login fails with error message |
| Empty username and password | Empty username and password | Login fails with error message |


### Data Source Management


| Test Scenario | Input | Expected Output |
| --- | --- | --- |
| Display data | None | Display all data sources, including serial number, data source name, data source type, user, description information and operation buttons |
| Add MySQL data source | Data source name, data source driver, URL, user name, password, remarks | After adding successfully, you can see the new MySQL data source in the data source list |
| Add Doris data source | Data source name, data source driver, URL, user name, password, remarks | After adding successfully, you can see the new Doris data source in the data source list |
| Edit data source | The name of the data source to be edited, the new data source driver, URL, user name, password, note | After editing successfully, you can see the edited data source information in the data source list |
| Delete a data source in a single line | The name of the data source to be deleted | After the deletion is successful, the data source will no longer be displayed in the data source list |
|Add data source, the name is empty | Empty string | Failed to add, and an error message is prompted |
|Add MySQL data source, URL/user/password is empty | Data source name, data source driver, URL, empty string, password, remark | Failed to add, and an error message is displayed|
|Add Doris data source, URL/user/password is empty | Data source name, data source driver, URL, empty string, password, note | Failed to add, and an error message is displayed|
|Edit data source, the name/URL/user/password is empty | The name/URL/user/password that does not exist is empty |Editing fails and an error message is prompted |
| Data Source Expired | Single Row Select Data Source Expired | Success |


### Project Management


| Test Scenario | Input | Expected Output |
| --- | --- | --- |
| Add project | Project name, project description, project URL | After adding successfully, you can see the new project information in the project list |
| Query Item List | Item Name | Output Item List |
| Edit project name | Project name | After editing successfully, you can see the edited project information in the project list |
| Delete Item | The name of the item to be deleted | After successful deletion, the item will no longer appear in the item list |
| Add item with empty name | Empty string | Failed to add with an error message |
| Add an item, the description is empty | Empty string | After adding successfully, you can see the new item information in the item list, but the description information is empty |
| Edit item, name does not exist | Empty string | Editing fails with error message |

### Design


| ID | Test Scenario | Input | Expected Output |
| --- | --- | --- | --- |
|1 | Create scene | Scene name: "Test scene 1" | The new scene is created successfully, and "Test scene 1" is displayed in the scene list |
|2 | Create Page| Scenario: "Test Scenario 1", Page Name: "Test Page 1" | The new page is created successfully, and "Test Page 1" is displayed in the page list under scenario "Test Scenario 1" |
|3 | Add column chart legend| Scene: "Test scene 1", Page: "Test page 1", Legend name: "Column chart 1" | The legend is created successfully, and "Column chart" is displayed in "Test page 1" 1" |
|4 | Open the data selection sliding window |Scene: "Test Scene 1", Page: "Test Page 1", Legend: "Column Chart 1" | The data selection sliding window opens successfully, showing the data source type, data source and SQL input box |
|5 | Select data source type | Data source type: "Database" | The data source type is selected successfully, and the data source options related to the database are displayed |
|6 | Select data source| Data source: "MySQL database 1"| The data source is selected successfully, you can enter the SQL query statement
|7 | Enter the SQL query statement | SQL: "SELECT category, value FROM sample_data" | The SQL query statement is entered successfully, and bar chart 1 shows the data returned by the SQL query |
|8 | Save Page | Scene: "Test Scene 1", Page: "Test Page 1" | Page saved successfully, including legend and associated data settings|
|9 | Preview Scenario | Scenario: "Test Scenario 1" | The preview is successful, you can preview in the order of the scene and page|
|10| Edit scene name |Original scene name: "Test scene 1", New scene name: "Test scene 1-Modify"| The scene name is modified successfully, and "Test scene 1-Modify" is displayed in the scene list|
|11| Delete scene | Scene name: "Test scene 1-Modify" | The scene is deleted successfully, and "Test scene 1-Modify" is no longer displayed in the scene list|
|12| Edit Page Name| Scenario: "Test Scenario 1", Original Page Name: "Test Page 1", New Page Name: "Test Page 1-Modify"|The page name is modified successfully. "Test Page 1-Modified" is displayed in the page list |
|13| Delete Page| Scenario: "Test Scenario 1", Page Name: "Test Page 1-Modify"| The page is deleted successfully, and "Test Page 1-Modify" is no longer displayed in the page list under the scenario "Test Scenario 1" |
|14| Edit Legend Name| Scene: "Test Scene 1", Page: "Test Page 1", Original Legend Name: "Column Chart 1", New Legend Name: "Column Chart 1-Modify"| Legend Name Modification Success, "Column Chart 1-Modified" is displayed in "Test Page 1"|
|15| Delete Legend| Scene: "Test Scene 1", Page: "Test Page 1", Legend Name: "Column Chart 1-Modify" | The legend is deleted successfully, and "Column Chart" is no longer displayed in "Test Page 1" Figure 1 - Modification"|
|16| Edit SQL query statement| Scenario: "Test Scenario 1", Page: "Test Page 1", Legend: "Column Chart 1", New SQL: "SELECT category, value * 2 AS double_value FROM sample_data"| SQL The query statement is modified successfully, and column chart 1 shows the data returned by the new SQL query|
|17| Undo Legend Editing| Scene: "Test Scene 1", Page: "Test Page 1", Legend: "Column Chart 1" | Undo is successful, and the legend returns to the state before editing|

