#include <stdio.h>

struct student {
    int roll;
    char name[20];
    int marks[5];
    int total;
    float avg;
};

int main() 
{
    struct student s[10], temp;
    int i, j, sub;
    int max;
    char topper[20];

    // Input
    for (i = 0; i < 10; i++) 
    {
        printf("\nEnter details of student %d\n", i + 1);
        printf("Roll No: ");
        scanf("%d", &s[i].roll);
        printf("Name: ");
        scanf("%s", s[i].name);

        s[i].total = 0;
        for (j = 0; j < 5; j++) 
        {
            printf("Enter marks of subject %d: ", j + 1);
            scanf("%d", &s[i].marks[j]);
            s[i].total += s[i].marks[j];
        }
        s[i].avg = s[i].total / 5.0;
    }

    // Display Result Table
    printf("\nRESULT TABLE\n");
    printf("Roll\tName\tTotal\tAverage\n");
    for (i = 0; i < 10; i++) 
    {
        printf("%d\t%s\t%d\t%.2f\n",
               s[i].roll, s[i].name, s[i].total, s[i].avg);
    }

    // Sorting for Top 3 ranks
    for (i = 0; i < 9; i++) 
    {
        for (j = i + 1; j < 10; j++) 
        {
            if (s[i].avg < s[j].avg) 
            {
                temp = s[i];
                s[i] = s[j];
                s[j] = temp;
            }
        }
    }

    // Display Top 3 Rank Students
    printf("\nTOP 3 RANK STUDENTS\n");
    printf("Rank\tName\tAverage\n");
    for (i = 0; i < 3; i++) 
    {
        printf("%d\t%s\t%.2f\n", i + 1, s[i].name, s[i].avg);
    }

    // Highest marks in each subject
    printf("\nHIGHEST MARKS IN EACH SUBJECT\n");
    for (sub = 0; sub < 5; sub++) 
    {
        max = s[0].marks[sub];
        for (i = 1; i < 10; i++) 
        {
            if (s[i].marks[sub] > max) 
            {
                max = s[i].marks[sub];
            }
        }
        printf("Subject %d Highest Marks = %d\n", sub + 1, max);
    }

    return 0;
}
