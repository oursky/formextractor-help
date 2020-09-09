# Post-Processing Scripts

### How to use Post-Processing Script to refine the result?

{% hint style="success" %}
TODO: Screenshot here
{% endhint %}

* Create a Detection Area with Blue Anchor
* Click **Add New Field** and select **Script** as the **Type**
* Click **Edit Script** to open the script editing window

### How the script works?

`input` will be a global variable is accessible in the JS context. Structure of `input` is

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

It is expected the script will write the output to the `result` value in the global scope. If not, an exception will be raised. What assigned to `result`will be in the `content` field of the output response.

### Help Functions

FormExtractor Post-Processing Script provide the following functions as helper function:

```javascript
fuzzy_search(pattern, text, options)
```

Searches through a text with user-defined pattern

Parameters:

* pattern \(string\): Will be used to search target text
* text \(string\): The target text where search will be conducted upon
* options \(FuzzySearchOptions\): _Optional_ Options for configuring the fuzzy search behaviour
  * max\_subs \(number\)_Optional_ maximum subsitutions between the pattern and return string
  * max\_insert \(number\) _Optional_ amount of character that can be skipped in the pattern
  * max\_delete \(number\) _Optional_ amount of character that can be skipped in the return string
  * max\_l\_dist \(number\) _Optional_ maximum Levenshtein distance allowed between the pattern and return string

Return Value:

* matches \(Match\[\]\): array of matches
  * start \(number\): start position of the match
  * end \(number\): end position of the match
  * dist \(number\): Levenshtein distance between the matched part and the pattern
  * matched \(string\): matched part

```javascript
edit_distance(string1, string2)
```

Returns the distance between two strings

Parameters:

* string1 \(string\)**:** First string that will be compared with the other
* string2 \(string\): The other string

Return Value:

* Edit distance \(number\)

### Examples

{% hint style="success" %}
TODO
{% endhint %}

