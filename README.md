# Radix-i-converter
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

#define TITLE "DECIMAL TO RADIX-i converter"
#define AUTHOR "Timika Buthuram"
#define YEAR "2022"

void Dec2RadixI(int decValue, int radValue){
    char s[1000000];    //used to store the string
    int j=0;    //pointer
    while(decValue > 0){
        int rem = decValue%radValue;    //remainder is created
        char insert;        //character is inserted

        if (rem < 10){
            insert = '0'+rem;}
        else {
            insert = 'A'+rem-10;}   //inserted into array

        s[j] = insert;
        j++;
        decValue = decValue/radValue;
    }
    printf(" value is ",radValue);

    for (int k = j;k >= 0;k--){      //reverse string
            printf("%c",s[k]);}

    printf("\n");
}

int main(){
    printf("*****************************\n");      //header is printed
    printf("%s\n", TITLE);
    printf("Written by: %s\n", AUTHOR);
    printf("Date: %s\n", YEAR);
    printf("*****************************\n");

    int decValue;   //stores decimal value entered by user
    int radValue;   //stores radix value entered by user

while(1){
    printf("Enter a decimal number: "); //prompts user to enter a decimal value
    scanf("%d", &decValue);

    if (decValue < 0){
        printf("EXIT\n");
        break;}     //program terminates if a decimal number smaller than 0 is entered

    if (decValue >= 0){
        printf("The number you have entered is %d \n", decValue);}  //prints decimal value if it is bigger than and including 0

    printf("Enter a radix for the converter between 2 and 16: ");    //prompts user to enter a radix value
    scanf("%d", &radValue);

    if (2 < radValue || radValue < 16){      //if the radix is bigger than 2 and smaller than 16, both included, then it will be used as radix value
        printf("The radix you have entered is %d \n", radValue);}

    printf("The log2 of the number is %.2lf\n",log2(decValue));
    //log2 of decimal value is printed
    printf("The integer result of the number divided by %d", radValue);
    printf(" is %d\n",decValue/radValue);
    //integer result of the decimal value divided by radix is printed
    printf("The remainder is %d\n",decValue%radValue);
    //remainder of the decimal value divided by radix is printed

    if (decValue == 0){
        printf("The radix-%d value is %d \n", radValue, 0);}
    else {
        printf("The radix-%d", radValue);
        Dec2RadixI(decValue, radValue);}
    }
return 0;
}
