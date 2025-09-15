# NDF: The Nerva Data Format

NDF is a simple, human-readable data format based on a single, powerful data structure: the table.

NDF is used by the Nerva language to define tables (<https://github.com/aiafrasinei/nerva-lang>).

## Syntax

NDF files use a comma-separated syntax to define tables. A table is a collection of named and typed columns.

The basic structure is as follows:

```
name column1_type column2_type ...
```

Data is then inserted into the table using a similar comma-separated format:

```
name = , value1 value2 ... ,
```

## Data Types

NDF supports a set of primitive data types, which are specified as suffixes to column names.

| Suffix | Type      | Description                  |
|--------|-----------|------------------------------|
| `_i`   | Integer   | Whole numbers (e.g., 10, -5) |
| `_b`   | Boolean   | `true` or `false`            |
| `_r`   | Real      | Floating-point numbers (e.g., 3.14) |
| `_s`   | String    | Text, enclosed in double quotes if it contains spaces |
| `_t`   | Table     | A table                      |
| `_f`   | Function  | A function or procedure      |
| `_name`| Custom    | A user-defined type          |

## Examples

Here are some examples of how to use NDF.

### Simple Table

Here's how you define a table for a 2D point and create an instance of it:

```ndf
point2d x_i y_i

some_point2d = , 10 20 ,
```

### Table with Different Data Types

This example shows a `book` table with an author, a name, and a publication status.

```ndf
book author_s name_s published_b

herberts_book = , "Frank Herbert" "Dune" true ,
```

### Nested Tables

You can nest tables to create more complex data structures. Here, a `shelf` contains a `book` and a level.

```ndf
book author_s name_s published_b
shelf book_book level_i

first_shelf = , "Balzac" "Human comedy" true , 2 ,
```

### Custom Types

NDF allows you to define custom types, which are essentially other tables.

```ndf
point2d x_i y_i
twopoints start_point2d end_point2d

twopoints = , 10 20 , 30 40 ,
```

## Comments

To add comments to an NDF file, you can use a hash `#`.

```ndf
point2d x_i y_i ; Defines a 2D point
```

## File Extension

The recommended file extension for NDF files is `.ndf`.
