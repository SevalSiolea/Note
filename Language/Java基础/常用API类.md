## 字符串

### `String`

**`public final class` `java.lang.String` implements `Serializable`, `Comparable< String >`, `CharSequence`**

#### Introduce

The `String` class represents character strings.
All string literals in Java programs, such as `"abc"`, are implemented as instances of this class.
Strings are constant; their values cannot be changed after they are created. Because String objects are immutable they can be shared. For example: `String str = "abc";` is equivalent to: `char data[] = {'a', 'b', 'c'}; String str = new String(data);`

The Java language provides special support for the string concatenation operator ( + ), and for conversion of other objects to strings. String concatenation is implemented through the `StringBuilder`(or `StringBuffer`) class and its `append` method. String conversions are implemented through the method `toString`, defined by `Object` and inherited by all classes in Java.

A `String` represents a string in the UTF-16 format in which *supplementary characters* are represented by *surrogate pairs*. Index values refer to `char` code units, so a supplementary character uses two positions in a `String`. The `String` class provides methods for dealing with Unicode code points (i.e., characters), in addition to those for dealing with Unicode code units (i.e., `char` values).

#### Field

`static Comparator<String> CASE_INSENSITIVE_ORDER` A Comparator that orders `String` objects as by `compareToIgnoreCase`.

#### Constructor

`String()` Initializes a newly created `String` object so that it represents an empty character sequence.

`String( byte[] bytes )` Constructs a new `String` by decoding the specified array of bytes using the platform's default charset.

`String( bytes[] bytes, String charsetName )` Constructs a new `String` by decoding the specified array of bytes using the specified charset.

`String( char[] value )` Allocates a new `String` so that it represents the sequence of characters currently contained in the character array argument.

`String( String original )` Initializes a newly created `String` object so that it represents the same sequence of characters as the argument; in other words, the newly created string is a copy of the argument string.

`String( StringBuilder builder )` Allocates a new string that contains the sequence of characters currently contained in the string builder argument.

#### 1  `length`

`public int length()`

Returns the length of this string. The length is equal to the number of Unicode code units in the string.

#### 2  `codePointCount`

`public int codePointCount( int beginIndex, int endIndex )`

Returns the number of Unicode code points in the specified text range of this `String`. The text range begins at the specified `beginIndex` and extends to the `char` at index `endIndex - 1`. Thus the length (in `char`s) of the text range is `endIndex-beginIndex`. Unpaired surrogates within the text range count as one code point each.

**Throws** : `IndexOutOfBoundsException` - if the `beginIndex` is negative, or `endIndex` is larger than the length of this `String`, or `beginIndex` is larger than `endIndex`.

#### 3  `isEmpty`

`public boolean isEmpty()`

Returns `true` if and only if `length()` is `0`.

#### 4  `charAt`

`public char charAt( int index )`

Returns the `char` value at the specified index. An index ranges from `0` to `length() - 1`. If the `char` value specified by the index is a surrogate, the surrogate value is returned.

#### 5  `offsetByCodePoints`

`public int offsetByCodePoints( int index, int codePointOffset )`

Returns the index within this `String` that is offset from the given `index` by `codePointOffset` code points. Unpaired surrogates within the text range given by `index` and `codePointOffset` count as one code point each.

**Throws** : `IndexOutOfBoundsException` - if `index` is negative or larger then the length of this `String`, or if `codePointOffset` is positive and the substring starting with `index` has fewer than `codePointOffset` code points, or if `codePointOffset` is negative and the substring before `index` has fewer than the absolute value of `codePointOffset` code points.

#### 6  `codePointAt`

`public int codePointAt( int index )`

Returns the character (Unicode code point) at the specified index. The index refers to `char` values (Unicode code units) and ranges from `0` to `length() - 1`.

If the `char` value specified at the given index is in the high-surrogate range, the following index is less than the length of this `String`, and the `char` value at the following index is in the low-surrogate range, then the supplementary code point corresponding to this surrogate pair is returned. Otherwise, the `char` value at the given index is returned.

#### 7  `equalsIgnoreCase`

`public boolean equalsIgnoreCase( String anotherString )`

Compares this `String` to another `String`, ignoring case considerations. Two strings are considered equal ignoring case if they are of the same length and corresponding characters in the two strings are equal ignoring case.

