# Multimedia App Bounty

Based on **Multimedia Application** of the Web Development with React campaign which is released on the same day.

I 've buit two features:

   - **File Search**
   - **File sorting**

Both of those feature is really important for File Manager, like on **Search Feature** will really useful if user has a lot of data to shown on the file list and need to search some specific file faster. And on the other hand the **File Sorting** feature will help user to sorting the file in order Ascending or Descending.

---

### Overview of the Two Feature Added.

1. **File Search Feature**:
   - The File Search feature allows users to search for specific files within the application.
   - A search input field is provided where users can enter their search query.
   - As the user types in the search input field, the application dynamically filters the displayed file list based on the search query.
   - The search functionality typically matches the search query against file names or other relevant attributes to find matching files.
   - The filtered file list is updated in real-time as the user types or modifies the search query.
   - This feature helps users quickly locate specific files within a large collection, improving usability and productivity.
2. **File Sorting Feature:**
   - The File Sorting feature enables users to change the order in which files are displayed in the application.
   - A sort order toggle menu is provided to select the desired sorting criteria.
   - When the user selects a sorting option, the file list is rearranged accordingly to reflect the chosen sorting order.
   - The sort order may be ascending (e.g., A-Z, oldest to newest) or descending (e.g., Z-A, newest to oldest).
   - The sorting functionality helps users organize files based on their preferences and find files more easily based on different criteria.

These features enhance the file management capabilities of an application, allowing users to quickly locate specific files through search and customize the order of file display through sorting. They provide better control and flexibility in managing and accessing files.

### Code Overview.

This code demonstrates the implementation of search and sorting functionality for a list of files that added to **App.js,** Here's an overview:

1. **State Variables:**

```javascript
const [searchQuery, setSearchQuery] = useState("")
const [sortOrder, setSortOrder] = useState("asc")
```

   - `searchQuery` represents the current search query entered by the user.
   - `sortOrder` stores the current sorting order (ascending or descending) of the files.
2. **Filtered Files:**

```javascript
// Filter the files based on the search query and sort order
  const filteredFiles = useMemo(() => {
    // Sort the files based on the file name and sortOrder state
    const sortedFiles = [...myFiles].sort((a, b) => {
      if (sortOrder === "asc") {
        return a.name.localeCompare(b.name);
      } else {
        return b.name.localeCompare(a.name);
      }
    });

    return sortedFiles.filter(
      (file) =>
        file.name.toLowerCase().includes(searchQuery.toLowerCase()) ||
        file.type.toLowerCase().includes(searchQuery.toLowerCase())
    );
  }, [myFiles, searchQuery, sortOrder]);
```

   - The `filteredFiles` variable is a memoized value that is updated whenever `myFiles`, `searchQuery`, or `sortOrder` changes.
   - It filters the `myFiles` array based on the search query and sorts the filtered files according to the specified `sortOrder`.
   - The `sortedFiles` array is created by cloning the `myFiles` array and sorting it using the `Array.sort()` method and a comparison function based on the `sortOrder`.
   - The comparison function compares the `name` property of each file using `localeCompare()` to determine the correct sorting order.
3. **Toggle Sort Order:**

```javascript
// Function to toggle the sort order between ascending and descending
  const toggleSortOrder = () => {
    const newSortOrder = sortOrder === "asc" ? "desc" : "asc";
    setSortOrder(newSortOrder);
  };
```

   - The `toggleSortOrder` function is called when the user clicks the "Sort" button.
   - It updates the `sortOrder` state by toggling between "asc" (ascending) and "desc" (descending).
4. **Search Input**:

```javascript
{/* Search input */}
            <div style={styles.searchContainer}>
              <input
                type="text"
                placeholder="Search files here..."
                value={searchQuery}
                onChange={(e) => setSearchQuery(e.target.value)}
                style={styles.searchInput}
              />
            </div>
```

   - The code includes a search input field represented by an HTML `input` element.
   - It is connected to the `searchQuery` state, and its value is set to `searchQuery` to reflect the current search query entered by the user.
   - The `onChange` event handler updates the `searchQuery` state whenever the user types or modifies the search input.
5. **Sort Order Button**:

```javascript
{/* Sort order button */}
            <button style={styles.controlButton} onClick={toggleSortOrder}>
              Sort: {sortOrder === "asc" ? "Asc" : "Desc"}
            </button>
```

   - The code includes a button labeled "Sort" that displays the current sorting order (`asc` or `desc`).
   - Clicking the button triggers the `toggleSortOrder` function, which toggles the `sortOrder` state between ascending and descending.

Overall, this code enables users to search for files based on a search query and sort the displayed files in ascending or descending order. The search functionality updates the filtered files in real-time, and the sorting order can be toggled between ascending and descending by clicking the "Sort" button.

?descriptionFromFileType=function+toLocaleUpperCase()+{+[native+code]+}+File&mimeType=application/octet-stream&fileName=Multimedia+App+Bounty.md&fileType=undefined&fileExtension=md