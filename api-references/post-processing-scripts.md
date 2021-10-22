# Post-Processing Scripts

## JavaScript I/O

`input` will be a global variable accessible in the JS context. The structure of `input` is the following:

```javascript
interface Input = {
  text: string,
  textbox: TextBox
}
```

where

```javascript
interface TextBox {
  // TopLeft.x, TopLeft.y, TopRight.x, TopRight.y, BottomRight.x, BottomRight.y, BottomLeft.x, BottomLeft.y
  vertices: number[], 
  orientation: "Up" | "Left" | "Right" | "Down",
  lines: {
      words: Word[]
  }
}

interface Word {
  // TopLeft.x, TopLeft.y, TopRight.x, TopRight.y, BottomRight.x, BottomRight.y, BottomLeft.x, BottomLeft.y
  vertices: number[],
  value: string, // text in the word
  symbols: Symbol[]
}

interface Symbol {
  // TopLeft.x, TopLeft.y, TopRight.x, TopRight.y, BottomRight.x, BottomRight.y, BottomLeft.x, BottomLeft.y
  vertices: number[],
  value: string // character in the symbol
}
```

The script is expected to write the output to the `result` value in the global scope. If not, an exception will be raised. What is assigned to `result`will be in the `content` field of the output response.

## Helper Functions

FormX's post-processing script comes with the following helper functions:

```javascript
fuzzy_search(pattern, text, options)
```

This searches through a text with user-defined pattern

Parameters:

* pattern (string): Will be used to search target text
* text (string): The target text where search will be conducted upon
* options (FuzzySearchOptions): _Optional parameters_
  * Options for configuring the fuzzy search behaviour
    * max\_subs (number)_Optional_\
      __Maximum subsitutions between the pattern and return string
    * max\_insert (number) _Optional_\
      Amount of character that can be skipped in the pattern
    * max\_delete (number) _Optional_\
      __Amount of character that can be skipped in the return string
    * max\_l\_dist (number) _Optional_\
      Maximum Levenshtein distance allowed between the pattern and return string

Return Value:

* matches (Match\[]): Array of matches
  * start (number): Start position of the match
  * end (number): End position of the match
  * dist (number): Levenshtein distance between the matched part and the pattern
  * matched (string): matched part

```javascript
edit_distance(string1, string2)
```

Returns the distance between two strings

Parameters:

* string1 (string)**: **First string that will be compared with the other
* string2 (string): The other string

Return Value:

* Edit distance (number)
