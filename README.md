## EX. NO: 1(A) : IMPLEMENTATION OF CAESAR CIPHER
 

## AIM:

To implement the simple substitution technique named Caesar cipher using C language.

## DESCRIPTION:

To encrypt a message with a Caesar cipher, each letter in the message is changed using a simple rule: shift by three. Each letter is replaced by the letter three letters ahead in the alphabet. A becomes D, B becomes E, and so on. For the last letters, we can think of the
alphabet as a circle and "wrap around". W becomes Z, X becomes A, Y bec mes B, and Z
becomes C. To change a message back, each letter is replaced by the one three before it.

## EXAMPLE:



![image](https://github.com/Hemamanigandan/CNS/assets/149653568/eb9c6c43-8c80-4cdd-b9d4-91705a311c79)


## ALGORITHM:

### STEP-1: Read the plain text from the user.
### STEP-2: Read the key value from the user.
### STEP-3: If the key is positive then encrypt the text by adding the key with each character in the plain text.
### STEP-4: Else subtract the key from the plain text.
### STEP-5: Display the cipher text obtained above.


PROGRAM :-
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char plain[11], cipher[11];  // Increased size to accommodate null terminator
    int key, i, length;

    printf("\n Enter the plain text (max 10 chars): ");
    scanf("%10s", plain);  // Limits input to 10 characters

    printf("\n Enter the key value: ");
    scanf("%d", &key);

    length = strlen(plain);

    printf("\n \n \t PLAIN TEXT: %s", plain);
    printf("\n \n \t ENCRYPTED TEXT: ");

    for (i = 0; i < length; i++) {
        cipher[i] = plain[i] + key;

        // Handle wrap-around for uppercase letters
        if (isupper(plain[i]) && (cipher[i] > 'Z')) {
            cipher[i] -= 26;
        }
        // Handle wrap-around for lowercase letters
        if (islower(plain[i]) && (cipher[i] > 'z')) {
            cipher[i] -= 26;
        }

        printf("%c", cipher[i]);
    }
    cipher[length] = '\0';  // Null-terminate cipher text

    printf("\n \n \t AFTER DECRYPTION: ");
    for (i = 0; i < length; i++) {
        plain[i] = cipher[i] - key;

        // Handle wrap-around for uppercase letters
        if (isupper(cipher[i]) && (plain[i] < 'A')) {
            plain[i] += 26;
        }
        // Handle wrap-around for lowercase letters
        if (islower(cipher[i]) && (plain[i] < 'a')) {
            plain[i] += 26;
        }

        printf("%c", plain[i]);
    }
    plain[length] = '\0';  // Null-terminate plain text

    printf("\n");

    return 0;
}
```



OUTPUT :-

![image](https://github.com/user-attachments/assets/bc7bce65-d5a0-435c-a49a-d7c9fcb49c65)

