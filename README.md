# Lab-3
EXERCISE 1
#include <stdio.h>

int main(void) {
    long num, sum = 0L;
    int status;
    printf("Please enter integers to be summed, ending with a non-integer (q to quit): ");
    while (scanf("%ld", &num) == 1) {  
        sum += num;
        printf("Please enter next integer (q to quit): ");
    }
    printf("Those integers sum to %ld.\n", sum);
    return 0;
}

EXERCISE 2
#include <stdio.h>

int main(void) {
    int n;
    long long factorial = 1;
 printf("Enter a positive integer: ")
    scanf("%d", &n);
    if (n < 0) {
        printf("Factorial is not defined for negative numbers.\n");
        return 1;
    }
for (int i = 1; i <= n; i++) {
        factorial *= i;  
    }

printf("Factorial of %d is %lld.\n", n, factorial);
    return 0;
}

EXERCISE 3
#include <stdio.h>

int main(void) {
    int pin = 1234, input, attempts = 0;

 while (attempts < 5) {
        printf("Enter PIN: ");
        scanf("%d", &input);

 if (input == pin) {
            printf("Access granted.\n");
            return 0; 
        } else {
            printf("Incorrect PIN. Try again.\n");
            attempts++;
        }
    }

printf("Too many incorrect attempts. Access locked.\n");
    return 0;
}

EXERCISE 4
#include <stdio.h>

int main(void) {
    for (int i = 1; i <= 10; i++) {
        for (int j = 1; j <= 10; j++) {
            printf("%4d", i * j);
        }
        printf("\n");
    }
    return 0;
}


EXERCISE 5
#include <stdio.h>

#define MAX_SIZE 20

float mean(int arr[], int n);
int mode(int arr[], int n);
float median(int arr[], int n);
void sort(int arr[], int n);

int main(void) {
    int numbers[MAX_SIZE], n;

printf("Enter number of elements (max 20): ");
    scanf("%d", &n);

printf("Enter the numbers (ascending order):\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &numbers[i]);
    }

printf("Mean: %.2f\n", mean(numbers, n)); 
printf("Mode: %d\n", mode(numbers, n));
printf("Median: %.2f\n", median(numbers, n));

  return 0;
}

float mean(int arr[], int n) {
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += arr[i];
    }
    return (float)sum / n;
}

int mode(int arr[], int n) {
    int maxCount = 0, mode = arr[0], count;
    for (int i = 0; i < n; i++) {
        count = 0;
        for (int j = 0; j < n; j++) {
            if (arr[j] == arr[i]) {
                count++;
            }
        }
        if (count > maxCount) {
            maxCount = count;
            mode = arr[i];
        }
    }
    return mode;
}

float median(int arr[], int n) {
    sort(arr, n);
    if (n % 2 == 0) {
        return (arr[n / 2 - 1] + arr[n / 2]) / 2.0;
    } else {
        return arr[n / 2];
    }
}

void sort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[i] > arr[j]) {
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
    }
}


EXERCISE 6
#include <stdio.h>

int main(void) {
    float income, tax = 0;

printf("Enter your income: ");
    scanf("%f", &income);

if (income <= 10000) {
        tax = income * 0.18;
    } else if (income <= 18000) {
        tax = 10000 * 0.18 + (income - 10000) * 0.20;
    } else {
        tax = 10000 * 0.18 + 8000 * 0.20 + (income - 18000) * 0.25;
    }

char industry;
    printf("Are you in the ICT industry? (y/n): ");
    scanf(" %c", &industry);  
    if (industry == 'y') {
        tax *= 0.95; 
    }

char recycling;
    printf("Do you collect old electronic equipment for disposal? (y/n): ");
    scanf(" %c", &recycling);  
    if (recycling == 'y') {
        tax -= 10000 * 0.18;  
    }

   printf("Your total tax is: %.2f\n", tax);
    return 0;
}


EXERCISE 7
#include <stdio.h>
#include <ctype.h>
#include <string.h>

#define MAX_WORD_LENGTH 100

int is_valid_word(char *word) {
    int length = strlen(word);
    if (isupper(word[0])) {
        for (int i = 1; i < length; i++) {
            if (isupper(word[i])) {
                return 0; 
            }
        }
    }
    if (length > 10 && !strchr(word, '-')) {
        return 0; 
    }
    if (!isalpha(word[0])) {
        return 0; 
    }
    return 1; 
}

int main(void) {
    char word[MAX_WORD_LENGTH];
    int error_count = 0;
    printf("Enter words (type 'exit' to quit):\n");
while (1) {
        int i = 0
        int ch;
        while ((ch = getchar()) != EOF && !isspace(ch) && ch != '\n' && ch != '\t') {
            word[i++] = ch;
        }
        word[i] = '\0'; 
if (strcmp(word, "exit") == 0) {
            break; // Exit the loop if 'exit' is typed
        }
        if (!is_valid_word(word)) {
            printf("Warning: Invalid word \"%s\"\n", word);
            error_count++;
        }
    }
if (error_count == 0) {
        printf("No errors found.\n");
    } else if (error_count == 1) {
        printf("1 error found.\n");
    } else {
        printf("%d errors found.\n", error_count);
    }
return 0;
}