#### 8  `compareTo`

`public int compareTo( String anotherString )`

Compares two strings lexicographically. The comparison is based on the Unicode value of each character in the strings. The character sequence represented by this `String` object is compared lexicographically to the character sequence represented by the argument string. The result is a negative integer if this `String` object lexicographically precedes the argument string. The result is a positive integer if this `String` object lexicographically follows the argument string. The result is zero if the strings are equal; `compareTo` returns `0` exactly when the `equals(Object)` method would return `true`.

This is the definition of lexicographic ordering. If two strings are different, then either they have different characters at some index that is a valid index for both strings, or their lengths are different, or both. If they have different characters at one or more index positions, let *k* be the smallest such index; then the string whose character at position *k* has the smaller value, as determined by using the < operator, lexicographically precedes the other string. In this case, `compareTo` returns the difference of the two character values at position `k` in the two string -- that is, the value:

`this.charAt( k ) - anotherString.charAt( k )`


If there is no index position at which they differ, then the shorter string lexicographically precedes the longer string. In this case, `compareTo` returns the difference of the lengths of the strings -- that is, the value:

`this.length() - anotherString.length()`

**Returns** : the value `0` if the argument string is equal to this string; a value less than `0` if this string is lexicographically less than the string argument; and a value greater than `0` if this string is lexicographically greater than the string argument.

#### 9  `compareToIgnoreCase`

`public int compareToIgnoreCase( String str )`

Compares two strings lexicographically, ignoring case differences. 

#### 10-1  `indexOf`

`public int indexOf( int ch )`

Returns the index within this string of the first occurrence of the specified character. If a character with value `ch` occurs in the character sequence represented by this `String` object, then the index (in Unicode code units) of the first such occurrence is returned. 

For values of `ch` in the range from 0 to 0xFFFF (inclusive), this is the smallest value *k* such that : `this.charAt( k ) == ch` is true. 

For other values of `ch`, it is the smallest value *k* such that : `this.codePointAt( k ) == ch` is true. 

In either case, if no such character occurs in this string, then `-1` is returned.

**Parameters** : `ch` - a character (Unicode code point).

**Returns** : the index of the first occurrence of the character in the character sequence represented by this object, or `-1` if the character does not occur.

#### 10-2  `indexOf`

`public int indexOf( int ch, int fromIndex )`

Returns the index within this string of the first occurrence of the specified character, starting the search at the specified index.

#### 10-3  `indexOf`

`public int indexOf( String str )`

Returns the index within this string of the first occurrence of the specified substring. If no such value of *k* exists, then `-1` is returned.

#### 10-4  `indexOf`

`public int indexOf( String str, int fromIndex )`

Returns the index within this string of the first occurrence of the specified substring, starting at the specified index. If no such value of *k* exists, then `-1` is returned.

#### 11  `substring`

`public String substring( int beginIndex, int endIndex )`

Returns a string that is a substring of this string. The substring begins at the specified `beginIndex` and extends to the character at index `endIndex - 1`. Thus the length of the substring is `endIndex-beginIndex`.

**Throws** : `IndexOutOfBoundsException` - if the `beginIndex` is negative, or `endIndex` is larger than the length of this `String` object, or `beginIndex` is larger than `endIndex`.

#### 12  `replace`

Returns a string resulting from replacing all occurrences of `oldChar` in this string with `newChar`.

#### 13  `matches`

`public boolean matches( String regex )`

Tells whether or not this string matches the given regular expression.

**Throws** : `PatternSyntaxException` - if the regular expression's syntax is invalid.

#### 14  `replaceAll`

`public String replaceAll( String regex, String replacement )`

Replaces each substring of this string that matches the given regular expression with the given replacement.

**Throws** : `PatternSyntaxException` - if the regular expression's syntax is invalid.

#### 15  `contains`

`public boolean contains( CharSequence s )`

Returns true if and only if this string contains the specified sequence of char values.

#### 16  `replace`

`public String replace( CharSequence target, CharSequence replacement )`

Replaces each substring of this string that matches the literal target sequence with the specified literal replacement sequence. 

The replacement proceeds from the beginning of the string to the end, for example, replacing "aa" with "b" in the string "aaa" will result in "ba" rather than "ab".

