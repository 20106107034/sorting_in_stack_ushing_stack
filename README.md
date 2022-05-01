
#include <stdio.h>
#include <stdlib.h>
#define MAX 10
int top = -1;
int top1 = -1;

void stack_1_push(int arr[])
{
    if (top == MAX - 1)
    {
        printf("\n ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^-----overflow-----^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^\n");
    }
    else
    {
        top++;
        printf("\n enter your element  \n");
        int s;
        scanf("%d", &s);
        arr[top] = s;
    }
}

int stack_1_pop(int arr[])
{
    if (top == -1)
    {
        printf("________________________________________________underflow________________________________________________________\n");
        return -1;
    }
    else
    {
        int val = arr[top];
        top--;
        return val;
    }
}
void display_element_of_stack(int arr[],int temp[])
{
   // while((getchar())!='\n');

    printf("your stack is -> ");
   //  for (int i = 0; i <= top; i++)
   //    printf("%d ", arr[i]);
    
          while (top!= -1)
         {
             int val = stack_1_pop(arr);
     
            top1++;
             temp[top1] = val;
      
            //    printf("%d ",val);
         }
          while (top1 != -1)
         {
             top++;
             arr[top] = temp[top1];
             printf("%d ", arr[top]);
             top1--;
         }
  //                                                                printf("\n %d ",top1);
  //                                                                    printf("%d ",top);
   // printf("\n");
    // printf("\n press enter to continue the program \n");
    printf("\n");
}

void sort_by_temp_stack(int arr[], int temp[])
{
   // while((getchar())!='\n');
    while (top != -1)
    {

        int te = stack_1_pop(arr);
        if (top1 == -1 || temp[top1] > te)
        {
            top1++;
            temp[top1] = te;
        }
        else
        {
            while (temp[top1] < te)
            {
                top++;
                arr[top] = temp[top1];
                top1--;
            }
            top1++;
            temp[top1] = te;
        }
    }

    while (top1 != -1)
    {
        top++;
        arr[top] = temp[top1];
        top1--;
    }
}

int main()
{
    int i = 0, arr[MAX], temp[MAX];
    printf("=================================================================================================================================================\n");
    printf("--------------------------------welcome_in_sorting-of-stack_element------------------------------------------------\n");
    while (i == 0)
    {
       // while((getchar())!='\n');
            int ch;
        printf("=============================================================================================================================================\n");
        printf("\t 1.)stop the programe \n");
        printf("\t 2.) push the element \n");
        printf("\t 3.) pop the element \n");
        printf("\t 4.) display the stack element \n");
        printf("\t 5.) sorting of stack \n");
        printf("=============================================================================================================================================\n");

        scanf("%d", &ch);
        switch (ch)
        {
        case 1:
            i = 2;
            break;
        case 2:
            stack_1_push(arr);
            break;
        case 3:
            printf("you pop the element %d   \n ", stack_1_pop(arr));
            break;
        case 4:
            display_element_of_stack(arr,temp);
            break;
        case 5:
            sort_by_temp_stack(arr,temp);
            break;
        default:
            printf("\n invalid input \n ");
            break;
        }
    }

    // int *temp = (int *)malloc(sizeof(int) * (top + 1));

   // sort_by_temp_stack(temp, arr);

    //display_element_of_stack(arr);
    return 0;
 } 
