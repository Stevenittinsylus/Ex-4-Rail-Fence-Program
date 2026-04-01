
## Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.


STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main() {
    char text[100];
    int rails, i, j, k = 0;

    printf("Enter text: ");
    scanf("%s", text);

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    int len = strlen(text);
    char rail[rails][len];

    // Fill with '*'
    for(i = 0; i < rails; i++)
        for(j = 0; j < len; j++)
            rail[i][j] = '*';

    // Fill characters in zig-zag
    int row = 0, dir = 1;
    for(i = 0; i < len; i++) {
        rail[row][i] = text[i];

        if(row == 0) dir = 1;
        else if(row == rails - 1) dir = -1;

        row = row + dir;
    }

    // Print cipher text
    printf("Cipher Text: ");
    for(i = 0; i < rails; i++) {
        for(j = 0; j < len; j++) {
            if(rail[i][j] != '*')
                printf("%c", rail[i][j]);
        }
    }

    return 0;
}
```
# OUTPUT
<img width="405" height="173" alt="image" src="https://github.com/user-attachments/assets/ef2ea458-5a1b-4427-8804-ce03cb3e5706" />


# RESULT

The program is executed successfully
