# C Programming

## Size of Array

- 1D Array

```c
int array[] = { 5, 10, 15, 20, 25};

size_of_array = sizeof(array) / sizeof(array[0]);
```

- 2D Array

```c
int array[2][5] = {{5, 10, 15, 20, 25}, {2, 4, 6, 8, 10}};

size_of_row = sizeof(array) / sizeof(array[0]);
size_of_column = sizeof(array[0]) / sizeof(array[0][0]);
```

## String of Array

```c
int main()
{
    char cars[][10] = {"Saga", "Kancil", "Myvi"};
    for (int i = 0; i < sizeof(cars) / sizeof(cars[0]); i++)
    {
        printf("%s\n", cars[i]);
    }
    return 0;
}
```

## String Copy

```c
char str1[] = "Hello World!";
char str2[30];
strcpy(str2, str1);
```

## Struct

- similar to `Class` in other language, but no `method`.

```c
struct Person { // DEFINE
    char name[];
    int age;
};

int main() {
    struct Person person1;  // DECLARE
    person1.age = 26;   // ASSIGN
    return 0;
};
```

## Typedef

- create alias for already existing data type.

```c
typedef int Integer;  // Create an alias "Integer" for "int"
```

- simplify `struct`

```c
typedef struct Person { // DEFINE
    char name[];
    int age;
} Person;   // alias

int main() {
    Person person1;  // DECLARE
    person1.age = 26;   // ASSIGN
    return 0;
};
```

## Array of struct

```c
Student student1 = {"Stuart", 3.1};
Student student2 = {"Michael", 3.6};
Student student3 = {"Sunday", 4.0};
Student student4 = {"Robin", 2.0};

Student students[] = {student1, student2, student3, student4};
```

## Enum

- a set of named integer constants.
- not strings, but can be treated as `int`.

```c
enum Enum {element1, element2, element3};
```

## Pseudo Random Number

```c
#include <time.h>
int main()
{
    srand(time(0)); // seed
    int number1 = (rand() % 6) + 1; // 1-6
    printf("%d", number1);
    return 0;
}
```

## Pointer

- a variable that **points to** (stores the address of) another variable.

```c
int main()
{
    int num = 42; // Declare an integer variable
    int *ptr;     // Declare a pointer to an integer

    ptr = &num; // Assign the address of "num" to "ptr"
    printf("Value of num: %d\n", num);             // Output: 42
    printf("Address of num: %p\n", &num);          // Output: Address of num (e.g., 0x7ffdfb4c)
    printf("Value of ptr: %p\n", ptr);             // Output: Address of num (same as above)
    printf("Value pointed to by ptr: %d\n", *ptr); // Output: 42 (dereferencing)
    return 0;
}
```
