# data-structure with c


#include<stdio.h>
#include<stdlib.h>

void create();

void display();

void deleteAtBeg();

void deleteAtMid();

void deleteAtLast();

 struct node 
{
	struct node *prev;
	int data;
	struct node *next;
	
};

struct node *head=NULL, *tail=NULL;

int main()
{
	create();
	display();
    deleteAtBeg();
    display();
   deleteAtMid();
    display();
    deleteAtLast();
    display();
    
	return 0;
}

void create()
{
	int m,ch;
	struct node *temp ;
	
	do{
		printf("\n Enter the data that tou want");
		scanf("%d",&m);
		temp=(struct node*) malloc(sizeof(struct node));
		
		temp->data=m;
		temp->prev=NULL;
		temp->next=NULL;
		
		if(head==NULL)
		{
			head=tail=temp;
		}
		else
		{
			tail->next=temp;
			temp->prev=tail;
			tail=temp;
		
		}
		printf("\n For more nodes to insert type 1");
		scanf("%d",&ch);
		
	}while(ch==1);
	printf("\n");
}

void display()
{
	struct node *ptr ;
	
	ptr=head;

	while(ptr!=NULL)
	{
		printf("%d-> ",ptr->data);
		ptr=ptr->next;
	}
	
	printf("\n");
}

void deleteAtBeg()
{
	struct node *ptr;
	

	ptr=head;
	head=head->next;
	ptr->next=NULL;
	free(ptr);

} 

void deleteAtMid()
{
	struct node *ptr;
	int m;
	printf("\n enter the node you want to delete :");
	scanf("%d", &m);
	ptr=head;
	
	while(ptr->data!=m)
	{	
       ptr=ptr->next;   
    }
    ptr->next->prev=ptr->prev;
   ptr->prev->next=ptr->next;
   ptr->next=NULL;
   ptr->prev=NULL;
   free(ptr);
    
   
}

void deleteAtLast()
	{
		struct node *ptr;
       ptr=tail;
       tail=ptr->prev;
       tail->next=NULL;
       ptr->prev=NULL;
       free(ptr);
    }
 
	

	
