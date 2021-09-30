---
title: "CS50 Week2"
description: "花了四個小時才做完的作業"
date: 2021-08-27T18:26:40+02:00
draft: false
image: "caesar.png"
---
## 紀錄CS50自學進度 🤯
2021年8月27日的下午，回台灣倒數一個月，Bayreuth越來越冷（14度C），窩在學校的總圖用了整個下午完成了 CS50 “Array" 的作業，滿滿的成就感 ++++++

附上偶寫的 code 在下面！耶！

```c++
#include <cs50.h>
#include <stdio.h>
#include <string.h>
#include <ctype.h>
#include <stdlib.h>

string rotate(string text, int key);

int main(int argc, string argv[])
{
    //call function that accepts single command-line arguement
    if (argc == 2)
    {

        for (int i = 0, len = strlen(argv[1]); i < len; i++)
        {
            if (isdigit(argv[1][i]))
            {
            }
            else
            {
                printf("Usage: ./caesar key\n");
                return 1;
            }
        }
    }
    else if (argc != 2)
    {
        printf("Usage: ./caesar key\n");
        return 1;
    }

    //output "plaintext: " without a new line and prompt user for a string (get_string)
    string plain = get_string("plaintext: ");
    
    //function: take plain text and key as inputs, rotate plain text by 'k' positions and return the cipher text
    string cipher = rotate(plain, atoi(argv[1]));
    
    //output "ciphertext: " without a new line
    printf("ciphertext: %s", cipher);

    //printf \n and exist by returning '0'
    printf("\n");
    return 0;
}

//write a function that take plain text and key as inputs, rotate plain text by 'k' positions and return the cipher text
string rotate(string text, int key)
{
    //iterate through the string, rotate 'k' to each element (character) of the string of array
    for (int i = 0, len = strlen(text); i < len; i++)
    {
        //if uppercase -> rotate by 'k', preserve uppercase, printf rotated element (character)
        if (isupper(text[i]))
        {
            text[i] = ((text[i] - 65) + key) % 26 + 65;
        }
        //if lowercase -> rotate by 'k', preserve lowercase, printf rotated element (character)
        if (islower(text[i]))
        {
            text[i] = ((text[i] - 97) + key) % 26 + 97;
        }
    }
   
    return text;
}
```