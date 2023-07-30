# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6

## List
- First item
- Second item
- Third item
- Fourth item
#### -----------------
* First item
* Second item
* Third item
* Fourth item
#### -----------------
+ First item
+ Second item
+ Third item
+ Fourth item
#### -----------------
- First item
- Second item
- Third item
    - Indented item
    - Indented item
- Fourth item

## Ordered list
1. First item
2. Second item
3. Third item
4. Fourth item
#### -----------------
1. First item
1. Second item
1. Third item
1. Fourth item
#### -----------------
1. First item
8. Second item
3. Third item
5. Fourth item
#### -----------------
1. First item
2. Second item
3. Third item
    1. Indented item
    2. Indented item
4. Fourth item


## Bold and *Italic*
Italicized text is the *cat's meow*.
**Italicized** text is the _cat's meow_.
A*cat*meow

## 
I just love **bold text**.
I just love __bold text__.
Love**is**bold

## Table 01
| Name       | Age | Occupation      |
|------------|-----|-----------------|
| John       | 30  | Software Engineer |
| Emily      | 25  | Graphic Designer |
| Michael    | 35  | Data Analyst     |
| Jessica    | 28  | Project Manager  |

## table 02
| Item                | Quantity | Price (USD) |
|---------------------|---------:|------------:|
| Laptop              |        2 |      1000   |
| Smartphone          |        3 |       500   |
| Headphones          |        5 |        50   |
| External Hard Drive |        1 |       150   |

## table 03
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |


## paragraph
This is the first `paragraph`. It contains some text to demonstrate how Markdown handles paragraphs. Each continuous block of text, separated by a blank line, is treated as a separate paragraph.

**This is the second paragraph. Markdown is a lightweight markup language that allows you to write simple and easy-to-read formatted text. It's widely used for creating documentation, `README` files, blogs, and more**.

*And this is the third paragraph*. Markdown provides various features such as headers, lists, code blocks, [links](https://www.devopseasylearning.com/), images, and more. It's a convenient and human-readable way to create formatted content without needing to deal with complex HTML or other markup languages.


## Block of code 
```
#!/bin/bash

# Simple bash script to calculate the factorial of a number

read -p "Enter a number: " number

if [[ $number -lt 0 ]]; then
    echo "Error: Factorial is not defined for negative numbers."
elif [[ $number -eq 0 ]]; then
    echo "Factorial of 0 is 1."
else
    factorial=1
    for (( i=1; i<=$number; i++ )); do
        factorial=$(( factorial * i ))
    done
    echo "Factorial of $number is $factorial."
fi
```

```sh
#!/bin/bash

# Simple bash script to calculate the factorial of a number

read -p "Enter a number: " number

if [[ $number -lt 0 ]]; then
    echo "Error: Factorial is not defined for negative numbers."
elif [[ $number -eq 0 ]]; then
    echo "Factorial of 0 is 1."
else
    factorial=1
    for (( i=1; i<=$number; i++ )); do
        factorial=$(( factorial * i ))
    done
    echo "Factorial of $number is $factorial."
fi

mkdir tia
groupadd hr 
usermod -aG hr tia
```