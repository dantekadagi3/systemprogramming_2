Sure! Let's break down the code step by step:

```c
#include <stdio.h>
```
This line includes the standard input-output header file, which is necessary for using functions like `printf`, `scanf`, `fopen`, `fgets`, and `fprintf`.

```c
int main() {
```
This is the main function where the program execution starts.

```c
    FILE *fptr;
```
This declares a pointer to a `FILE` type, which will be used to refer to the file we want to work with.

```c
    char filename[100], str[100];
```
These lines declare two character arrays (`filename` and `str`), each capable of holding up to 100 characters. `filename` will store the name of the file, and `str` will store the string to be appended to the file.

```c
    printf("Enter the filename: ");
    scanf("%s", filename);
```
These lines prompt the user to enter the name of the file and then read the input into the `filename` array.

```c
    fptr = fopen(filename, "a");
```
This line attempts to open the file specified by `filename` in "append" mode. In this mode, data will be written at the end of the file without truncating it.

```c
    if (fptr == NULL) {
        printf("Cannot open file \n");
        return 1;
    }
```
If the file cannot be opened (for example, if it doesn't exist or there are permission issues), `fopen` returns `NULL`. This `if` statement checks if `fptr` is `NULL` and, if so, prints an error message and returns 1 to indicate that the program ended with an error.

```c
    printf("Enter a string to append to the file: ");
    getchar(); // consume newline left by scanf
```
This line prompts the user to enter a string to append to the file. `getchar()` is used to consume the newline character left in the input buffer by the previous `scanf` call. This ensures that the subsequent `fgets` call works correctly.

```c
    fgets(str, 100, stdin);
```
This line reads a line of text from the standard input (`stdin`) into the `str` array. It reads up to 99 characters or until a newline character is encountered, whichever comes first.

```c
    fprintf(fptr, "%s", str);
```
This line writes the contents of `str` to the file referred to by `fptr`.

```c
    fclose(fptr);
```
This line closes the file. It's important to close files to free up resources and ensure that all data is properly written to the file.

```c
    printf("Content appended to the file.\n");
```
This line prints a confirmation message to the user indicating that the content has been successfully appended to the file.

```c
    return 0;
}
```
This line indicates that the program ended successfully by returning 0.