#### 17-1  `split`

`public String[] split( String regex, int limit )`

Splits this string around matches of the given regular expression.

The array returned by this method contains each substring of this string that is terminated by another substring that matches the given expression or is terminated by the end of the string. The substrings in the array are in the order in which they occur in this string. If the expression does not match any part of the input then the resulting array has just one element, namely this string.

When there is a positive-width match at the beginning of this string then an empty leading substring is included at the beginning of the resulting array. A zero-width match at the beginning however never produces such empty leading substring.

The `limit` parameter controls the number of times the pattern is applied and therefore affects the length of the resulting array. If the limit *n* is greater than zero then the pattern will be applied at most *n* - 1 times, the array's length will be no greater than *n*, and the array's last entry will contain all input beyond the last matched delimiter. 
If *n* is non-positive then the pattern will be applied as many times as possible and the array can have any length. 
If *n* is zero then the pattern will be applied as many times as possible, the array can have any length, and trailing empty strings will be discarded.

**Throws** : `PatternSyntaxException` - if the regular expression's syntax is invalid.

#### 17-2  `split`

`public String[] split( String regex )`

Splits this string around matches of the given regular expression.

This method works as if by invoking the two-argument `split` method with the given expression and a limit argument of zero. Trailing empty strings are therefore not included in the resulting array.

**Throws** : `PatternSyntaxException` - if the regular expression's syntax is invalid.

#### 18  `join`

`public static String join( CharSequence delimiter, CharSequence... elements )`

Returns a new String composed of copies of the `CharSequence elements` joined together with a copy of the specified `delimiter`.

Note that if an element is null, then `"null"` is added.

#### 19  `toLowerCase`

`public String toLowerCase()`

Converts all of the characters in this `String` to lower case using the rules of the default locale. This is equivalent to calling `toLowerCase( Locale.getDefault() )`.

This method is locale sensitive, and may produce unexpected results if used for strings that are intended to be interpreted locale independently. To obtain correct results for locale insensitive strings, use `toLowerCase( Locale.ROOT )`.

#### 20  `toUpperCase`

`public String toUpperCase()`

Converts all of the characters in this `String` to upper case using the rules of the default locale. This method is equivalent to `toUpperCase( Locale.getDefault() )`.

This method is locale sensitive, and may produce unexpected results if used for strings that are intended to be interpreted locale independently. To obtain correct results for locale insensitive strings, use `toUpperCase( Locale.ROOT )`.

#### 21  `trim`

`public String trim()`

Returns a string whose value is this string, with any leading and trailing whitespace removed.

#### 22  `toCharArray`

`public char[] toCharArray()`

Converts this string to a new character array.

#### 23  `format`

`public static String format( String format, Object... args )`

Returns a formatted string using the specified format string and arguments.

The locale always used is the one returned by `Locale.getDefault()`.

If there are more arguments than format specifiers, the extra arguments are ignored. The number of arguments is variable and may be zero. 

**Throws** : `IllegalFormatException` - If a format string contains an illegal syntax, a format specifier that is incompatible with the given arguments, insufficient arguments given the format string, or other illegal conditions.

#### 24-1  `valueOf`

`public static String valueOf( Object obj )`

Returns the string representation of the `Object` argument.

**Returns** : if the argument is `null`, then a string equal to `"null"`; otherwise, the value of `obj.toString()` is returned.

#### 24-2  `valueOf`

`public static String valueOf( char[] data )`

Returns the string representation of the `char` array argument.

#### 25  `intern`

`public String intern()`

Returns a canonical representation for the string object.

A pool of strings, initially empty, is maintained privately by the class `String`.

When the intern method is invoked, if the pool already contains a string equal to this `String` object as determined by the `equals( Object )` method, then the string from the pool is returned. Otherwise, this `String` object is added to the pool and a reference to this `String` object is returned.

All literal strings and string-valued constant expressions are interned.

**Returns** : a string that has the same contents as this string, but is guaranteed to be from a pool of unique strings.

### `StringBuilder`

## 数组

### `Array`

### `Arrays`

## 计算

### `Math`

### `BigInteger`

### `BigDecimal`

## 反射

### `Class`

### `Field`

### `Method`

### `Constructor`