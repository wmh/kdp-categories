# KDP Categories Database

Complete Amazon KDP (Kindle Direct Publishing) category hierarchy in two formats: **flat** and **tree**.

## 📊 Dataset Overview

- **450 category files** in flat format
- **5 root categories** with full hierarchical structure in tree format
- Covers major KDP categories including:
  - Arts & Photography
  - Children's Books
  - Crafts, Hobbies & Home
  - Religion & Spirituality
  - Travel

## 📁 Directory Structure

```
kdp-categories/
├── flat/           # Flat JSON files (450 files)
│   ├── 0.json      # Root categories list
│   ├── 1.json      # Arts & Photography
│   ├── 4.json      # Children's Books
│   └── ...
└── tree/           # Hierarchical directory structure (5 root categories)
    ├── Arts_&_Photography/
    ├── Children's_Books/
    ├── Crafts,_Hobbies_&_Home/
    ├── Religion_&_Spirituality/
    └── Travel/
```

## 🗂️ Format Specifications

### Flat Format

Each category is a JSON file named by its ID (e.g., `4.json`):

```json
{
  "id": "4",
  "name": "Children's Books",
  "level": 0,
  "isLeaf": false,
  "path": [],
  "nodes": [
    { "id": "3371", "name": "Activity Books" },
    { "id": "2882", "name": "Animals" }
  ],
  "leafs": [
    { "id": "3400", "name": "Action & Adventure" }
  ]
}
```

**Fields:**
- `id`: Category ID
- `name`: Category name
- `level`: Depth level (0 = root)
- `isLeaf`: Whether this is a leaf category
- `path`: Array of parent category names
- `nodes`: Child categories with children
- `leafs`: Leaf categories (no children)

**Root Categories (`0.json`):**
```json
{
  "id": "0",
  "name": "Root",
  "level": -1,
  "isLeaf": false,
  "path": [],
  "nodes": [
    { "id": "1", "name": "Arts & Photography" },
    { "id": "4", "name": "Children's Books" }
  ],
  "leafs": []
}
```

### Tree Format

Each category is a directory containing:
- `_meta.json`: Category metadata
- `_leafs.json`: Leaf categories (if any)
- Subdirectories for child categories

**Example `_meta.json`:**
```json
{
  "id": "4",
  "name": "Children's Books",
  "level": 0,
  "path": []
}
```

**Example `_leafs.json`:**
```json
[
  { "id": "3400", "name": "Action & Adventure" },
  { "id": "3371", "name": "Activity Books" }
]
```

## 🚀 Usage Examples

### Load Root Categories

```javascript
const rootCategories = require('./flat/0.json');
console.log(rootCategories.nodes); // All root categories
```

### Find Category by ID

```javascript
const category = require('./flat/4.json');
console.log(category.name); // "Children's Books"
console.log(category.nodes); // Child categories
```

### Navigate Tree Structure

```bash
# Browse categories
cd tree/Children\'s_Books/
cat _meta.json              # Category info
cat _leafs.json             # Leaf categories
ls                          # Subcategories
```

## 📦 Data Collection

This dataset was scraped from Amazon KDP using Playwright automation. 

**Source Repository:** [playwright-category-scraper](https://github.com/yourusername/playwright-category-scraper)

## 📅 Last Updated

December 21, 2025

## 📄 License

MIT License - Feel free to use this data for any purpose.

## 🤝 Contributing

Found missing categories or errors? Please open an issue or submit a pull request!

## ⚠️ Disclaimer

This is an unofficial dataset. Amazon KDP categories may change over time. Use at your own discretion.
