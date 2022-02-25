# CIRCULAR-QUEUE
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int data;
        struct node*next;
}*temp,*newnode;
struct node*front=NULL;
struct node*rare=NULL;
void create()
 {
        int value;
        int ch;
        do{
        newnode=(struct node*)malloc(sizeof(struct node*));
        printf("enter the value");
        scanf("%d",&value);
        newnode->data=value;
        newnode->next=NULL;
        if((front==NULL)&&(rare==NULL))
        {
                front=newnode;
                rare=newnode;
        }
        else
        {
                newnode->data=value;
                newnode->next=front;
                front=newnode;
        }
        printf("enter 1-create,0-exist\n");
        scanf("%d",&ch);
        }
        while(ch==1);
 }
void enqueue()
{
        int value;
        newnode=(struct node*)malloc(sizeof(struct node*));
        printf("enter the value");
        scanf("%d",&value);
        newnode->data=value;
        newnode->next=NULL;
        if((front==NULL)&&(rare==NULL))
        {
                front=newnode;
                rare=newnode;
                rare->next=newnode;
        }
        else
        {
                rare->next=newnode;
                rare=newnode;
                newnode->next=front;

        }
}
void dequeue()
{
        front=temp;
        printf("enter the value to deleted");
        if((front==NULL)&&(rare==NULL))
        {
                printf("enter queue is empty");
        }
        else
        {
                front=front->next;
                temp->next=NULL;
                rare->next=front;
                free(temp);
        }
}
void print()
{
        temp=front;
        printf("operations on queue is:");
        do{
                printf("%d",temp->data);
                temp=temp->next;
        }
        while(temp==NULL);
}
int main()
{
        int choice=0;
        printf("operations on queue is:");
        do{
            printf("enter 1-create\n");
            printf("enter 2-enqueue\n");
            printf("enter 3-dequeue\n,4-print\n");
            printf("enter your choice");
            scanf("%d",&choice);
            switch(choice)
        {
                case 1:
                        create();
                        break;
                case 2:
                        enqueue();
                        break;
                case 3:
                        dequeue();
                        break;
                case 4:
                        print();
                        break;
                default:
                        printf("wrong choice");
                        break;
        }
        }while(choice<5);
}

OUTPUT:
