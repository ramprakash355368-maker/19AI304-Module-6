# 19AI304 - Fundamentals of C Programming - Even Junior -2026

# IAPR 6 - Module 6

# Exp.1 : Area and Perimeter of a Circle Using Pointer and Function

## Aim:

To write a C program that calculates the area and perimeter (circumference) of a circle using functions with pointer arguments.

## Algorithm:

1. Start the program.
2. Define a macro constant pi as 3.14.
3. Define two functions:
   * area(int *r) → calculates and prints the area of the circle.
   * peri(int *r) → calculates and prints the perimeter of the circle.
4. In the main() function:
   * Declare an integer variable r for radius.
   * Read the value of radius from the user.
   * Pass the address of r to both area() and peri() functions.
5. The functions use pointer dereferencing (*r) to access the radius value.
6. Print the calculated area and perimeter.
7. End the program.

## Program.:

```c
#include <stdio.h>
#define pi 3.14

void area(int *r) {
    printf("Area of Circle = %.2f\n", pi * (*r) * (*r));
}

void peri(int *r) {
    printf("Perimeter of Circle = %.2f\n", 2 * pi * (*r));
}

int main() {
    int r;
    scanf("%d", &r);
    area(&r);
    peri(&r);
    return 0;
}
```

## Output:

<img width="728" height="201" alt="503043953-9185bd83-d961-439b-9cd4-355fccc2714a" src="https://github.com/user-attachments/assets/bc369ffe-862b-46c8-af10-ce22b5f56f29" />

## Result:

Thus, The C program to calculates the area and perimeter (circumference) of a circle using functions with pointer arguments was successfully executed.

***

# Exp.2 : Add Elements to an Existing Array Using realloc()

## Aim:
To write a C program that dynamically allocates memory for an array using malloc(), expands its size using realloc(), and adds new elements to it.

## Algorithm:

1. Start the program.
2. Declare an integer pointer arr to store the base address of dynamically allocated memory.
3. Define two variables:
   * currentsize → initial size of the array.
   * newsize → number of additional elements to be added.
4. Use malloc() to allocate memory for currentsize elements.
   * If memory allocation fails, display an error message and exit.
5. Initialize the first four elements of the array (1, 2, 3, 4).
6. Use realloc() to increase the size of the array to hold currentsize + newsize elements.
7. Add the new elements (12, 10, 8) to the extended part of the array.
8. Print all array elements to confirm both old and new values are stored correctly.
9. Use free() to release the allocated memory.
10. End the program.

## Program:

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int *arr;
    int currentsize = 4;
    int newsize = 3;
    int newnewsize = currentsize + newsize;

    arr = (int*)malloc(currentsize * sizeof(int));
    if (arr == NULL) {
        printf("No memory");
        return 1;
    }

    arr[0] = 1;
    arr[1] = 2;
    arr[2] = 3;
    arr[3] = 4;

    arr = (int*)realloc(arr, newnewsize * sizeof(int));

    arr[4] = 12;
    arr[5] = 10;
    arr[6] = 8;

    for (int i = 0; i < newnewsize; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    free(arr);
    return 0;
}
```

## Output:

<img width="437" height="115" alt="503044745-d9bfc7ff-948f-4bff-98e3-aeb462e30129" src="https://github.com/user-attachments/assets/f30c1f70-6bd7-4733-b9c0-932be8f23d25" />

## Result:

Thus, The C program to dynamically allocates memory for an array using malloc(), expands its size using realloc(), and adds new elements to it was successfully executed.

*** 

# Exp.3 : Store and Display Student Information Using Structures

## Aim:

To write a C program using structures to store and display the information of 5 students including roll number, name, and marks.

## Algorithm:

1. Start the program.
2. Define a structure named info with the following members:
   * name → character array to store the student’s name.
   * marks → float variable to store marks.
   * rollno → integer to store the roll number.
3. Declare an array s[5] of structure type info to store data for 5 students.
4. Using a loop from 0 to 4:
   * Assign roll number as i + 1.
   * Read the student’s name and marks from the user.
5. After input, print the details of all students using another loop.
6. End the program.

## Program:

```c
#include <stdio.h>

struct info {
    char name[20];
    float marks;
    int rollno;
};

int main()
{
    int i;
    struct info s[5];
    
    for (i = 0; i < 5; i++) {
        s[i].rollno = i + 1;
        scanf("%s", s[i].name);
        scanf("%f", &s[i].marks);
    }
    
    printf("Displaying Information:\n");
    for (i = 0; i < 5; i++) {
        printf("Roll number: %d\n", s[i].rollno);
        printf("First name: %s\n", s[i].name);
        printf("Marks: %.1f\n", s[i].marks);
        printf("\n");
    }
}
```

## Output:

<img width="638" height="576" alt="503045576-35e932ee-0de1-4eb8-80db-ebe0159a47eb" src="https://github.com/user-attachments/assets/9714b41f-09ee-42d0-867d-d0ea2fc07fdb" />

## Result:

Thus, The C program using structures to store and display the information of 5 students including roll number, name, and marks was successfully executed. 

***

# Exp.4 : EB Bill Calculation Using Structures

## Aim:

To write a C program using structures to calculate the electricity bill for 3 customers based on their previous and current readings.

## Algorithm:

1. Start the program.
2. Define a structure Customer with the following members:
   * cust_no → Customer number.
   * prev_reading → Previous meter reading.
   * curr_reading → Current meter reading.
   * units → Units consumed.
   * bill → Total bill amount.
3. Create an array c[3] to store data of 3 customers.
4. For each customer:
   * Input customer number, previous reading, and current reading.
   * Calculate units consumed as: units = curr_reading - prev_reading
   * Calculate bill using the following conditions:
      + If units ≤ 100 → ₹2 per unit
      + If 101–200 → ₹3 per unit for next 100 units
      + Above 200 → ₹5 per unit for remaining units
5. Display each customer's number and bill amount.
6. End the program.

## Program:

```c
#include <stdio.h>

struct Customer {
    int cust_no;
    float prev_reading;
    float curr_reading;
    float units;
    float bill;
};

int main() {
    struct Customer c[3];
    int i;
    
    for (i = 0; i < 3; i++) {
        scanf("%d", &c[i].cust_no);
        scanf("%f", &c[i].prev_reading);
        scanf("%f", &c[i].curr_reading);

        // Calculate units consumed
        c[i].units = c[i].curr_reading - c[i].prev_reading;

        // Bill calculation
        if (c[i].units <= 100)
            c[i].bill = c[i].units * 2;
        else if (c[i].units <= 200)
            c[i].bill = (100 * 2) + (c[i].units - 100) * 3;
        else
            c[i].bill = (100 * 2) + (100 * 3) + (c[i].units - 200) * 5;
    }

    printf("Details of the EB Customer\n");
    for (i = 0; i < 3; i++) {
        printf("%d      %.2f\n", c[i].cust_no, c[i].bill);
    }

    return 0;
}
```

## Output:

<img width="686" height="523" alt="503048894-73c2048b-4750-4b49-93da-6bbfa95bb455" src="https://github.com/user-attachments/assets/505a97bd-532e-4155-9cae-faec985d2e4e" />

## Result:

Thus, The C program using structures to calculate the electricity bill for 3 customers based on their previous and current readings was successfully executed.

***

# Exp.5 : Gas Customer Bill Calculation Using Structures

## Aim:

To write a C program using structures to calculate and display gas bill details for 3 customers, applying a subsidy on the total amount.

## Algorithm:

1. Start the program.
2. Define a structure gas_cust with the following members:
   * cust_no → Customer number.
   * cust_name → Customer name.
   * units_consumed → Number of gas units consumed.
   * subsidy → Subsidy amount (10% of total).
   * tot_amt → Total payable amount after applying subsidy.
3. Input customer details (number, name, and units consumed) for 3 customers.
4. For each customer, calculate the total bill based on the following slab rates:
   * Up to 50 units: ₹10 per unit + fixed charge ₹50.
   * 51 to 100 units: ₹10 per unit for first 50 units and ₹20 per unit for next units.
   * Above 100 units: ₹10 per unit for first 50, ₹20 per unit for next 50, and ₹30 per unit beyond 100.
5. Calculate subsidy = 10% of total bill and subtract it from the total amount.
6. Display customer number, units consumed, and final total amount.
7. End the program.

## Program:

```c
#include <stdio.h>
struct gas_cust
{
    int cust_no;
    char cust_name[30];
    int units_consumed;
    float subsidy;
    int tot_amt;
};

int main()
{
    struct gas_cust bill[3];
    for(int i=0; i<3; i++)
    {
        scanf("%d %s %d", &bill[i].cust_no, bill[i].cust_name, &bill[i].units_consumed);
    }

    for(int i=0; i<3; i++)
    {
        if(bill[i].units_consumed <= 50)
        {
            bill[i].tot_amt = 50 + (10 * bill[i].units_consumed);
        }
        else if(bill[i].units_consumed > 50 && bill[i].units_consumed <= 100)
        {
            bill[i].tot_amt = 50 + (50 * 10) + (20 * (bill[i].units_consumed - 50));
        }
        else
        {
            bill[i].tot_amt = 50 + (50 * 10) + (50 * 20) + (30 * (bill[i].units_consumed - 100));
        }

        bill[i].subsidy = (float)10 / 100 * bill[i].tot_amt;
        bill[i].tot_amt = bill[i].tot_amt - bill[i].subsidy;
    }

    printf("Customer Gas Details\n");
    for(int i=0; i<3; i++)
    {
        printf("%d  %d  %d\n", bill[i].cust_no, bill[i].units_consumed, bill[i].tot_amt);
    }

    return 0;
}
```

## Output:

<img width="594" height="278" alt="503049830-36e51642-04fe-4b14-bc1a-c17ff907243a" src="https://github.com/user-attachments/assets/956b8020-f2c1-42fb-96d3-032f6ab4c125" />

## Result:

Thus, The C program using structures to calculate and display gas bill details for 3 customers, considering consumption slabs and a 10% subsidy on the total amount was successfully executed.
