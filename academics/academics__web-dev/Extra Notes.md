## **Regular Expressions in JavaScript (RegEx)**

A Regular Expression (RegEx) is a sequence of characters that defines a search pattern. In JavaScript, RegEx is commonly used for string matching and manipulation, such as searching, replacing, and validating data in text.

## **Creating a RegEx in JavaScript**
There are two ways to define a RegEx in JavaScript:

1. **Literal notation**: 
   ```javascript
   let regex = /pattern/flags;
   ```

2. **Using `RegExp` constructor**:
   ```javascript
   let regex = new RegExp("pattern", "flags");
   ```

## **Flags in Regular Expressions**

Flags in Regular Expressions are optional parameters that modify the behavior of the search pattern. They are written after the closing slash of a literal RegEx (or as the second argument in the `RegExp` constructor). These flags allow you to fine-tune how the search is performed, such as making it case-insensitive or enabling global matching.

1. **`g` (Global Search)**:
   - Searches for **all occurrences** of the pattern in the string, not just the first one.
   - Without this flag, the RegEx will stop after finding the first match.
   ```javascript
   let regex = /cat/g;
   let text = "The cat is a friendly cat.";
   console.log(text.match(regex));  // ["cat", "cat"]
   ```

2. **`i` (Case-Insensitive Search)**:
   - Makes the search **case-insensitive**, meaning it will match both lowercase and uppercase letters.
   ```javascript
   let regex = /hello/i;
   let text = "Hello World!";
   console.log(regex.test(text));  // true
   ```

3. **`m` (Multi-line Search)**:
   - Treats the **start (`^`) and end (`$`)** anchors of the pattern as spanning across **multiple lines**. It allows matching patterns at the beginning and end of each line, not just the start and end of the entire string.
   ```javascript
   let regex = /^hello/m;
   let text = `hello world
   goodbye world`;
   console.log(regex.test(text));  // true
   ```

## **Regular Expressions (RegEx) Metacharacters **

Metacharacters are special symbols in RegEx that have a specific meaning beyond their literal character interpretation. They allow you to create dynamic patterns for matching more complex string structures.
Here’s a breakdown of common metacharacters and their uses:
#### **1. `.` (Dot)**
- **Matches any character** (except newline `\n`).
- Example:
   ```javascript
   let regex = /h.t/;
   let text = "hat, hit, hut";
   console.log(text.match(regex));  // ["hat"]
   ```

#### **2. `^` (Caret)**
- **Anchors the match to the beginning of the string** or a line when used in multiline mode.
- Example:
   ```javascript
   let regex = /^Hello/;
   let text = "Hello world";
   console.log(regex.test(text));  // true
   ```

#### **3. `$` (Dollar Sign)**
- **Anchors the match to the end of the string** or the end of a line in multiline mode.
- Example:
   ```javascript
   let regex = /world$/;
   let text = "Hello world";
   console.log(regex.test(text));  // true
   ```

#### **4. `[]` (Character Set)**
- **Matches any one of the characters inside the brackets**.
- You can also define a range of characters.
- Example:
   ```javascript
   let regex = /[aeiou]/;
   let text = "apple";
   console.log(text.match(regex));  // ["a"]
   ```

#### **5. `|` (Alternation)**
- **Acts as an OR operator**, matching either the pattern on the left or right of `|`.
- Example:
   ```javascript
   let regex = /cat|dog/;
   let text = "I love cats and dogs.";
   console.log(text.match(regex));  // ["cat"]
   ```

#### **6. `()` (Grouping)**
- **Groups subpatterns** together. Useful for capturing parts of a match or applying quantifiers to the entire group.
- Example:
   ```javascript
   let regex = /(cat|dog)/;
   let text = "I have a cat and a dog.";
   console.log(text.match(regex));  // ["cat"]
   ```

#### **7. `\` (Escape Character)**
- **Escapes a metacharacter** to treat it as a literal.
- Example:
   ```javascript
   let regex = /\$/;  // Matches the dollar sign '$'
   let text = "Cost is $5";
   console.log(text.match(regex));  // ["$"]
   ```

### **Quantifiers in Regular Expressions (RegEx)**

Quantifiers in RegEx allow you to specify **how many times** a pattern should be matched. They are used to define repetition, whether you want a pattern to match **zero, one, or multiple times**. Quantifiers are applied to the element (character, group, or set) that immediately precedes them.

#### **Types of Quantifiers:**

1. **`*` (Zero or More)**
   - **Matches zero or more occurrences** of the preceding element.
   - It can match none or an unlimited number of times.
   - Example:
     ```javascript
     let regex = /a*/;
     let text = "aaaa";
     console.log(text.match(regex));  // ["aaaa"]
     ```
   - In this case, the `*` matches any sequence of "a" characters, including zero occurrences.

2. **`+` (One or More)**
   - **Matches one or more occurrences** of the preceding element.
   - It requires at least one match.
   - Example:
     ```javascript
     let regex = /a+/;
     let text = "aa";
     console.log(text.match(regex));  // ["aa"]
     ```
   - The `+` requires that at least one "a" is present in the match.

3. **`?` (Zero or One)**
   - **Matches zero or one occurrence** of the preceding element.
   - It makes the preceding element optional.
   - Example:
     ```javascript
     let regex = /colou?r/;  // Matches "color" or "colour"
     let text = "color";
     console.log(regex.test(text));  // true
     ```
   - Here, the `u` is optional, so it matches both "color" and "colour."

