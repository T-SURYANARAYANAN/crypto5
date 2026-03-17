# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.<br>
STEP-2: Arrange the plain text in row columnar matrix format.<br>
STEP-3: Now read the keyword depending on the number of columns of the plain text.<br>
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.<br>
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.<br>

# PROGRAM
```c
#include <stdio.h>
#include <string.h>

int main()
{
    char text[100], rail[10][100];
    int i, j, len, key;
    int row = 0, dir = 1;

    printf("Enter text: ");
    scanf("%s", text);

    printf("Enter key: ");
    scanf("%d", &key);

    len = strlen(text);

    // Initialize matrix
    for(i = 0; i < key; i++)
        for(j = 0; j < len; j++)
            rail[i][j] = '\n';

    // Fill zig-zag
    for(i = 0; i < len; i++)
    {
        rail[row][i] = text[i];

        if(row == 0)
            dir = 1;
        else if(row == key - 1)
            dir = -1;

        row += dir;
    }

    // Encryption
    printf("Encrypted Text: ");
    for(i = 0; i < key; i++)
    {
        for(j = 0; j < len; j++)
        {
            if(rail[i][j] != '\n')
                printf("%c", rail[i][j]);
        }
    }
    printf("\n");
    return 0;
}
```
# OUTPUT
<img width="534" height="262" alt="image" src="https://github.com/user-attachments/assets/21041caa-96ac-4da7-9578-e7d1c19cb27a" />

# RESULT
C program to implement the rail fence transposition technique is executed successfully
