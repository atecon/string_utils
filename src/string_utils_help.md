# String Utils Package

This package is a collection of helper functions for various operations of string variables and string arrays which are not covered by gretl's built-in methods (yet).

Please ask questions and report bugs on the gretl mailing list if possible. Alternatively, create an issue ticket on the [github repo](https://github.com/atecon/string_utils).

# Public functions

`camelcase(string input)`

Camel-case is a capitalization of the first letter (and the remaining letters are lowercase) before concatenating each of the space-separated words to a single word. Words of the 'input' variable are expected to be separated by space. Eventual spaces at the beginning or end of the string are removed before return.

**Arguments:**

- `input` - string, Input string

**Return:**

String in camel-case format.

---

`capitalize(string input)`

Convert first letter of a string to uppercase and other letters to lowercase. Eventual spaces will not be removed before return.

**Arguments:**

- `input` - string, String to be capitalized

**Return:**

Returns capitalized string.

---

`strfind(const string search, const string find)`

Finds a substring in a string and returns the index of the substring. Eventual spaces are not ignored. If 'find' exists multiple times, the position of its first occurrence is returned.

**Arguments:**

- `search` - string, String to be searched
- `find` - string, String to find

**Return:**

Position of the 'find' string within the search string. In case, `find` is not found in the `search` string, the scalar value 0 is returned.

---

`msortby_rowlabels(const matrix X, const strings rowlabels_new)`

Sort rows of matrix `X` by re-ordering row-labels of `X` by string array `rowlabels_new`.

**Arguments:**

- `X` - matrix, must include row-labels
- `rowlabels_new` - string array, re-order `X` row-labels by this string

**Return:**

Matrix with sorted rows of `X` by `rowlabels_new`. `X` must have row-labels. Also, all elements in `rowlabels_new` must be present in `X` row-labels too, otherwise an empty matrix is returned (can be checked by <nelem(matrix)>).

---

`snakecase(string input)`

The snakecase is a style replacing spaces by underscores, and transforming all letters to lowercase. Words of the `input` variable are expected to be separated by space. Eventual spaces at the beginning or end of the string are removed before return.

**Arguments:**

- `input` - string, Input string

**Return:**

String in snake-case format.

---

`strdrop(strings S, string pattern)`

Drop a specific string pattern from string array `S`. String `pattern` may occur multiple times.

**Arguments:**

- `S` - string array, Input
- `pattern` - string, Pattern of string value to be dropped from S

**Return:**

String array excluding string `pattern` if present in `S`. If `drop_str` is not present, the original array `S` is returned instead. If string array `S` has length zero, an empty array is returned.

---

`strrepl(const string S, const int n[1::])`

Copy string n-times into a string array `S` of length `n`.

**Arguments:**

- `S` - string, String to be repeated `n` times
- `n` - int, Number of times to repeat `S`

**Return:**

Array containing string `S` n-times. Also works for an empty string `S`.

---

`strsandwich(matrix x, const string prefix[null], const string suffix[null])`

Construct a string array. To each numerical value of `x`, concatenate a string `prefix` and a `suffix`.

**Arguments:**

- `x` - matrix, holding numerical values
- `prefix` - string, prefix to add (optional, default = "")
- `suffix` - string, suffix to add (optional, default = "")

**Return:**

Array of length `n=rows(vec(x))`. Each string is a combination of the `prefix`, the i-th numerical value of `x` and the `suffix`.

---

`strstarts(const string target, const string pattern)`

Check whether `target` starts with `pattern`.

**Arguments:**

- `target` - string, String being searched
- `pattern` - string, Pattern to search for

**Return:**

`TRUE` if `target` starts with `pattern`, otherwise `FALSE`.

---

`strends(const string target, const string pattern)`

Check whether `target` ends with `pattern`.

**Arguments:**

- `target` - string, String being searched
- `pattern` - string, Pattern to search for

**Return:**

`TRUE` if `target` ends with `pattern`, otherwise `FALSE`.

---

`struniq(const strings input, const bool do_sort[FALSE])`

The function takes an array of strings (`input`) and a boolean flag (`do_sort`) as input. It returns an array of unique strings from the input array. If `do_sort` is `TRUE`, the input array is sorted before extracting unique values. If `do_sort` is `FALSE`, the function uses a more complex method to extract unique values without changing the original order of the input array. **NOTE:** If speed is relevant for your task, you should set `do_sort = TRUE` which is much faster.

**Arguments:**

- `S` - strings, Array of input strings
- `do_sort` - bool, Sort the unique values in alphabetic order if `TRUE`, otherwise return the unique values in order of appearance.

**Return:**

Array containing the distinct elements of array `input` either sorted or not. Empty items of the array are placed first.

---

`titlecase(string input)`

The titlecase is a capitalization style used for titles so that the first letter of each word is uppercase, and the remaining letters are lowercase. Words are expected to be separated by space. Space at the beginning or end of the string are removed.

**Arguments:**

- `input` - string, Input string

**Return:**

"titlelized" string.

# Changelog:

*0.7, December 2023*

- The `struniq()` function now supports ordering of the unique values.
- Remove the `strflatten()` function. Use the built-in `flatten()` function instead which accepts an arbitrary delimiter string since version 2022c.
- Improved speed for both the `struniq()` and `strdrop()` function, respectively.
- New minimal version requirement is 2023c.

*0.6, November 2023*

- Added the `strstarts()` and `strends()` functions.
- The `struniq()` function now supports not sorting the unique values.
- Fixed a bug in the `strfind()` function where it would return incorrect results if the search string contained special characters.

*0.5, October 2023*

- Added the `struniq()` and `strdrop()` functions.
- The `strrepl()` function now supports repeating an empty string.
- Fixed a bug in the `msortby_rowlabels()` function where it would not correctly sort the rows if the row labels contained numbers.

*0.4, September 2023*

- Added the `msortby_rowlabels()` function.
- The `strfind()` function now returns 0 if the substring is not found.
- Fixed a bug in the `strsandwich()` function where it would not correctly concatenate the prefix and suffix if they contained special characters.

*0.3, August 2023*

- Added the `strsandwich()` function.
- The `strfind()` function now ignores leading and trailing spaces in the search string and the substring.
- Fixed a bug in the `camelcase()` function where it would not correctly capitalize the first letter of the string if it was a special character.

*0.2, July 2023*

- Added the `strfind()`, `camelcase()`, and `titlecase()` functions.
- The `capitalize()` function now ignores leading and trailing spaces in the string.
- Fixed a bug in the `snakecase()` function where it would not correctly replace spaces with underscores if the string contained special characters.

*0.1, June 2023*

- Initial release.
- Added the `capitalize()` and `snakecase()` functions.
