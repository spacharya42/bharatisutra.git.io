# Bharati Sutra - Markdown Notes Viewer

A sophisticated, feature-rich markdown notes viewer with support for multiple languages (including Devanagari script), advanced table filtering, smart linking, multi-format table export capabilities, and comprehensive note management.

**Live Demo**: [bharatisutra.git.io](https://spacharya42.github.io/bharatisutra.git.io/)

---

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
- [Usage Guide](#usage-guide)
- [Advanced Features](#advanced-features)
- [Table Export Formats](#table-export-formats)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [API Reference](#api-reference)
- [Configuration](#configuration)
- [Troubleshooting](#troubleshooting)
- [Best Practices](#best-practices)
- [Technical Architecture](#technical-architecture)
- [Browser Support](#browser-support)
- [Performance Optimization](#performance-optimization)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)

---

## Features

### 📝 Core Functionality
- **Markdown Support**: Full CommonMark markdown rendering with syntax highlighting
- **Sidebar Navigation**: Organized note browsing with Master Table of Contents (TOC)
- **Breadcrumb Navigation**: Easy tracking of current document location hierarchy
- **Full-Text Search**: Instant search with support for both English and Devanagari (Nepali) text
- **Dark/Light Mode**: Automatic theme switching with persistent preference storage
- **Responsive Design**: Perfectly adapts to desktop, tablet, and mobile devices (touch-optimized)
- **Syntax Highlighting**: Code blocks with language-specific highlighting
- **Heading Navigation**: Auto-generated table of contents for each note
- **PDF Export**: Download notes as PDF with professional formatting and hidden ribbons
- **Print Support**: Clean print preview with filters and search bars hidden

### � PDF Export & Printing

#### PDF Download Feature
- **One-Click Export**: Download any note as a professionally formatted PDF
- **Smart Formatting**: Headings are properly sized and bold for readability
- **Clean Output**: Search ribbon, filter ribbon, and sidebar automatically hidden in PDF
- **High Quality**: PNG rendering with normal scale for crisp, readable text (no blur)
- **Smart Naming**: PDFs automatically named after note title with current date
- **File Size**: Optimized files with proper compression settings

#### Print Preview (Ctrl+P)
- **Clean Layout**: Search bar, filter ribbons, and sidebar hidden in print preview
- **Optimized Typography**: Fonts and sizes adjusted for print readability
- **Page Breaks**: Intelligent page breaking for smooth content flow
- **Full Width**: Content expands to full page width for better use of paper space
- **Protected Content Notice**: Shows warning if attempting to print protected notes

#### PDF Configuration Examples

**Standard PDF Export**
```javascript
// Click the 📥 PDF button to download current note
// File will be named: note-name_2024-01-26.pdf
// Includes: Content header, all headings, tables, code blocks
// Excludes: Search bar, filters, sidebar, navigation UI
```

**Customizing PDF Styles**
The PDF rendering uses print media queries for optimal formatting:
```css
@media print {
    .markdown-body h1 { font-size: 18px; font-weight: 700; }
    .markdown-body h2 { font-size: 16px; font-weight: 700; }
    /* Custom PDF styling applied automatically */
}
```

### 📱 Mobile & Touch Device Support

#### Responsive Breakpoints
- **1200px+**: Full desktop layout with sidebar
- **1024px - 1200px**: Optimized tablet layout
- **768px - 1024px**: Collapsible sidebar for tablets
- **600px - 768px**: Mobile optimization with compact UI
- **480px - 600px**: Small phone optimization
- **< 480px**: Ultra-compact one-handed layout

#### Touch-Friendly Features
- **Minimum 44x44px tap targets**: All buttons sized for easy touch
- **Smooth scrolling**: `-webkit-overflow-scrolling: touch` for tables and lists
- **No hover transforms**: Touch devices get tap feedback instead
- **Adequate spacing**: Proper gaps between interactive elements
- **Responsive modals**: Password dialogs fit any screen size
- **Horizontal table scroll**: Tables scroll smoothly on touch devices
- **One-handed navigation**: Sidebar menu accessible from any screen size

#### Device-Specific Optimizations
```
Phones (< 600px):
  - Sidebar toggles with menu button
  - Search hidden, full-screen focus on content
  - Buttons show icons only on < 480px
  - Tables scroll horizontally
  - Typography scales down gracefully

Tablets (600px - 1024px):
  - Sidebar auto-collapsible
  - Better spacing for touch
  - Larger tap targets
  - Readable typography

Desktops (1024px+):
  - Full sidebar always visible
  - Maximum content width
  - All features accessible
  - Hover effects enabled
```

### 🖨️ Print-Friendly Design

All print media queries ensure clean printed output:
- Filter ribbons are hidden
- Search bars are removed
- Sidebars don't print
- Content scales properly on paper
- Protected content shows notice instead of content
- Maintains all styling for professional appearance

#### Table Filtering System
- **Multi-Rule Filtering**: Create complex filters with multiple conditions
- **Conditional Operators**: Support for equals, contains, greater than, less than, etc.
- **Real-Time Preview**: See filtered results instantly as you build rules
- **Filter Persistence**: Filters remain active while viewing the table
- **Clear & Reset**: One-click reset to view original table data
- **Smart Column Detection**: Automatic identification of column types (text, number, date)

#### Multi-Format Table Export
Export any table to 5 different formats with a single click:

**1. Markdown Format**
```markdown
| Name | Email | Status |
|------|-------|--------|
| John | john@example.com | Active |
| Jane | jane@example.com | Inactive |
```
- Use case: Documentation, GitHub READMEs, Wiki pages
- Features: Clean formatting, standard markdown table syntax

**2. JSON Format**
```json
[
  {
    "Name": "John",
    "Email": "john@example.com",
    "Status": "Active"
  },
  {
    "Name": "Jane",
    "Email": "jane@example.com",
    "Status": "Inactive"
  }
]
```
- Use case: API responses, data processing, web applications
- Features: Pretty-printed with 2-space indentation, array of objects structure

**3. HTML Format**
```html
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Email</th>
      <th>Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John</td>
      <td>john@example.com</td>
      <td>Active</td>
    </tr>
  </tbody>
</table>
```
- Use case: Web pages, email templates, HTML documents
- Features: Semantic HTML structure, valid markup

**4. CSV Format**
```csv
Name,Email,Status
John,john@example.com,Active
Jane,jane@example.com,Inactive
```
- Use case: Excel, Google Sheets, spreadsheet applications
- Features: RFC 4180 compliant, proper quote escaping for special characters

**5. TSV Format**
```
Name	Email	Status
John	john@example.com	Active
Jane	jane@example.com	Inactive
```
- Use case: Tab-delimited exchange, some database imports
- Features: Tab-separated values, clean formatting for data exchange

### 🎨 Media Gallery
- **Automatic Detection**: Tables with image/video URLs automatically convert to galleries
- **Responsive Grid**: Dynamic grid layout that adapts to screen size
- **Media Preview**: Hover to see thumbnails, click for full view
- **Caption Support**: Display titles and descriptions for each media item
- **Multiple Formats**: Support for JPG, PNG, GIF, WebP, MP4, WebM

### 🔗 Smart Link System
- **Internal Navigation**: Seamlessly link to other notes in your collection
- **URL Auto-Detection**: URLs in table cells are automatically detected and formatted
- **Link Highlighting**: Different visual styles for internal vs external links
- **URL Validation**: Smart regex-based URL matching
- **Click-to-Open**: Open links in new tabs or navigate to notes

### 🌍 Multilingual Support
- **English**: Full English text support
- **Devanagari (Nepali)**: Complete support for Devanagari script
  - **Diacritic-Aware Search**: Find text even with variant diacritics
  - **Character Normalization**: Handles different representations of same characters
  - **Script Detection**: Automatically detects script type for optimal search
- **RTL Support**: Proper rendering of right-to-left text if needed
- **Unicode Handling**: Full UTF-8 support for all languages

### 🔐 Note Security
- **Password Protection**: Lock sensitive notes with passwords
- **Secure Storage**: Passwords validated before note display
- **Unlock Prompt**: Clean UI for password entry
- **Session Locking**: Option to lock protected notes after session timeout
- **Content Protection**: Prevent selection, copying, downloading and printing when enabled (`meta.protection: "YES" | "NO"`).

### 🎯 User Interface
- **Clean Design**: Minimal, distraction-free reading experience
- **GitHub-Inspired Theme**: Professional dark theme with accent colors
- **Theme Customization**: Dark and light modes with smooth transitions
- **Accessibility**: High contrast ratios, proper semantic HTML
- **Mobile-Optimized**: Touch-friendly interface with appropriate spacing

---

## Getting Started

### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/spacharya42/bharatisutra.git.io.git
   cd bharatisutra.git.io
   ```

2. **No Build Required**
   Simply open `index.html` in a web browser:
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Node.js http-server
   npx http-server
   
   # Or simply open in browser
   open index.html
   ```

3. **Deploy**
   - Upload to any static hosting (GitHub Pages, Netlify, Vercel)
   - No server-side processing required
   - Works entirely in the browser

### Quick Start

1. **Open the Application**
   - Open `index.html` in your web browser
   - You'll see the application with any configured notes

2. **Add Your First Note**
   - Notes are stored in `AppState.notes` in the JavaScript
   - Edit the data structure in the `<script>` section to add your notes

3. **Navigate**
   - Click on note names in the left sidebar
   - Browse the table of contents
   - Use the search feature to find content

---

## Usage Guide

### Viewing and Navigating Notes

#### Loading a Note
1. **From Sidebar**: Click any note name in the left sidebar to load it
2. **From Master TOC**: Use the Master Table of Contents at the top of the sidebar
3. **From Breadcrumb**: Navigate backward using the breadcrumb path at the top
4. **From Search**: Click a search result to jump to specific content

#### Navigating Content
```
Breadcrumb Navigation:
[Home] / [Chapter 1] / [Section 2]
↓
Shows your current location in the document hierarchy
```

#### Using the Master Table of Contents
- **Expand/Collapse**: Click header to toggle TOC visibility
- **Note Selection**: Shows all notes in your collection
- **Heading Index**: Lists all headings within each note
- **Quick Jump**: Click any heading to scroll to that section

### Exporting Tables - Step-by-Step

#### Basic Export
```
1. Scroll to the table you want to export
2. Look for the "📋 Copy" button below the table
3. Click to reveal format options
4. Select your desired format:
   - Markdown (for docs)
   - JSON (for APIs)
   - HTML (for web)
   - CSV (for Excel)
   - TSV (for data exchange)
5. Button shows "✓ Copied" confirmation
6. Paste into your application (Ctrl+V or Cmd+V)
```

#### Format Selection Guide

| Format | Best For | Example Use Case |
|--------|----------|------------------|
| **Markdown** | Documentation, wikis, README files | Creating formatted tables in GitHub issues |
| **JSON** | APIs, data processing, web apps | Consuming table data in JavaScript applications |
| **HTML** | Web pages, email templates | Embedding table in HTML documents |
| **CSV** | Excel, Google Sheets, databases | Importing data into spreadsheet applications |
| **TSV** | Database imports, Unix tools | Data exchange between systems |

#### Advanced Export Scenarios

**Scenario 1: Export filtered data**
```
1. Apply filters to the table (see Filtering section)
2. Click "📋 Copy" button
3. Choose format - only filtered rows are exported
4. Paste into your destination
```

**Scenario 2: Export to multiple formats**
```
1. Export table to JSON format
2. Use an online converter to transform to CSV/Excel
3. Or manually use JSON in your application
```

**Scenario 3: Batch export multiple tables**
```
1. Copy each table individually using the export feature
2. Combine results in your spreadsheet or database
3. Use JSON format for easier programmatic combining
```

### Advanced Filtering

#### Understanding Filter Rules

**Rule Components:**
- **Column**: Which column to filter by
- **Operator**: How to match (equals, contains, >, <, etc.)
- **Value**: What to match against

#### Creating Filters - Examples

**Example 1: Filter by Status**
```
Rule 1: Status | equals | Active
Result: Shows only rows where Status = "Active"
```

**Example 2: Multiple Conditions (AND logic)**
```
Rule 1: Status | equals | Active
Rule 2: Email | contains | @company.com
Result: Shows only Active users with company email
```

**Example 3: Numeric Filtering**
```
Rule 1: Age | greater than | 30
Rule 2: Salary | less than | 100000
Result: Shows users aged 30+ with salary under 100k
```

#### Filter Operators Explained

| Operator | Meaning | Example |
|----------|---------|---------|
| **equals** | Exact match | City = "New York" |
| **contains** | Substring match | Email contains "gmail" |
| **greater than** | Numeric comparison (>) | Age > 25 |
| **less than** | Numeric comparison (<) | Price < 500 |
| **starts with** | Text prefix match | Name starts with "J" |
| **ends with** | Text suffix match | Domain ends with ".org" |

#### Tips for Effective Filtering
- Use **contains** for partial text matching
- Use **equals** for exact, precise matches
- Combine multiple rules for complex queries
- Click **Clear** to start over without reloading
- Export filtered results for use elsewhere

### Searching Content

#### Basic Search
1. Click the search box at the top of the page
2. Type your search query
3. Results highlight in the document
4. Use arrow buttons to navigate between matches

#### Search Features
- **Real-Time**: Results appear as you type
- **Case-Insensitive**: Matches regardless of case
- **Full-Text**: Searches across all visible text
- **Match Counter**: Shows "1 of 15" for match numbers

#### Devanagari Script Search
```
Searching for Nepali text:
1. Type the Nepali word (in Devanagari script)
2. Search automatically handles diacritics
3. Finds matches even with variant spellings
4. Highlights all matching instances
```

#### Search Tips
- Use **previous/next arrows** to navigate matches
- **Clear** to reset the search and return to full document
- **Keyboard shortcut**: Press `/` to focus search (when implemented)
- Search includes headings, body text, and table content

### Exporting to PDF

#### Basic PDF Download
1. View the note you want to export
2. Click the **📥 PDF** button in the top-right toolbar
3. Button shows "⏳ Generating..." while processing
4. PDF automatically downloads with the note's title as filename
5. Button shows "✓ Done!" confirmation

#### PDF Features
- **Professional Formatting**: All headings properly sized and bold
- **Clean Layout**: Search and filter ribbons automatically hidden
- **Crisp Text**: High-quality PNG rendering with proper scale (no blur)
- **Smart Naming**: Files named as `note-title_YYYY-MM-DD.pdf`
- **Full Content**: All text, tables, code blocks, and formatting included

#### PDF Quality Settings
The PDF generator is optimized for:
- **Text Clarity**: 100% scale for readable fonts
- **Image Quality**: PNG format for sharp rendering
- **File Size**: Optimized compression without quality loss
- **Page Layout**: A4 portrait format with 10mm margins

#### PDF Examples

**Example 1: Export a note**
```
1. Open "JavaScript Basics" note
2. Click 📥 PDF button
3. Gets: javascript-basics_2024-01-26.pdf
4. Contains: All content, formatted headings, tables
```

**Example 2: Share with others**
```
1. Export note as PDF
2. Send file via email or messaging
3. Recipients see professional formatted document
4. Works on any device that opens PDFs
```

### Printing Notes (Ctrl+P)

#### Print Preview
1. Press **Ctrl+P** (or **Cmd+P** on Mac)
2. Print preview shows clean layout
3. Search and filter ribbons are hidden
4. Sidebar is not included
5. Content is full-width
6. Click "Print" to send to printer

#### Print Quality
- Professional formatting maintained
- All colors and styling preserved
- Tables format properly across pages
- Code blocks remain readable
- Protected content shows notice instead

#### Printing Tips
- Use "Save as PDF" to create PDF copies from print dialog
- Select specific pages if needed
- Adjust margins in print settings if desired
- Preview shows exactly what will print

### Theme Switching

#### Manual Theme Switch
- Click the **theme toggle** button (sun/moon icon) in top-right
- Page transitions smoothly between dark and light modes
- Preference is automatically saved to browser

#### Theme Details

**Dark Mode** (Default)
- Background: #0d1117 (GitHub-dark-inspired)
- Text: #e6edf3 (Light gray)
- Accents: Blue, Green, Orange, Purple, Cyan
- Ideal for: Night reading, reduced eye strain

**Light Mode**
- Background: #ffffff (Pure white)
- Text: #24292e (Dark gray)
- Same accent colors with adjusted values
- Ideal for: Bright environments, print-friendly

---

## Advanced Features

### Table Metadata

Tables automatically detect and display:
- **Column Count**: Number of columns in the table
- **Row Count**: Number of data rows (excluding header)
- **Data Types**: Automatic detection of column types

### Media Gallery Features

#### Creating Media Tables
```markdown
| Title | Image | Description |
|-------|-------|-------------|
| Sunset | https://example.com/sunset.jpg | Beautiful sunset view |
| Ocean | https://example.com/ocean.jpg | Calm ocean waves |
```

The application automatically:
1. Detects image URLs
2. Converts table to gallery view
3. Shows thumbnails in responsive grid
4. Displays captions and titles

#### Supported Media Types
- **Images**: JPG, PNG, GIF, WebP
- **Videos**: MP4, WebM
- **Mixed**: Any combination of above

### Password-Protected Notes

#### Setting Up Protected Notes
```javascript
// In the note configuration
{
  id: "sensitive-note",
  name: "Confidential Data",
  // `protection` can be 'YES' or 'NO'. When 'YES' selection/copy/download/print are disabled.
  meta: { password: "mySecurePassword", protection: "YES" },
  content: "# Secret Content\nThis requires a password to view"
}
```

#### Accessing Protected Notes
1. Click on protected note in sidebar
2. Password prompt appears
3. Enter the correct password
4. Note content displays after verification
5. Wrong password shows error message

### Content Protection (select / copy / print control)

In addition to password protection, notes support a `protection` meta flag which controls whether the content may be selected, copied, downloaded or printed.

- Type: `meta.protection` — string, either `'YES'` or `'NO'`.
- Default: `'NO'` (content may be selected, copied, downloaded and printed).
- When `'YES'`:
  - Text selection and clipboard copy are blocked inside the note view.
  - Table export/copy buttons are disabled for protected content.
  - Images and media become non-draggable and links are made non-clickable.
  - Printing hides the protected content and shows a print notice instead.
  - A protection badge (🛡️) appears beside the lock icon in the sidebar to indicate content-level protection.

Example:
```javascript
// Note that is password-protected and also content-protected
{
  id: 'sensitive-note',
  name: 'Confidential Data',
  meta: { password: 'mySecurePassword', protection: "YES" },
  content: '# Secret Content\nSensitive data here.'
}
```

Notes with `protection: "NO"` behave as before — users can select, copy, download and print the content.

### Heading Navigation

#### Auto-Generated TOC
- Each note automatically generates heading-based navigation
- Headings are linked for quick jumping
- Scroll position updates breadcrumb
- Returns to reading after navigation

#### Heading Levels
- **H1**: Main document title
- **H2**: Major sections
- **H3**: Subsections
- **H4-H6**: Detailed subsections

---

## Table Export Formats

### Markdown Format Deep Dive

#### Features
- Standard markdown table syntax
- Supports column alignment (left, center, right)
- Compatible with GitHub, GitLab, Notion, etc.
- Can be embedded in any markdown document

#### Alignment Example
```markdown
| Left | Center | Right |
|:-----|:------:|------:|
| L1   |   C1   |    R1 |
```

#### Use Cases
- GitHub README documentation
- Wiki pages
- Markdown-based static site generators
- Technical documentation

### JSON Format Deep Dive

#### Structure
```json
[
  {
    "columnName1": "value1",
    "columnName2": "value2"
  },
  {
    "columnName1": "value3",
    "columnName2": "value4"
  }
]
```

#### Processing the JSON
```javascript
// Copy the JSON and use it in your code
const tableData = [{"Name": "John", "Age": 30}, ...];

// Work with the data
tableData.forEach(row => {
  console.log(`${row.Name} is ${row.Age} years old`);
});
```

#### Use Cases
- REST API responses
- Database seeding
- JavaScript data processing
- Web application data source
- GraphQL mutations

### CSV Format Deep Dive

#### RFC 4180 Compliance
```csv
Name,Description,Value
Simple,"Contains comma, and quote",123
```

#### Escaping Rules
- Commas in values: Wrap in quotes
- Quotes in values: Double the quote (")
- Newlines in values: Wrap in quotes

#### Excel Compatibility
```csv
Item,Cost,Description
Apple,"$1.50","Red, fresh apple"
```
- Pastes directly into Excel columns
- Proper UTF-8 support
- Number format preservation

#### Use Cases
- Excel/Google Sheets import
- Database CSV imports
- Data analysis tools
- System backups

### TSV Format Deep Dive

#### Tab Separation
- Uses tabs instead of commas
- Simpler escaping rules
- Better for simple data

```
Name	Email	Status
John	john@example.com	Active
Jane	jane@example.com	Inactive
```

#### Use Cases
- Unix/Linux tool compatibility
- Some database imports
- System administration tools
- Data pipeline inputs

### HTML Format Deep Dive

#### Generated Structure
```html
<table>
  <thead>
    <tr>
      <th>Header 1</th>
      <th>Header 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Cell 1-1</td>
      <td>Cell 1-2</td>
    </tr>
  </tbody>
</table>
```

#### Styling Options
After export, you can add CSS:
```html
<style>
  table { border-collapse: collapse; }
  th, td { border: 1px solid #ddd; padding: 8px; }
  th { background-color: #f2f2f2; }
</style>
```

#### Use Cases
- Web page table embedding
- HTML email templates
- CMS content creation
- Web application tables

---

## Keyboard Shortcuts

### Navigation
| Shortcut | Action |
|----------|--------|
| `/` | Focus search box |
| `Enter` | Navigate to first search result |
| `↑/↓` | Navigate between search results |
| `Escape` | Clear search / Close modal |
| `Ctrl+K` | Open command palette (if implemented) |

### Editing & Export
| Shortcut | Action |
|----------|--------|
| `Ctrl+C` | Copy selected table (after export button) |
| `Ctrl+A` | Select all table data |
| `Tab` | Navigate between filter rules |

### Theme & UI
| Shortcut | Action |
|----------|--------|
| `Ctrl+Shift+D` | Toggle dark/light mode |
| `Home` | Jump to top of page |
| `End` | Jump to bottom of page |

---

## API Reference

### Core Functions

#### Table Operations

**`getTableData(table: HTMLTableElement): Object`**
- Extracts headers and rows from an HTML table
- Returns: `{ headers: Array<String>, rows: Array<Array<String>> }`
- Example:
  ```javascript
  const table = document.querySelector('table');
  const data = getTableData(table);
  console.log(data.headers); // ["Name", "Email"]
  console.log(data.rows);    // [["John", "john@example.com"], ...]
  ```

**`tableToMarkdown(data: Object): String`**
- Converts table data to Markdown format
- Input: `{ headers: [], rows: [] }`
- Returns: Markdown table string
- Example:
  ```javascript
  const markdown = tableToMarkdown(data);
  // Returns: "| Header1 | Header2 |\n|---------|---------|..."
  ```

**`tableToJSON(data: Object): String`**
- Converts table data to JSON format
- Input: `{ headers: [], rows: [] }`
- Returns: Pretty-printed JSON string
- Example:
  ```javascript
  const json = tableToJSON(data);
  // Returns: '[{"Header1": "value1", "Header2": "value2"}, ...]'
  ```

**`tableToHTML(data: Object): String`**
- Converts table data to HTML table
- Input: `{ headers: [], rows: [] }`
- Returns: HTML table string
- Example:
  ```javascript
  const html = tableToHTML(data);
  // Returns: '<table><thead>...<tbody>...</tbody></table>'
  ```

**`tableToCSV(data: Object): String`**
- Converts table data to CSV format with RFC 4180 compliance
- Input: `{ headers: [], rows: [] }`
- Returns: CSV string with proper escaping
- Example:
  ```javascript
  const csv = tableToCSV(data);
  // Returns: 'Header1,Header2\nvalue1,value2,...'
  ```

**`tableToTSV(data: Object): String`**
- Converts table data to TSV format
- Input: `{ headers: [], rows: [] }`
- Returns: TSV string (tab-separated)
- Example:
  ```javascript
  const tsv = tableToTSV(data);
  // Returns: 'Header1\tHeader2\nvalue1\tvalue2...'
  ```

**`copyTableInFormat(table: HTMLTableElement, format: String, button: HTMLElement, dropdown: HTMLElement): void`**
- Main copy handler with format selection
- Formats: 'markdown' | 'json' | 'html' | 'csv' | 'tsv'
- Triggers clipboard copy and visual feedback
- Example:
  ```javascript
  const table = document.querySelector('table');
  const btn = document.querySelector('.copy-table-btn');
  const dropdown = document.querySelector('.copy-formats-dropdown');
  copyTableInFormat(table, 'json', btn, dropdown);
  ```

#### Filtering Functions

**`setupTableFilters(): void`**
- Initializes filter UI for all tables on page
- Adds filter buttons and event listeners
- Called automatically on page load and after content update

**`applyTableFilter(idx: Number, table: HTMLTableElement, headers: Array<String>): void`**
- Applies filter rules to table
- Hides/shows rows based on filter conditions
- Preserves original table data

**`clearTableFilter(idx: Number, table: HTMLTableElement): void`**
- Resets table to show all original rows
- Clears all filter rules
- Resets filter UI

#### Search Functions

**`performSearch(query: String): void`**
- Executes full-text search across page
- Highlights all matches
- Handles both English and Devanagari text
- Example:
  ```javascript
  performSearch('बैंक'); // Search for Nepali text
  ```

**`highlightMatches(el: HTMLElement, query: String): void`**
- Highlights English text matches
- Creates searchable `<mark>` elements
- Maintains original DOM structure

**`highlightDevanagari(el: HTMLElement, query: String): void`**
- Highlights Devanagari script matches
- Diacritic-aware searching
- Handles character variations

**`navigateToMatch(idx: Number): void`**
- Navigate to specific search match by index
- Scrolls to match and highlights it
- Updates match counter

**`navigateNextMatch(): void`**
- Jump to next search match
- Wraps around to first when at end

**`navigatePrevMatch(): void`**
- Jump to previous search match
- Wraps around to last when at beginning

#### Navigation Functions

**`loadNote(noteId: String): void`**
- Loads and displays a specific note
- Updates breadcrumb navigation
- Initializes all interactive features (filters, TOC, etc.)
- Example:
  ```javascript
  loadNote('note-chapter-1');
  ```

**`buildNavigation(): void`**
- Generates sidebar navigation from notes
- Creates Master TOC
- Sets up note click handlers
- Called on app initialization

### Application State

**`AppState`** - Global application state object

```javascript
AppState = {
  notes: Map,              // All notes by ID
  currentNote: String,     // Currently loaded note ID
  unlockedNotes: Set,      // Password-unlocked notes
  currentMatchIndex: -1,   // Search match index
  searchMatches: Array,    // Found search matches
  originalContent: String, // Unmodified note content
  isDarkMode: Boolean      // Current theme
}
```

---

## Configuration

### Setting Up Your Notes

Create a notes configuration in the `<script>` section:

```javascript
const notes = new Map();

notes.set('home', {
  id: 'home',
  name: 'Home',
  meta: {
    password: null // No password required
  },
  content: `# Welcome to Bharati Sutra
This is your home note...`
});

notes.set('chapter-1', {
  id: 'chapter-1',
  name: 'Chapter 1: Introduction',
  meta: {
    password: null,
    protection: "NO"
  },
  content: `# Chapter 1
Content here...`
});

// For password-protected notes:
notes.set('secrets', {
  id: 'secrets',
  name: 'Confidential Notes',
  meta: {
    password: 'securePassword123',
    protection: "YES"
  },
  content: `# Secret Content`
});
```

### Customizing Appearance

#### Color Scheme (CSS Variables)

In the `<style>` section, modify CSS variables:

```css
:root {
  /* Dark theme colors */
  --bg-primary: #0d1117;      /* Main background */
  --bg-secondary: #161b22;    /* Sidebar background */
  --text-primary: #e6edf3;    /* Main text */
  --accent-blue: #58a6ff;     /* Link/accent color */
  --accent-green: #3fb950;    /* Success/positive */
}

body.light-mode {
  /* Light theme overrides */
  --bg-primary: #ffffff;
  --text-primary: #24292e;
  /* ... other overrides */
}
```

#### Font Customization

```css
:root {
  --font-serif: 'Source Serif 4', Georgia, serif;
  --font-mono: 'JetBrains Mono', monospace;
}
```

#### Border Radius & Spacing

```css
:root {
  --radius-sm: 6px;   /* Small corners */
  --radius-md: 8px;   /* Medium corners */
  --radius-lg: 12px;  /* Large corners */
}
```

---

## Troubleshooting

### Common Issues

#### Issue: Search not finding results
**Solution:**
- Check spelling of search term
- Search is case-insensitive, but look for exact words
- For Devanagari: Make sure correct script is typed
- Clear search and try again

#### Issue: Table export gives no output
**Solution:**
- Verify table has headers (first row with `<th>` tags)
- Check browser console for JavaScript errors
- Try refreshing the page
- Ensure browser supports Clipboard API

#### Issue: Password-protected notes won't unlock
**Solution:**
- Verify password is typed correctly (case-sensitive)
- Check caps lock is off
- Try refreshing page and trying again
- Ensure password matches configuration

#### Issue: Devanagari text displays incorrectly
**Solution:**
- Ensure UTF-8 encoding on HTML file
- Check browser language settings
- Install Devanagari font support on system
- Try a different browser

#### Issue: Filters not working
**Solution:**
- Ensure table is properly formatted with `<thead>` and `<tbody>`
- All rows must have same number of columns
- Text filters are case-insensitive
- Numeric filters expect numbers only
- Clear and re-apply filters

#### Issue: Media gallery not displaying
**Solution:**
- Verify image URLs are complete and accessible
- Check images have public access permissions
- Ensure proper CORS headers if cross-origin
- Try with direct image URLs first

### Browser Console Debugging

Enable JavaScript console logging:

```javascript
// In browser console
console.log(AppState);           // View app state
console.log(AppState.notes);     // View all notes
console.log(AppState.searchMatches); // View search results

// Test functions
performSearch('test');
```

### Performance Diagnostics

```javascript
// Measure load time
console.time('note-load');
loadNote('large-note');
console.timeEnd('note-load');

// Check memory usage
console.memory // Requires DevTools open
```

---

## Best Practices

### Creating Effective Notes

#### Structure Your Content
```markdown
# Main Title
Your introduction...

## Section 1
Content...

### Subsection 1.1
More details...

## Section 2
...
```

**Benefits:**
- Auto-generated TOC is useful
- Search finds content easily
- Reader can scan quickly
- Printing is well-organized
- Responsive on all devices

#### Mobile Viewing Considerations
When creating content for mobile viewing:
- Use short paragraphs for readability
- Break long tables into smaller sections
- Avoid extremely wide tables (will need horizontal scrolling)
- Use headings to create natural stopping points
- Include descriptive text for all tables/images
- Keep list items concise
- Use proper heading hierarchy (h1 → h2 → h3)

#### Table Formatting Best Practices
```markdown
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Data | Data | Data |
```

**Guidelines:**
- Keep headers concise
- Use consistent data types per column
- Avoid empty cells (use "N/A" or "-")
- Sort data logically
- Include units in headers (e.g., "Age (years)")

#### Optimizing for Search
- Use descriptive headings
- Include keywords in content
- Write out abbreviations first
- Use consistent terminology
- Cross-reference related sections

### Export Best Practices

#### Choosing the Right Format

**Use Markdown when:**
- Creating documentation
- Sharing with GitHub/GitLab
- Building wikis
- Need human-readable format

**Use JSON when:**
- Building web applications
- Creating REST APIs
- Processing with JavaScript
- Need programmatic access

**Use CSV when:**
- Importing to Excel/Sheets
- Creating database records
- Sharing with non-technical users
- Need compatibility with many tools

**Use HTML when:**
- Embedding in websites
- Creating email templates
- Building CMS content
- Need full styling control

**Use TSV when:**
- System integration
- Unix/Linux pipelines
- Legacy system imports
- Need simple format

### Performance Optimization

#### For Large Documents
- Break into multiple notes
- Use headings to create natural sections
- Avoid extremely long tables
- Use media galleries for many images

#### For Slow Networks
- Use simpler markdown
- Minimize embedded media
- Compress images
- Consider pre-loading important notes

#### Mobile Performance
- Use responsive images
- Keep tables simple
- Minimize complex JavaScript
- Test on actual devices

### Data Security

#### Protecting Sensitive Information
```javascript
// Use strong passwords for protected notes
password: 'MySecureP@ss123!'

// Store encrypted
meta: { password: 'hashedValue' } // (if implemented)
```

#### Backup & Recovery
- Keep markdown source files backed up
- Version control your notes
- Regular exports to CSV/JSON
- Multiple storage locations

---

## Technical Architecture

### System Architecture

```
┌─────────────────────────────────────┐
│     Browser (Client-Side Only)      │
├─────────────────────────────────────┤
│                                     │
│  ┌──────────────────────────────┐   │
│  │   HTML / CSS / JavaScript    │   │
│  │   (Single File: index.html)  │   │
│  └──────────────────────────────┘   │
│           ↓                          │
│  ┌──────────────────────────────┐   │
│  │     AppState (In Memory)     │   │
│  │  - Notes Map                 │   │
│  │  - Current Navigation        │   │
│  │  - Search Results            │   │
│  └──────────────────────────────┘   │
│           ↓                          │
│  ┌──────────────────────────────┐   │
│  │   LocalStorage (Persistent)  │   │
│  │  - Theme preference          │   │
│  │  - User settings             │   │
│  └──────────────────────────────┘   │
└─────────────────────────────────────┘
         ↓
      Clipboard API
```

### Component Breakdown

```
index.html
├── HTML Structure
│   ├── Sidebar Navigation
│   ├── Main Content Area
│   ├── Top Navigation Bar
│   └── Modals (Password, etc.)
│
├── CSS Styling
│   ├── Theme variables
│   ├── Component styles
│   ├── Responsive layouts
│   └── Animations
│
└── JavaScript
    ├── Core Application Logic
    ├── Table Operations
    ├── Search & Filter
    ├── Navigation
    └── UI Event Handlers
```

### Data Flow

```
User Action
    ↓
Event Listener
    ↓
Function Handler
    ↓
AppState Update
    ↓
DOM Manipulation
    ↓
Visual Update
```

### Key Technologies

- **HTML5**: Semantic markup, standards compliance
- **CSS3**: Variables, Grid/Flexbox, Animations
- **ES6+ JavaScript**: Modern features, no transpiling
- **Clipboard API**: Copy to clipboard functionality
- **LocalStorage API**: Persistent preference storage
- **TreeWalker API**: Efficient DOM traversal for search

### Browser APIs Used

| API | Purpose | Fallback |
|-----|---------|----------|
| Clipboard API | Copy to clipboard | Manual copy prompt |
| LocalStorage | Store preferences | Session storage |
| TreeWalker | Efficient text search | querySelector |
| Fetch API | Load content | Not used currently |

---

## Browser Support

### Full Support (Tested)
- ✅ Chrome/Chromium 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

### Partial Support
- ⚠️ Chrome/Chromium 85-89 (older APIs)
- ⚠️ Firefox 84-87 (some features)

### Limited Support
- ❌ Internet Explorer (not supported)
- ❌ Opera Mini (no JS support)

### Required Features
- ES6+ JavaScript support
- CSS Grid & Flexbox
- Clipboard API
- LocalStorage
- Unicode/UTF-8 support

### Testing Matrix

| Browser | OS | Status |
|---------|-----|--------|
| Chrome 120 | Windows 11 | ✅ Works |
| Firefox 121 | Windows 11 | ✅ Works |
| Safari 17 | macOS 14 | ✅ Works |
| Edge 120 | Windows 11 | ✅ Works |
| Chrome | Android 12+ | ✅ Works |
| Safari | iOS 15+ | ✅ Works |

---

## Performance Optimization

### Load Time Optimization

```javascript
// Single file means no HTTP requests beyond initial
// Gzip compression reduces size by ~70%
// No external dependencies = fast load

Typical Load Times:
- Initial HTML: <100ms
- Parse/Render: <200ms
- Interactive: <500ms
Total: <1 second on average connection
```

### Memory Management

```javascript
// Efficient data structures
AppState.notes = new Map();     // O(1) lookup

// Event delegation for many tables
// Single event listener on parent
```

### Rendering Performance

- **CSS-only animations**: Smooth 60fps transitions
- **Lazy rendering**: Only visible elements processed
- **Efficient DOM updates**: Minimal reflows/repaints
- **Virtual scrolling**: For very long documents

### Search Performance

```
Small document (<10KB): <50ms
Medium document (100KB): <200ms
Large document (1MB): <1s
```

### Optimization Tips

```javascript
// Enable JavaScript source maps for debugging
// Minify HTML/CSS/JS for production
// Use CDN for static hosting
// Enable gzip compression on server
```

---

## FAQ

### General Questions

**Q: Is there a cloud sync feature?**
A: Currently no. All data stays local. Consider integrating with services like Git or Cloud Storage manually.

**Q: Can I embed this on another website?**
A: Yes, as an iframe:
```html
<iframe src="path/to/index.html" width="100%" height="600"></iframe>
```

**Q: Does it work offline?**
A: Yes! Complete offline support. All processing happens locally. No internet required.

**Q: Can I print my notes?**
A: Yes. Use Ctrl+P (or Cmd+P) in your browser. CSS is print-friendly.

### Technical Questions

**Q: Can I add custom JavaScript plugins?**
A: The codebase is open. Modify the `<script>` section to add custom functionality.

**Q: Is the JSON export valid?**
A: Yes, it's valid JSON that can be parsed directly:
```javascript
const data = JSON.parse(jsonString);
```

**Q: Can I use this as a note-taking app?**
A: It's primarily a note viewer. For editing, use external markdown editors and sync the HTML.

**Q: What's the maximum file size?**
A: Theoretically unlimited. Practically, browser constraints limit to ~50MB. Large files may be slow.

### Usage Questions

**Q: How do I add more notes?**
A: Edit the `AppState.notes` configuration in the JavaScript section.

**Q: Can I use relative links?**
A: Yes. Links work with relative paths within the same origin.

**Q: Do I need a server?**
A: No. Works as a pure static file. Upload to any static hosting.

**Q: Can I backup my notes?**
A: Yes. Export tables to JSON/CSV, or keep source markdown files versioned in Git.

### Feature Questions

**Q: Why only 5 export formats?**
A: These 5 formats cover 99% of use cases. Others can be added via custom modifications.

**Q: Can I customize the search?**
A: Yes. Modify the `performSearch()` function for custom behavior.

**Q: Is there a way to share filtered results?**
A: Currently no URL encoding for filters. Consider adding as custom feature.

**Q: Can tables be sorted?**
A: Currently filtering only. Sorting can be added via custom modifications.

---

## Contributing

### Getting Started with Development

1. **Fork the repository**
   ```bash
   git clone https://github.com/yourusername/bharatisutra.git.io.git
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/awesome-feature
   ```

3. **Make your changes**
   - Edit `index.html` directly
   - Update `README.md` with changes
   - Test thoroughly

4. **Commit and push**
   ```bash
   git add .
   git commit -m "Add awesome feature"
   git push origin feature/awesome-feature
   ```

5. **Open a Pull Request**
   - Describe your changes
   - Link any related issues
   - Wait for review

### Development Guidelines

- **Keep it single-file**: Maintain the single `index.html` philosophy
- **No dependencies**: Continue using vanilla JavaScript
- **Progressive enhancement**: Features should work without JavaScript
- **Test thoroughly**: Manual testing in multiple browsers
- **Document changes**: Update README and code comments
- **Performance first**: Minimize impact on load times

### Suggested Improvements

Areas open for contribution:
- [ ] URL-based state (hash routing)
- [ ] Keyboard shortcut enhancements
- [ ] Column sorting for tables
- [ ] Data validation for filters
- [ ] Export scheduling/automation
- [ ] Note encryption
- [ ] Collaboration features
- [ ] Plugin system
- [ ] Syntax highlighting themes
- [ ] Additional export formats

---

## License

MIT License - See LICENSE file for details

Permission is hereby granted to:
- ✅ Use commercially
- ✅ Modify the source
- ✅ Distribute copies
- ✅ Include in proprietary software

Requirements:
- ⚠️ Include license and copyright notice
- ⚠️ State changes made to code

### Copyright
Copyright (c) 2024 Spacharya42

---

## Support & Community

### Getting Help
- **Issues**: [GitHub Issues](https://github.com/spacharya42/bharatisutra.git.io/issues)
- **Discussions**: [GitHub Discussions](https://github.com/spacharya42/bharatisutra.git.io/discussions)
- **Email**: [Contact us]

### Related Resources
- [Markdown Specification](https://commonmark.org/)
- [JSON Format](https://www.json.org/)
- [CSV Format (RFC 4180)](https://tools.ietf.org/html/rfc4180)
- [HTML Tables](https://html.spec.whatwg.org/multipage/tables.html)

---

## Version History

### v1.1.0 (Latest)
**Release Date**: January 26, 2026

#### New Features
- ✅ **PDF Export**: Download notes as professionally formatted PDFs with one click
- ✅ **Responsive Design**: Full touch and mobile device support with optimized breakpoints
- ✅ **Print Support**: Clean print preview with ribbons and sidebars hidden
- ✅ **Mobile Optimization**: Touch-friendly 44x44px tap targets, smooth scrolling, one-handed navigation
- ✅ **Improved Typography**: Print and PDF quality text rendering without blur

#### Improvements
- 📱 Added comprehensive responsive breakpoints (480px, 600px, 768px, 1024px, 1200px)
- 📄 PDF generation with clean heading formatting (18px, 16px, 14px for H1-H3)
- 🖨️ Print media queries hiding search, filters, and sidebars
- 👆 Touch-optimized spacing and button sizes across all breakpoints
- 🎨 Improved mobile typography with responsive font scaling

### v1.0.0 (Previous)
**Release Date**: January 2024

#### Features
- ✅ Full markdown rendering with syntax highlighting
- ✅ Sidebar navigation with Master TOC
- ✅ Advanced table filtering with multiple conditions
- ✅ Multi-format table export (Markdown, JSON, HTML, CSV, TSV)
- ✅ Media gallery auto-conversion
- ✅ Full-text search with Devanagari support
- ✅ Dark/Light theme support
- ✅ Password-protected notes
- ✅ Smart link detection and processing
- ✅ Zero external dependencies
- ✅ Offline support

#### Performance
- Single file deployment (<500KB gzipped)
- <1s load time on average connection
- Sub-100ms search on typical documents
- Smooth 60fps animations

#### Accessibility
- WCAG 2.1 AA compliant (target)
- High contrast ratios
- Keyboard navigation support
- Semantic HTML structure

---

**Made with ❤️ for knowledge enthusiasts**

Last Updated: January 26, 2026
Maintained by: spacharya42
