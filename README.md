AIM:
To encrypt and decrypt the given message by using Ceaser Cipher encryption algorithm.

DESIGN STEPS:
Step 1:
Design of Caeser Cipher algorithnm

Step 2:
Implementation using C or pyhton code

Step 3:
Testing algorithm with different key values.

ALGORITHM DESCRIPTION:
The Playfair cipher uses a 5 by 5 table containing a key word or phrase. To generate the key table, first fill the spaces in the table with the letters of the keyword, then fill the remaining spaces with the rest of the letters of the alphabet in order (usually omitting "Q" to reduce the alphabet to fit; other versions put both "I" and "J" in the same space). The key can be written in the top rows of the table, from left to right, or in some other pattern, such as a spiral beginning in the upper-left-hand corner and ending in the centre. The keyword together with the conventions for filling in the 5 by 5 table constitutes the cipher key. To encrypt a message, one would break the message into digrams (groups of 2 letters) such that, for example, "HelloWorld" becomes "HE LL OW OR LD", and map them out on the key table. Then apply the following 4 rules, to each pair of letters in the plaintext:

If both letters are the same (or only one letter is left), add an "X" after the first letter. Encrypt the new pair and continue. Some
variants of Playfair use "Q" instead of "X", but any letter, itself uncommon as a repeated pair, will do.
If the letters appear on the same row of your table, replace them with the letters to their immediate right respectively (wrapping around to the left side of the row if a letter in the original pair was on the right side of the row).
If the letters appear on the same column of your table, replace them with the letters immediately below respectively (wrapping around to the top side of the column if a letter in the original pair was on the bottom side of the column).
If the letters are not on the same row or column, replace them with the letters on the same row respectively but at the other pair of corners of the rectangle defined by the original pair. The order is important – the first letter of the encrypted pair is the one that lies on the same row as the first letter of the plaintext pair. To decrypt, use the INVERSE (opposite) of the last 3 rules, and the 1st as-is (dropping any extra "X"s, or "Q"s that do not make sense in the final message when finished).

PROGRAM:
#include <stdio.h>
#include <string.h>

void encrypt(char message[], int shift) {
    char ch;
    for (int i = 0; message[i] != '\0'; ++i) {
        ch = message[i];
        if (ch >= 'a' && ch <= 'z') {
            ch = ch + shift;
            if (ch > 'z') {
                ch = ch - 'z' + 'a' - 1;
            }
            message[i] = ch;
        } else if (ch >= 'A' && ch <= 'Z') {
            ch = ch + shift;
            if (ch > 'Z') {
                ch = ch - 'Z' + 'A' - 1;
            }
            message[i] = ch;
        }
    }
    printf("Encrypted message: %s\n", message);
}

void decrypt(char message[], int shift) {
    char ch;
    for (int i = 0; message[i] != '\0'; ++i) {
        ch = message[i];
        if (ch >= 'a' && ch <= 'z') {
            ch = ch - shift;
            if (ch < 'a') {
                ch = ch + 'z' - 'a' + 1;
            }
            message[i] = ch;
        } else if (ch >= 'A' && ch <= 'Z') {
            ch = ch - shift;
            if (ch < 'A') {
                ch = ch + 'Z' - 'A' + 1;
            }
            message[i] = ch;
        }
    }
    printf("Decrypted message: %s\n", message);
}

int main() {
    char message[100];
    int shift;

    printf("Enter a message: ");
    gets(message);  // reads a line of text

    printf("Enter shift amount: ");
    scanf("%d", &shift);

    // Make a copy of the message to decrypt later
    char encrypted_message[100];
    strcpy(encrypted_message, message);

    encrypt(encrypted_message, shift);
    decrypt(encrypted_message, shift);

    return 0;
}


OUTPUT:
'''
<img width="379" alt="Screenshot 2024-10-21 at 10 39 15 AM" src="https://github.com/user-attachments/assets/ff51c1af-8be8-4a7e-8831-d19eff8ba8ba">
'''

RESULT:
The program is executed successfully
