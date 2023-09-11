include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <string.h>
void swap(char *a, char *b) 
{
char temp = *a;
*a = *b;
*b = temp;
}
void reverse(char *str, int start, int end) 
{
while (start < end) 
{
swap(&str[start], &str[end]);
start++;
end--;
}
}
bool find_next_permutation(char *str) 
{
int len = strlen(str);
int i = len - 2;
while (i >= 0 && str[i] >= str[i + 1]) 
{
i--;
}
if (i >= 0) 
{
int j = len - 1;
while (str[j] <= str[i]) 
{
j--;
}
swap(&str[i], &str[j]);
reverse(str, i + 1, len - 1);
return true;
}
return false;
}
int find_next_number_with_same_digits(int number) 
{
char str[15];
sprintf(str, "%d", number);
if (find_next_permutation(str)) 
{
int next_number = atoi(str);
return next_number;
}
return -1; 
}
int main() 
{
int input_number;
printf("Enter a number: ");
scanf("%d", &input_number);
int next_number = find_next_number_with_same_digits(input_number);
if (next_number == -1) 
{
printf("No greater number with the same set of digits found.\n");
}
else 
{
printf("The next greater number with the same set of digits: %d\n", next_number);
}
return 0;
}
