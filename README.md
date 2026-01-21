# SubCatOnly

**SubCatOnly** is a lightweight, browser-based tool designed to help Wikimedia Commons contributors avoid "over-categorization." It analyzes a list of input categories and automatically removes any category that is a parent (or ancestor) of another category in the list.

According to [Commons:Categories#Over-categorization](https://commons.wikimedia.org/wiki/Commons:Categories#Over-categorization), files should generally be placed in the most specific category available. This tool automates the process of checking the category tree to ensure specificity.

[**Tool Link**](https://kuldeepburjbhalaike.github.io/SubCatOnly/)

## Features

* **Deep Ancestor Scan:** Checks up to **6 levels** up the category tree to find hidden redundancy (e.g., *Grandparent -> Parent -> Child*).
* **Format Preservation:** Respects your input format. If you input `[[Category:Name]]`, the output will use that format. If you input `Name`, the output stays as plain text.
* **Client-Side Only:** Runs entirely in your browser using JavaScript. No backend server is required.
* **CORS Support:** Connects directly to the MediaWiki API using `origin=*`.
* **Theme Support:** Automatically detects Dark/Light mode based on your system settings and includes a manual toggle.
* **Analysis Log:** Provides a clear log explaining exactly *why* a category was removed (e.g., "Removing **France** because it is an ancestor of **Paris**").

## How to Use

### Option 1: Run Locally
1.  Download the `index.html` file from this repository.
2.  Open the file in any modern web browser (Chrome, Firefox, Edge, Safari).
3.  Paste your list of categories into the text box.
4.  Click **Prune Categories**.

### Option 2: Host on GitHub Pages (Recommended)
1.  Fork this repository.
2.  Go to **Settings** > **Pages** in your GitHub repository menu.
3.  Select the `main` branch as the source and save.
4.  Your tool will be live at `https://<your-username>.github.io/SubCatOnly/`.

## Example

**Input:**
```text
Culture of Punjab, India
[[Category:Culture of India]]
Mansa district, Punjab
Burj Bhalaike
```

**Output:**
```text
Culture of Punjab, India
Burj Bhalaike
```

**Logic Applied:**
* `Culture of India` is removed because it is a parent of `Culture of Punjab, India`.
* `Mansa district, Punjab` is removed because it is a grandparent of `Burj Bhalaike` (via the category *Villages in Mansa district, Punjab*).

## Technical Details

* **Stack:** HTML5, CSS3, Vanilla JavaScript (ES6+).
* **API:** [MediaWiki Action API](https://www.mediawiki.org/wiki/API:Main_page).
* **Method:** Breadth-First Search (BFS) algorithm to traverse the category tree.
* **Caching:** Implements local caching during the session to minimize API requests and improve speed.

## Contributing

Feel free to open issues or submit pull requests if you find bugs or have feature ideas!

## License

This project is open source and available under the [MIT License](LICENSE).

---
Made with ❤️ by [Kuldeep](https://meta.wikimedia.org/wiki/User:Kuldeepburjbhalaike)
