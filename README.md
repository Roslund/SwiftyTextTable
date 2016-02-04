# SwiftyTextTable

A lightweight Swift library for generating text tables.

## Usage

```swift
// First create some columns
let foo = TextTableColumn(header: "foo")
let bar = TextTableColumn(header: "bar")
let baz = TextTableColumn(header: "baz")

// Then create a table with the columns
var table = TextTable(columns: [foo, bar, baz])

// Then add some rows
table.addRow(1, 2, 3)
table.addRow(11, 22, 33)

// Then render the table and use
let tableString = table.render()
print(tableString)

/*
+-----+-----+-----+
| foo | bar | baz |
+-----+-----+-----+
| 1   | 2   | 3   |
| 11  | 22  | 33  |
+-----+-----+-----+
*/
```

Any `CustomStringConvertible` can be used for row `values`.

### Row Padding/Truncation

When adding rows, `TextTable` will automatically pad the rows with empty strings
when there are fewer `values` than columns. `TextTable` will also disregard all
`values` over the column count.

```swift
let foo = TextTableColumn(header: "foo")
let bar = TextTableColumn(header: "bar")
let baz = TextTableColumn(header: "baz")

var table = TextTable(columns: [foo, bar, baz])

table.addRow(1, 2)
table.addRow(11, 22, 33)
table.addRow(111, 222, 333, 444)

let tableString = table.render()
print(tableString)

/*
+-----+-----+-----+
| foo | bar | baz |
+-----+-----+-----+
| 1   | 2   |     |
| 11  | 22  | 33  |
| 111 | 222 | 333 |
+-----+-----+-----+
*/
```
