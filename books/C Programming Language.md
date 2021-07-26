# C Programming Language

## Brian W. Kernighan and Dennis Ritchie

#books
#kindle

![](https://images-na.ssl-images-amazon.com/images/I/51cm0z-4qpL._SL2000_.jpg)

### Highlights from July 26, 2021

- If an arithmetic operator has integer operands, an integer operation is performed. If an arithmetic operator has one floating-point operand and one integer operand, however, the integer will be converted to floating point before the operation is done. If we had written fahr−32, the 32 would be automatically converted to floating point. Nevertheless, writing floating-point constants with explicit decimal points even when they have integral values emphasizes their floating-point nature for human readers. ([Location 535](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=535))
    - **Note:** Basically, just always use floats.
- The printf conversion specification %3.0f says that a floating-point number (here fahr) is to be printed at least three characters wide, with no decimal point and no fraction digits. %6.1f describes another number (celsius) that is to be printed at least six characters wide, with 1 digit after the decimal point. ([Location 547](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=547))
- %d print as decimal integer %6d print as decimal integer, at least 6 characters wide %f print as floating point %6f print as floating point, at least 6 characters wide %.2f print as floating point, 2 characters after decimal point %6.2f print as floating point, at least 6 wide and 2 after decimal point Among others, printf also recognizes %o for octal, %x for hexadecimal, %c for character, %s for character string, and %% for % itself. ([Location 560](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=560))
- symbolic constant to be a particular string of characters: #define  name  replacement text ([Location 610](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=610))
- Symbolic constant names are conventionally written in upper case so they can be readily distinguished from lower case variable names. ([Location 627](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=627))
- The model of input and output supported by the standard library is very simple. Text input or output, regardless of where it originates or where it goes to, is dealt with as streams of characters. ([Location 631](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=631))
- represents an integer value equal to the numerical value of the character in the machine’s character set. ([Location 768](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=768))
- “Definition” refers to the place where the variable is created or assigned storage; “declaration” refers to places where the nature of the variable is stated but no storage is allocated. ([Location 1187](https://readwise.io/to_kindle?action=open&asin=B009ZUZ9FW&location=1187))
