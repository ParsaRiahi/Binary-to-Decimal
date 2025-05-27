# Binary-to-Decimal

#include <stdio.h>
#include <math.h>

int binaryTurner(int *array, int size)
{
    int sum = 0;
    for(int i = 0; i < size; i++)
    {        
        sum = sum + array[i] * pow(2, size - 1 - i);
    }
    return sum;
}

void numToArray(int *array, int size, int input)
{
    for(int i = size - 1; i >= 0; i--)
    {
        array[i] = input % 10;
        input /= 10;
    }
}

int binarySizeCalculator(int input)
{
    int size = 0;
    do 
    {
        input /= 10;
        size++;
    } while(input > 0);
    return size;
}

int main(void)
{
    int input;
    int decimal;
    int size;

    printf("Enter a binary number: ");
    scanf("%d", &input);

    size = binarySizeCalculator(input);

    // printf("Binary number: %d\n", input);
    // printf("Number of digits: %d\n", size);

    int array[size];

    numToArray(array, size, input);

    // printf("Seperated numbers:\n");
    // for(int i = 0; i < size; i++)
    // {
    //     printf("%d ", array[i]);
    // }
    // printf("\n");

    decimal = binaryTurner(array, size);

    printf("Result in decimal: %d\n", decimal);

    return 0;
}
