- 👋 Hi, I’m @Hrithik-tech333
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Hrithik-tech333/Hrithik-tech333 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#include <stdio.h>
#include <stdlib.h>

#define MAX 20

void create();
void insert();
void deletion();
void search();
void display();

int n = 0; // Number of elements in the list
int b[MAX]; // Array to hold the list elements

int main() {
    int ch;
    char g = 'y';

    do {
        printf("\nMain Menu");
        printf("\n1. Create");
        printf("\n2. Delete");
        printf("\n3. Search");
        printf("\n4. Insert");
        printf("\n5. Display");
        printf("\n6. Exit");
        printf("\nEnter your choice: ");
        scanf("%d", &ch);

        switch (ch) {
            case 1:
                create();
                break;
            case 2:
                deletion();
                break;
            case 3:
                search();
                break;
            case 4:
                insert();
                break;
            case 5:
                display();
                break;
            case 6:
                exit(0);
                break;
            default:
                printf("\nEnter the correct choice:");
        }

        printf("\nDo you want to continue? (y/n): ");
        scanf(" %c", &g); // Note the space before %c to consume any newline character
    } while (g == 'y' || g == 'Y');

    return 0;
}

void create() {
    printf("\nEnter the number of nodes (max %d): ", MAX);
    scanf("%d", &n);
    
    if (n > MAX) {
        printf("Cannot create more than %d elements.\n", MAX);
        n = MAX; // Limit to MAX if user enters a larger number
    }

    for (int i = 0; i < n; i++) {
        printf("Enter element %d: ", i + 1);
        scanf("%d", &b[i]);
    }
}

void deletion() {
    int pos;
    printf("\nEnter the position you want to delete (1 to %d): ", n);
    scanf("%d", &pos);

    if (pos < 1 || pos > n) {
        printf("\nInvalid Location.\n");
    } else {
        for (int i = pos - 1; i < n - 1; i++) {
            b[i] = b[i + 1]; // Shift elements left
        }
        n--; // Decrease the number of elements
    }

    printf("\nThe elements after deletion:\n");
    display();
}

void search() {
    int e;
    printf("\nEnter the element to be searched: ");
    scanf("%d", &e);
    
    int found = 0; // Flag to track if element is found
    for (int i = 0; i < n; i++) {
        if (b[i] == e) {
            printf("Value %d is found at position %d.\n", e, i + 1);
            found = 1;
            break; // Element found, exit the loop
        }
    }
    if (!found) {
        printf("Value %d is not in the list.\n", e);
    }
}

void insert() {
    int pos;
    printf("\nEnter the position you need to insert (1 to %d): ", n + 1);
    scanf("%d", &pos);

    if (pos < 1 || pos > n + 1) {
        printf("\nInvalid Location.\n");
    } else {
        if (n >= MAX) {
            printf("\nCannot insert more elements. The array is full.\n");
            return;
        }

        for (int i = n; i >= pos; i--) {
            b[i] = b[i - 1]; // Shift elements right
        }

        printf("Enter the element to insert: ");
        scanf("%d", &b[pos - 1]); // Insert the element at the correct position
        n++; // Increase the number of elements
    }

    printf("\nThe list after insertion:\n");
    display();
}

void display() {
    printf("\nThe elements of the list are:");
    for (int i = 0; i < n; i++) {
        printf("\n%d", b[i]);
    }
    printf("\n");
}