EXERCISE 8
#include <stdio.h>
#include <ctype.h>
#include <string.h>

#define MAX_WORD_LENGTH 100

int is_valid_word(char *word) {
    int length = strlen(word);
    if (isupper(word[0])) {
        for (int i = 1; i < length; i++) {
            if (isupper(word[i])) {
                return 0; 
            }
        }
    }
    if (length > 10 && !strchr(word, '-')) {
        return 0; 
    }
    if (!isalpha(word[0])) {
        return 0;
    }
    return 1; 
}

int is_punctuation_preceded_by_space(char *word) {
    for (int i = 0; i < strlen(word); i++) {
        if (isspace(word[i]) && ispunct(word[i + 1])) {
            return 1; 
        }
    }
    return 0; 
}

int has_repeated_spaces(char *word) {
    for (int i = 0; i < strlen(word) - 1; i++) {
        if (isspace(word[i]) && isspace(word[i + 1])) {
            return 1; 
        }
    }
    return 0;
}

int main(void) {
    char word[MAX_WORD_LENGTH];
    int error_count = 0;
printf("Enter words (type 'exit' to quit):\n");

  while (1) {
        int i = 0;
        int ch;
        while ((ch = getchar()) != EOF && !isspace(ch) && ch != '\n' && ch != '\t') {
            word[i++] = ch;
        }
        word[i] = '\0'; 

  if (strcmp(word, "exit") == 0) {
            break; 
        }
        if (!is_valid_word(word)) {
            printf("Warning: Invalid word \"%s\"\n", word);
            error_count++;
        }
        if (is_punctuation_preceded_by_space(word)) {
            printf("Warning: Punctuation preceded by space in \"%s\"\n", word);
            error_count++;
        }
        if (has_repeated_spaces(word)) {
            printf("Warning: Repeated spaces in \"%s\"\n", word);
            error_count++;
        }
    }

  if (error_count == 0) {
        printf("No errors found.\n");
    } else if (error_count == 1) {
        printf("1 error found.\n");
    } else {
        printf("%d errors found.\n", error_count);
    }

  return 0;
}


EXERCISE 9
#include <stdio.h>
#include <stdlib.h>

#define MAX_NUMBERS 100

int main(void) {
    FILE *input_file, *output_file;
    double numbers[MAX_NUMBERS];
    int count = 0;
input_file = fopen("input.txt", "r");
    if (input_file == NULL) {
        printf("Error opening input file.\n");
        return 1;
    }
    while (fscanf(input_file, "%lf", &numbers[count]) == 1 && count < MAX_NUMBERS) {
        count++;
    }

  fclose(input_file);
    output_file = fopen("output.txt", "w");
    if (output_file == NULL) {
        printf("Error opening output file.\n");
        return 1;
    }
    for (int i = 0; i < count; i++) {
        if (numbers[i] >= 1.0 && numbers[i] <= 100.0) {
            fprintf(output_file, "%.2lf\n", numbers[i]);
        }
    }
    fclose(output_file);
    printf("Numbers processed and written to output.txt.\n");
    return 0;
}



EXERCISE 10
#include <stdio.h>
#include <stdlib.h>

#define MAX_ITEMS 5

void print_menu() {
    printf("1. Add items to shopping cart\n");
    printf("2. Show current total\n");
    printf("3. Check out\n");
    printf("4. Cancel session\n");
    printf("q. Quit\n");
}

int main(void) {
    int choice;
    double cart_total = 0.0;
    double prices[MAX_ITEMS] = {10.99, 15.50, 23.75, 8.99, 12.30}; // Example item prices
    char items[MAX_ITEMS][20] = {"Item1", "Item2", "Item3", "Item4", "Item5"};
    int cart[MAX_ITEMS] = {0}; // Stores quantities of items added to the cart
    int session_active = 1;

   while (session_active) {
        print_menu();
        printf("Choose an option: ");
        scanf("%d", &choice);

  switch (choice) {
            case 1: {
                printf("Choose an item (1-5): ");
                int item_choice, quantity;
                scanf("%d", &item_choice);
                if (item_choice < 1 || item_choice > 5) {
                    printf("Invalid choice.\n");
                } else {
                    printf("Enter quantity: ");
                    scanf("%d", &quantity);
                    cart[item_choice - 1] += quantity;
                    cart_total += prices[item_choice - 1] * quantity;
                }
                break;
            }
            case 2:
                printf("Current total: %.2f\n", cart_total);
                break;
            case 3:
                printf("Itemized bill:\n");
                for (int i = 0; i < MAX_ITEMS; i++) {
                    if (cart[i] > 0) {
                        printf("%s - %d x %.2f = %.2f\n", items[i], cart[i], prices[i], cart[i] * prices[i]);
                    }
                }
                printf("Total: %.2f\n", cart_total);
                cart_total = 0.0;
                break;
            case 4:
                printf("Canceling session...\n");
                cart_total = 0.0; 
                break;
            case 'q':
                session_active = 0; 
                break;
            default:
                printf("Invalid choice.\n");
        }
    }
    printf("Goodbye!\n");
    return 0;
}

