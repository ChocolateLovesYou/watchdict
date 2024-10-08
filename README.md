 # WatchDict



 **WatchDict** is a Python library that provides an enhanced data structure for monitoring dynamic changes in collections, allowing for efficient querying using trie-based search functionality. The `WatchDict` class enables logging of modifications and supports advanced search capabilities, while also saving all changes in a JSON file that acts as a database.



 ## Features

 - **WatchDict**: Automatically logs and saves changes when items are added, removed, or modified.

 - **Trie-Based Search**: Fast searching for prefixes, suffixes, and exact matches using a trie data structure.

 - **Flexible Querying**: Supports exact matches, substring searches, and numerical comparisons (greater than, less than).

 - **Persistent Storage**: Saves all changes in a JSON file, allowing data to persist between sessions.

 - **Debug Logging**: Easily toggle logging of changes to standard output.



 ## Installation

 You can install the WatchDict package using pip:



 ```bash
 pip install watchdict 
 ```



 ## Usage



 ### Importing the Library

 To use `WatchDict`, import it into your Python script:



 ```python

 from watchdict import WatchDict

 ```



 ### Creating a WatchDict

 You can create a `WatchDict` to monitor and manipulate a dictionary of items. Here’s how to do it:



 ```python

 # Initialize a WatchDict with a file path for persistence

 watchdict = WatchDict(database='data.json', allow_search=True)



 # Set items

 watchdict['key1'] = 'value1'  # Output: Set item: key1 = value1

 watchdict['key2'] = 'value2'  # Output: Set item: key2 = value2



 # Get an item

 value = watchdict['key1']  # Output: 'value1'



 # Delete an item

 del watchdict['key2']  # Output: Deleted item: key2 which had value value2



 # Search for values

 results = watchdict['$value1$']  # Exact match query

 print(results)  # Output: [{'key1': 'value1'}]



 # Greater than query

 greater_than_results = watchdict['>100']

 print(greater_than_results)  # Output: results of greater than 100

 between_results = watchdict['>100&<200']

 or_opration = watchdict['$hello|*bye']

 ```



 ### Persistent Storage

 All changes made to the `WatchDict` are saved in a specified JSON file. When the `WatchDict` is initialized, it loads existing data from the file, allowing for persistence between sessions. 



 ### Logging

 To enable logging of changes, set the `debug` flag to `True` at the beginning of your script:



 ```python

 debug = True  # Enable logging

 ```



 To disable logging, set `debug` to `False`:



 ```python

 debug = False  # Disable logging

 ```



 ## Example Usage

 Here's a complete example showcasing the features of WatchDict:



 ```python

 from watchdict import WatchDict



 # Enable debug logging

 debug = True



 # Create and manipulate a WatchDict

 watchdict = WatchDict(database='data.json', allow_search=True)

 watchdict['key1'] = 'value1'

 watchdict['key2'] = 'value2'



 # Get an item

 print(watchdict['key1'])  # Output: 'value1'



 # Delete an item

 del watchdict['key2']



 # Search for an exact value

 print(watchdict['$value1$'])  # Output: [{'key1': 'value1'}]



 # Perform a greater than query

 # Assume numerical values are stored in the WatchDict

 print(watchdict['>100'])  # Output: results for values greater than 100

 ```



 ## Query Syntax

 You can perform various types of queries on the `WatchDict`. Here are the supported query formats:



 - **Exact match**: Enclose the word in `$` symbols (e.g., `$word$`)

 - **Greater than**: Start the query with `>` (e.g., `>10`)

 - **Less than**: Start the query with `<` (e.g., `<5`)



 ## License

 This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



 ## Acknowledgments

 - This project utilizes a trie data structure for efficient searching. The implementation is based on common patterns for prefix trees.

