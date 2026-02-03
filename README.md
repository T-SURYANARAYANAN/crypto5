# Ex-4 Rail-Fence-Program

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
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void encryptRailFence(char *message, int rails) {
    int len = strlen(message);

    char rail[rails][len];

    // Fill with newline as placeholder
    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            rail[i][j] = '\n';

    int row = 0;
    int direction = 1;

    for (int i = 0; i < len; i++) {
        rail[row][i] = message[i];

        // Move up or down
        row += direction;

        // Change direction at top or bottom
        if (row == rails - 1 || row == 0)
            direction = -direction;
    }

    printf("Encrypted text: ");
    for (int i = 0; i < rails; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);

    printf("\n");
}

int main() {
    char message[100];
    int rails;

    printf("Enter a Secret Message: ");
    scanf(" %[^\n]", message);   // allows spaces

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    encryptRailFence(message, rails);

    return 0;
}

```
# OUTPUT
<img width="1919" height="924" alt="image" src="https://github.com/user-attachments/assets/7abe5ec6-2f5d-43c1-b5ce-963f18660480" />

# RESULT
C program to implement the rail fence transposition technique is executed successfully
