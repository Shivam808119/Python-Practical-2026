# Python Programming – Practical File

| | |
|---|---|
| **Name** | Shivam Pal |
| **Roll No.** | 26570055 |
| **Course / Semester** | B.Sc. (Hons.) Computer Science, Semester I |
| **College** | Ramanujan College, University of Delhi |
| **Submitted To** | Dr. Aakash |
| **Session** | 2026–27 |
| **Tool** | Python 3 |

---

## Table of Contents

| No. | Practical | File |
|:---:|---|---|
| 1 | [Roots of a Quadratic Equation](#practical-1-roots-of-a-quadratic-equation) | `practical_01_quadratic.py` |
| 2 | [Prime Numbers](#practical-2-prime-numbers) | `practical_02_prime_numbers.py` |
| 3 | [Pyramid and Reverse Pyramid](#practical-3-pyramid-and-reverse-pyramid) | `practical_03_pyramids.py` |
| 4 | [Character Check](#practical-4-character-check) | `practical_04_character_check.py` |
| 5 | [Operations on a String](#practical-5-operations-on-a-string) | `practical_05_string_operations.py` |
| 6 | [Swap First n Characters of Two Strings](#practical-6-swap-first-n-characters-of-two-strings) | `practical_06_swap_characters.py` |
| 7 | [Indices of a Substring](#practical-7-indices-of-a-substring) | `practical_07_find_substring_indices.py` |
| 8 | [Cubes of Even Integers](#practical-8-cubes-of-even-integers) | `practical_08_cubes_of_even.py` |
| 9 | [File Handling](#practical-9-file-handling) | `practical_09_file_handling.py` |
| 10 | [Class Point](#practical-10-class-point) | `practical_10_point_class.py` |
| 11 | [Dictionary of Cubes](#practical-11-dictionary-of-cubes) | `practical_11_dictionary_cubes.py` |
| 12 | [Tuple Operations](#practical-12-tuple-operations) | `practical_12_tuples.py` |
| 13 | [Exception Handling](#practical-13-exception-handling) | `practical_13_exception_handling.py` |

> **How to run:** `python practical_01_quadratic.py` (replace with the file name of the practical).

---

## Practical 1: Roots of a Quadratic Equation

**Question:** WAP to find the roots of a quadratic equation.

**Program** (`practical_01_quadratic.py`)

```python
# Practical 1: WAP to find the roots of a quadratic equation  (ax^2 + bx + c = 0)
import cmath


def quadratic_roots(a, b, c):
    """Return the two roots of ax^2 + bx + c = 0 (real or complex)."""
    d = b ** 2 - 4 * a * c            # discriminant
    root1 = (-b + cmath.sqrt(d)) / (2 * a)
    root2 = (-b - cmath.sqrt(d)) / (2 * a)
    return d, root1, root2


print("Quadratic equation: ax^2 + bx + c = 0")
a = float(input("Enter a: "))
b = float(input("Enter b: "))
c = float(input("Enter c: "))

if a == 0:
    print("'a' cannot be 0 - this is not a quadratic equation.")
    if b != 0:
        print("It is linear, with root x =", -c / b)
else:
    d, r1, r2 = quadratic_roots(a, b, c)
    print("Discriminant =", d)
    if d > 0:
        print("Roots are real and distinct.")
        print("x1 =", r1.real, "\nx2 =", r2.real)
    elif d == 0:
        print("Roots are real and equal.")
        print("x1 = x2 =", r1.real)
    else:
        print("Roots are complex conjugates.")
        print("x1 =", r1, "\nx2 =", r2)
```

**Output**

```text






```

---

## Practical 2: Prime Numbers

**Question:** WAP to accept a number 'n' and

- a. Check if 'n' is prime
- b. Generate all prime numbers till 'n'
- c. Generate first 'n' prime numbers

This program may be done using functions.

**Program** (`practical_02_prime_numbers.py`)

```python
# Practical 2: WAP to accept a number 'n' and
#   a. Check if 'n' is prime
#   b. Generate all prime numbers till 'n'
#   c. Generate first 'n' prime numbers
# (done using functions)


def is_prime(num):
    """Return True if num is a prime number."""
    if num < 2:
        return False
    i = 2
    while i * i <= num:
        if num % i == 0:
            return False
        i += 1
    return True


def primes_till(n):
    """Return a list of all primes <= n."""
    return [i for i in range(2, n + 1) if is_prime(i)]


def first_n_primes(n):
    """Return a list of the first n primes."""
    result = []
    candidate = 2
    while len(result) < n:
        if is_prime(candidate):
            result.append(candidate)
        candidate += 1
    return result


n = int(input("Enter a number n: "))

# a
if is_prime(n):
    print(f"a) {n} is a prime number")
else:
    print(f"a) {n} is not a prime number")

# b
print(f"b) Prime numbers till {n}:", primes_till(n))

# c
print(f"c) First {n} prime numbers:", first_n_primes(n))
```

**Output**

```text






```

---

## Practical 3: Pyramid and Reverse Pyramid

**Question:** WAP to create a pyramid of the character '\*' and a reverse pyramid.

**Program** (`practical_03_pyramids.py`)

```python
# Practical 3: WAP to create a pyramid of the character '*' and a reverse pyramid


def pyramid(rows):
    """Print a pyramid with the given number of rows (1, 3, 5, ... stars)."""
    for i in range(1, rows + 1):
        print(" " * (rows - i) + "*" * (2 * i - 1))


def reverse_pyramid(rows):
    """Print a reverse (inverted) pyramid with the given number of rows."""
    for i in range(rows, 0, -1):
        print(" " * (rows - i) + "*" * (2 * i - 1))


rows = int(input("Enter the number of rows: "))

print("\nPyramid:")
pyramid(rows)

print("\nReverse pyramid:")
reverse_pyramid(rows)
```

**Output**

```text






```

---

## Practical 4: Character Check

**Question:** WAP that accepts a character and performs the following:

- a. print whether the character is a letter or numeric digit or a special character
- b. if the character is a letter, print whether the letter is uppercase or lowercase
- c. if the character is a numeric digit, prints its name in text (e.g., if input is 9, output is NINE)

**Program** (`practical_04_character_check.py`)

```python
# Practical 4: WAP that accepts a character and performs the following:
#   a. print whether the character is a letter or numeric digit or a special character
#   b. if the character is a letter, print whether the letter is uppercase or lowercase
#   c. if the character is a numeric digit, print its name in text (e.g. 9 -> NINE)

DIGIT_NAMES = {
    '0': "ZERO", '1': "ONE", '2': "TWO", '3': "THREE", '4': "FOUR",
    '5': "FIVE", '6': "SIX", '7': "SEVEN", '8': "EIGHT", '9': "NINE",
}

ch = input("Enter a single character: ")

if len(ch) != 1:
    print("Please enter exactly one character.")
elif ch.isalpha():
    print(f"'{ch}' is a letter")
    if ch.isupper():
        print("It is an uppercase letter")
    else:
        print("It is a lowercase letter")
elif ch.isdigit():
    print(f"'{ch}' is a numeric digit")
    print("Name in text:", DIGIT_NAMES.get(ch, "(not a decimal digit 0-9)"))
else:
    print(f"'{ch}' is a special character")
```

**Output**

```text






```

---

## Practical 5: Operations on a String

**Question:** WAP to perform the following operations on a string:

- a. Find the frequency of a character in a string.
- b. Replace a character by another character in a string.
- c. Remove the first occurrence of a character from a string.
- d. Remove all occurrences of a character from a string.

**Program** (`practical_05_string_operations.py`)

```python
# Practical 5: WAP to perform the following operations on a string
#   a. Find the frequency of a character in a string
#   b. Replace a character by another character in a string
#   c. Remove the first occurrence of a character from a string
#   d. Remove all occurrences of a character from a string


def frequency(s, ch):
    count = 0
    for c in s:
        if c == ch:
            count += 1
    return count


def replace_char(s, old, new):
    result = ""
    for c in s:
        result += new if c == old else c
    return result


def remove_first(s, ch):
    index = s.find(ch)
    if index == -1:
        return s
    return s[:index] + s[index + 1:]


def remove_all(s, ch):
    result = ""
    for c in s:
        if c != ch:
            result += c
    return result


text = input("Enter a string: ")

ch = input("a) Enter a character to find its frequency: ")[:1]
print(f"   '{ch}' occurs {frequency(text, ch)} time(s)")

old = input("b) Enter the character to be replaced: ")[:1]
new = input("   Enter the new character: ")[:1]
print("   Result:", replace_char(text, old, new))

ch = input("c) Enter a character to remove its first occurrence: ")[:1]
print("   Result:", remove_first(text, ch))

ch = input("d) Enter a character to remove all its occurrences: ")[:1]
print("   Result:", remove_all(text, ch))
```

**Output**

```text






```

---

## Practical 6: Swap First n Characters of Two Strings

**Question:** WAP to swap the first n characters of two strings.

**Program** (`practical_06_swap_characters.py`)

```python
# Practical 6: WAP to swap the first n characters of two strings


def swap_first_n(s1, s2, n):
    """Return (s1', s2') after exchanging the first n characters."""
    return s2[:n] + s1[n:], s1[:n] + s2[n:]


str1 = input("Enter the first string: ")
str2 = input("Enter the second string: ")
n = int(input("Enter n (number of characters to swap): "))

if n < 0 or n > len(str1) or n > len(str2):
    print("n must be between 0 and the length of the shorter string.")
else:
    new1, new2 = swap_first_n(str1, str2, n)
    print("Before swapping:", str1, "|", str2)
    print("After swapping :", new1, "|", new2)
```

**Output**

```text






```

---

## Practical 7: Indices of a Substring

**Question:** Write a function that accepts two strings and returns the indices of all the occurrences of the second string in the first string as a list. If the second string is not present in the first string then it should return -1.

**Program** (`practical_07_find_substring_indices.py`)

```python
# Practical 7: Write a function that accepts two strings and returns the indices of
# all the occurrences of the second string in the first string as a list.
# If the second string is not present in the first string then it should return -1.


def find_all(first, second):
    indices = []
    start = first.find(second)
    while start != -1:
        indices.append(start)
        start = first.find(second, start + 1)   # +1 also finds overlapping matches
    return indices if indices else -1


s1 = input("Enter the first string: ")
s2 = input("Enter the second string: ")

if s2 == "":
    print("The second string must not be empty.")
else:
    print("Result:", find_all(s1, s2))
```

**Output**

```text






```

---

## Practical 8: Cubes of Even Integers

**Question:** WAP to create a list of the cubes of only the even integers appearing in the input list (may have elements of other types also) using the following:

- a. 'for' loop
- b. list comprehension

**Program** (`practical_08_cubes_of_even.py`)

```python
# Practical 8: WAP to create a list of the cubes of only the even integers appearing
# in the input list (may have elements of other types also) using:
#   a. 'for' loop
#   b. list comprehension

# The input list is mixed on purpose: ints, floats, strings, bool and None.
data = [1, 2, 3, 4, "hello", 6, 7.0, 8, 9, 10, True, None, "12", 14, -2]
print("Input list:", data)


def is_integer(x):
    # bool is a subclass of int in Python, so it is excluded explicitly
    return isinstance(x, int) and not isinstance(x, bool)


# a. using a for loop
cubes_loop = []
for item in data:
    if is_integer(item) and item % 2 == 0:
        cubes_loop.append(item ** 3)
print("a) Using for loop          :", cubes_loop)

# b. using list comprehension
cubes_comp = [x ** 3 for x in data if is_integer(x) and x % 2 == 0]
print("b) Using list comprehension:", cubes_comp)
```

**Output**

```text






```

---

## Practical 9: File Handling

**Question:** WAP to read a file and

- a. Print the total number of characters, words and lines in the file.
- b. Calculate the frequency of each character in the file. Use a variable of dictionary type to maintain the count.
- c. Print the words in reverse order.
- d. Copy even lines of the file to a file named 'File1' and odd lines to another file named 'File2'.

**Program** (`practical_09_file_handling.py`)

```python
# Practical 9: WAP to read a file and
#   a. Print the total number of characters, words and lines in the file.
#   b. Calculate the frequency of each character in the file. Use a variable of
#      dictionary type to maintain the count.
#   c. Print the words in reverse order.
#   d. Copy even lines of the file to a file named 'File1' and odd lines to another
#      file named 'File2'.
import os

filename = input("Enter the file name (press Enter to use sample.txt): ").strip() or "sample.txt"

# Create a sample file if the default one does not exist yet
if filename == "sample.txt" and not os.path.exists(filename):
    with open(filename, "w") as f:
        f.write("Python is a popular programming language.\n"
                "It is easy to learn and read.\n"
                "File handling is an important topic.\n"
                "This is the fourth line of the file.\n"
                "And this is the last line.\n")
    print("(sample.txt created)")

try:
    with open(filename, "r") as f:
        lines = f.readlines()
except FileNotFoundError:
    print("File not found:", filename)
    raise SystemExit

content = "".join(lines)

# a. characters, words, lines
print("\na) Total characters:", len(content))
print("   Total words     :", len(content.split()))
print("   Total lines     :", len(lines))

# b. frequency of each character (dictionary)
freq = {}
for ch in content:
    freq[ch] = freq.get(ch, 0) + 1
print("\nb) Frequency of each character:")
for ch, count in sorted(freq.items()):
    print(f"   {repr(ch):6} -> {count}")

# c. words in reverse order
print("\nc) Words in reverse order:")
print("  ", " ".join(content.split()[::-1]))

# d. even lines -> File1, odd lines -> File2  (line numbers start from 1)
with open("File1", "w") as f1, open("File2", "w") as f2:
    for number, line in enumerate(lines, start=1):
        if number % 2 == 0:
            f1.write(line if line.endswith("\n") else line + "\n")
        else:
            f2.write(line if line.endswith("\n") else line + "\n")
print("\nd) Even lines copied to 'File1' and odd lines copied to 'File2'.")
```

**Output**

```text






```

---

## Practical 10: Class Point

**Question:** WAP to define a class Point with coordinates x and y as attributes. Create relevant methods and print the objects. Also define a method distance to calculate the distance between any two point objects.

**Program** (`practical_10_point_class.py`)

```python
# Practical 10: WAP to define a class Point with coordinates x and y as attributes.
# Create relevant methods and print the objects. Also define a method distance to
# calculate the distance between any two point objects.
import math


class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y

    def __str__(self):
        return f"Point({self.x}, {self.y})"

    def distance(self, other):
        """Distance between this point and another Point object."""
        return math.sqrt((self.x - other.x) ** 2 + (self.y - other.y) ** 2)

    def move(self, dx, dy):
        """Shift the point by (dx, dy)."""
        self.x += dx
        self.y += dy

    def midpoint(self, other):
        return Point((self.x + other.x) / 2, (self.y + other.y) / 2)


p1 = Point(1, 2)
p2 = Point(4, 6)
print("p1 =", p1)
print("p2 =", p2)
print("Distance between p1 and p2 =", p1.distance(p2))
print("Midpoint of p1 and p2 =", p1.midpoint(p2))

p1.move(2, 3)
print("After moving p1 by (2, 3): p1 =", p1)

# Points entered by the user
x1, y1 = map(float, input("\nEnter x and y of the first point: ").split())
x2, y2 = map(float, input("Enter x and y of the second point: ").split())
a, b = Point(x1, y1), Point(x2, y2)
print(a, "and", b)
print("Distance =", round(a.distance(b), 4))
```

**Output**

```text






```

---

## Practical 11: Dictionary of Cubes

**Question:** Write a function that prints a dictionary where the keys are numbers between 1 and 5 and the values are cubes of the keys.

**Program** (`practical_11_dictionary_cubes.py`)

```python
# Practical 11: Write a function that prints a dictionary where the keys are numbers
# between 1 and 5 and the values are cubes of the keys.


def print_cubes_dict():
    cubes = {}
    for n in range(1, 6):
        cubes[n] = n ** 3
    print(cubes)
    return cubes


print_cubes_dict()
```

**Output**

```text






```

---

## Practical 12: Tuple Operations

**Question:** Consider a tuple t1 = (1, 2, 5, 7, 9, 2, 4, 6, 8, 10). WAP to perform following operations:

- a) Print half the values of the tuple in one line and the other half in the next line
- b) Print another tuple whose values are even numbers in the given tuple
- c) Concatenate a tuple t2 = (11, 13, 15) with t1
- d) Return maximum and minimum value from this tuple

**Program** (`practical_12_tuples.py`)

```python
# Practical 12: Consider a tuple t1 = (1, 2, 5, 7, 9, 2, 4, 6, 8, 10).
# WAP to perform following operations:
#   a) Print half the values of the tuple in one line and the other half in the next line
#   b) Print another tuple whose values are even numbers in the given tuple
#   c) Concatenate a tuple t2 = (11, 13, 15) with t1
#   d) Return maximum and minimum value from this tuple

t1 = (1, 2, 5, 7, 9, 2, 4, 6, 8, 10)
print("t1 =", t1)

# a) first half on one line, second half on the next
mid = len(t1) // 2
print("\na) First half :", *t1[:mid])
print("   Second half:", *t1[mid:])

# b) tuple of even numbers
evens = tuple(x for x in t1 if x % 2 == 0)
print("\nb) Even numbers tuple:", evens)

# c) concatenation with t2
t2 = (11, 13, 15)
t3 = t2 + t1
print("\nc) t2 + t1 =", t3)


# d) maximum and minimum
def max_min(t):
    return max(t), min(t)


maximum, minimum = max_min(t1)
print("\nd) Maximum value:", maximum)
print("   Minimum value:", minimum)
```

**Output**

```text






```

---

## Practical 13: Exception Handling

**Question:** WAP to accept a name from a user. Raise and handle appropriate exception(s) if the text entered by the user contains digits and/or special characters.

**Program** (`practical_13_exception_handling.py`)

```python
# Practical 13: WAP to accept a name from a user. Raise and handle appropriate
# exception(s) if the text entered by the user contains digits and/or special characters.


class InvalidNameError(Exception):
    """Raised when the name has digits or special characters."""
    pass


def validate_name(name):
    if name.strip() == "":
        raise ValueError("Name cannot be empty.")
    has_digit = any(ch.isdigit() for ch in name)
    has_special = any(not (ch.isalpha() or ch.isspace()) and not ch.isdigit() for ch in name)
    if has_digit and has_special:
        raise InvalidNameError("Name contains digits and special characters.")
    if has_digit:
        raise InvalidNameError("Name contains digits.")
    if has_special:
        raise InvalidNameError("Name contains special characters.")
    return name


while True:
    user_name = input("Enter your name: ")
    try:
        validate_name(user_name)
    except InvalidNameError as e:
        print("Invalid name ->", e, "Please try again.\n")
    except ValueError as e:
        print("Error ->", e, "Please try again.\n")
    else:
        print("Hello,", user_name.strip() + "! Your name is valid.")
        break
    finally:
        print("(validation finished)")
```

**Output**

```text






```

---

<p align="center"><i>Shivam Pal · Roll No. 26570055 · B.Sc. (Hons.) Computer Science, Semester I · Ramanujan College, University of Delhi</i></p>