4. **`{n}` (Exact Count)**
   - **Matches exactly `n` occurrences** of the preceding element.
   - Example:
     ```javascript
     let regex = /a{3}/;
     let text = "aaaa";
     console.log(text.match(regex));  // ["aaa"]
     ```
   - The pattern `a{3}` matches exactly three "a" characters.

5. **`{n,}` (At Least `n` Times)**
   - **Matches at least `n` occurrences** of the preceding element, with no upper limit.
   - Example:
     ```javascript
     let regex = /a{2,}/;
     let text = "aaaa";
     console.log(text.match(regex));  // ["aaaa"]
     ```
   - This pattern matches "a" repeated at least twice.

6. **`{n,m}` (Between `n` and `m` Times)**
   - **Matches between `n` and `m` occurrences** of the preceding element.
   - Example:
     ```javascript
     let regex = /a{2,4}/;
     let text = "aaaaa";
     console.log(text.match(regex));  // ["aaaa"]
     ```
   - The pattern `a{2,4}` matches between two and four "a" characters.

#### **Examples of Quantifiers in Action**

1. **Matching Digits with Exact Count**:
   ```javascript
   let regex = /\d{3}/;
   let text = "Phone: 123-456";
   console.log(text.match(regex));  // ["123"]
   ```
   - This will match exactly three digits.

2. **Matching at Least Two Digits**:
   ```javascript
   let regex = /\d{2,}/;
   let text = "12 123 1234";
   console.log(text.match(regex));  // ["12", "123", "1234"]
   ```
   - Matches sequences of digits with a minimum of two.

3. **Matching Optional Characters**:
   ```javascript
   let regex = /colou?r/;  // Matches both "color" and "colour"
   let text = "color, colour";
   console.log(text.match(regex));  // ["color", "colour"]
   ```
## ***Mthods in regEx*** ;
In Regular Expressions (RegEx), the methods `find`, `match`, and `replace` are commonly used for searching and manipulating strings. Here’s a detailed look at how to use these methods effectively in JavaScript:

### **1. Finding Matches with `String.prototype.match()`**

The `match()` method retrieves the matches when matching a string against a regular expression. It returns an array of matches or `null` if no matches are found.

#### **Syntax:**
```javascript
string.match(regex);
```

#### **Examples:**

- **Basic Match**:
  ```javascript
  let text = "Hello, world!";
  let regex = /world/;
  let result = text.match(regex);
  console.log(result);  // ["world"]
  ```

- **Global Matches**:
  If the regular expression has the global flag `g`, `match()` returns an array of all matches.
  ```javascript
  let text = "abcabcabc";
  let regex = /abc/g;
  let result = text.match(regex);
  console.log(result);  // ["abc", "abc", "abc"]
  ```

- **Capturing Groups**:
  `match()` returns the full match and any captured groups.
  ```javascript
  let text = "Date: 2024-10-04";
  let regex = /(\d{4})-(\d{2})-(\d{2})/;
  let result = text.match(regex);
  console.log(result);  // ["2024-10-04", "2024", "10", "04"]
  ```

---

### **2. Replacing with `String.prototype.replace()`**

The `replace()` method is used to search a string for a match against a regular expression and replace the matched substring with a new substring.

#### **Syntax:**
```javascript
string.replace(regex, newSubstr);
```

- You can also use a function as the second argument to perform more complex replacements.

#### **Examples:**

- **Simple Replacement**:
  ```javascript
  let text = "Hello, world!";
  let regex = /world/;
  let result = text.replace(regex, "there");
  console.log(result);  // "Hello, there!"
  ```

- **Global Replacement**:
  When using the global flag `g`, all occurrences of the match will be replaced.
  ```javascript
  let text = "abcabcabc";
  let regex = /abc/g;
  let result = text.replace(regex, "xyz");
  console.log(result);  // "xyzxyzxyz"
  ```

- **Using a Function for Replacement**:
  You can use a function to dynamically create the replacement string.
  ```javascript
  let text = "I have 2 apples and 3 bananas.";
  let regex = /(\d+)/g;  // Matches one or more digits
  let result = text.replace(regex, (match) => {
    return Number(match) * 2;  // Double the number
  });
  console.log(result);  // "I have 4 apples and 6 bananas."
  ```

---

### **3. Finding Matches with `String.prototype.search()`**

The `search()` method executes a search for a match between a regular expression and this `String` object. It returns the index of the first match or `-1` if no match is found.

#### **Syntax:**
```javascript
string.search(regex);
```

#### **Examples:**

- **Basic Search**:
  ```javascript
  let text = "Hello, world!";
  let regex = /world/;
  let result = text.search(regex);
  console.log(result);  // 7 (the index where "world" starts)
  ```

- **Using Global Flag**:
  The global flag does not affect the `search()` method; it only returns the index of the first match.
  ```javascript
  let text = "abcabcabc";
  let regex = /abc/g;
  let result = text.search(regex);
  console.log(result);  // 0 (the index of the first match)
  ```


## **Functions Using RegEx in JavaScript**
1. **`test()`**: Tests for a match in a string, returns `true` or `false`.
   ```javascript
   let regex = /cat/;
   console.log(regex.test("I have a cat"));  // true
   ```

2. **`exec()`**: Executes a search and returns an array or `null`.
   ```javascript
   let regex = /cat/;
   let result = regex.exec("I have a cat");
   console.log(result);  // ["cat"]
   ```

3. **`replace()`**: Replaces matched text in a string.
   ```javascript
   let result = "I have a cat".replace(/cat/, "dog");
   console.log(result);  // "I have a dog"
   ```

---
---
---

## **Question/Answers for Viva** 



