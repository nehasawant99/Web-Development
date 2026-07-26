# Pseudocode Practice & Mistakes

---

# Question 1 - Positive or Negative Number

## My Attempt

```text
START

INPUT num

IF num is positive
    PRINT "Positive"
ELSE
    PRINT "Negative"
ENDIF

END
```

## Mistake

- Didn't handle the case when the number is 0.
- Used "is positive" instead of a comparison operator.

## Correct Code

```text
START

INPUT num

IF num > 0 THEN
    PRINT "Positive"
ELSE IF num < 0 THEN
    PRINT "Negative"
ELSE
    PRINT "Zero"
ENDIF

END
```

## Learning

- Use comparison operators (`>`, `<`).
- Always think about edge cases like `0`.

---

# Question 2 - Print Numbers 1 to 100

## My Attempt

```text
START

FOR i = 1 TO 100
    PRINT i
ENDFOR

END
```

---

# Question 3 - Largest of Three Numbers

## My Attempt

```text
START

INPUT n1
INPUT n2
INPUT n3

IF n1 > n2 > n3
    PRINT larger number
ELSE
    PRINT not found
ENDIF

END
```

## Mistake

- A computer cannot compare three values together.
- "Not Found" is not a valid output here.

## Correct Code

```text
START

INPUT n1
INPUT n2
INPUT n3

IF n1 > n2 AND n1 > n3 THEN
    PRINT n1
ELSE IF n2 > n1 AND n2 > n3 THEN
    PRINT n2
ELSE
    PRINT n3
ENDIF

END
```

## Learning

Compare only two values at a time.

Wrong

```text
n1 > n2 > n3
```

Correct

```text
n1 > n2 AND n1 > n3
```

---

# Question 4 - Vowel or Consonant

## My Attempt

```text
START

INPUT alphabets

IF check vowels [a,e,i,o,u,s]
    PRINT vowels
ELSE
    PRINT alphabets
ENDIF

END
```

## Mistake

- `s` is not a vowel.
- Didn't compare the input with each vowel.
- "Alphabet" is not the correct output.

## Correct Code

```text
START

INPUT alphabet

IF alphabet = 'a' OR alphabet = 'e' OR alphabet = 'i' OR alphabet = 'o' OR alphabet = 'u' THEN
    PRINT "Vowel"
ELSE
    PRINT "Consonant"
ENDIF

END
```

## Learning

Use OR when checking multiple possible values.

---

# Question 5 - Search Number in List

## My Attempt

```text
START

INPUT searchNum

IF no_list > searchNum
    PRINT num
ELSE
    PRINT not found
ENDIF

END
```

## Mistake

- Used `>` instead of checking equality.
- Didn't iterate through the list.

## Correct Code

```text
START

INPUT searchNum

FOR each num IN numberList

    IF num = searchNum THEN
        PRINT "Number Found"
        END
    ENDIF

ENDFOR

PRINT "Number Not Found"

END
```

## Learning

Searching means comparing values using `=`.

Wrong

```text
num > searchNum
```

Correct

```text
num = searchNum
```

---

# Common Mistakes I Made

| Mistake | Correct Approach |
|---------|------------------|
| Forgot loop ending | Use ENDFOR or ENDWHILE |
| Compared three values together | Compare two values using AND |
| Didn't think about edge cases | Check for 0 or other special cases |
| Used `>` while searching | Searching uses `=` |
| Didn't compare each vowel | Use OR for multiple comparisons |
| Wrong output message | Print meaningful results like "Consonant" or the largest number |

---

# Key Learning

- Think about the logic before writing code.
- Compare only two values at a time.
- Every IF needs ENDIF.
- Every FOR needs ENDFOR.
- Every WHILE needs ENDWHILE.
- Use `AND` when all conditions must be true.
- Use `OR` when any one condition can be true.
- Searching uses `=`, not `>`.
- Always consider edge cases before finishing the solution.
