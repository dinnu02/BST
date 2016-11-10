# BST
#include<stdio.h>
#include<malloc.h>
struct node
{
 int data;
 struct node *lchild,*rchild;
}*ptr,*ptr1,*root,*new;
void insertion();
void preorder (struct node *);
void inorder (struct node *);
void postorder (struct node *);
void main()
{
 int ch,c;
 clrscr();
 root->data=NULL;
 root->lchild=NULL;
 root->rchild=NULL;

 ptr=root;
 while(1)
 {
  printf("\n enter your choice of operation");
  printf("\n 1. insertion \t 2.Traverse");
  scanf("%d",&ch);
  switch(ch)
  {
    case 1:
	   insertion();
	   break;
    case 2:
	   printf("\n Enter your traversal");
	   printf("\n 1. Preorder 2. Inorder 3. Postorder");
	   scanf("%d",&c);
	   if(c==1)
	   {
		printf("\n Nodes in BST are");
		preorder(root);
	   }
	   else if(c==2)
	   {
		printf("\n Nodes in BST are");
		inorder(root);
	   }
	   else if(c==3)
	   {
		printf("\n Nodes in BST are");
		postorder(root);
	   }
	   break;
    default : exit(0);
  }
 }
 getch();
}
void insertion()
{
  int item,flag=0;
  ptr=root;
  printf("\n Enter data part of node to be insert");
  scanf("%d",&item);
  while(ptr!=NULL && flag==0)
  {
    if(item==ptr->data)
    {
      printf("\n Item alredy exist in BST");
      flag=1;
    }
    else if(item<ptr->data)
    {
     ptr1=ptr;
     ptr=ptr->lchild;
    }
    else if(item>ptr->data)
    {
      ptr1=ptr;
      ptr=ptr->rchild;
    }
  }

  if(ptr==NULL)
  {
    new=malloc(sizeof(struct node));
    new->data=item;
    new->lchild=NULL;
    new->rchild=NULL;
    if(root->data==NULL)
    {
    root=new;
    printf("\n Node %d is inserted succussfully  as ROOT Node",item);
    }
    else if(item<ptr1->data) /* inserting new node as left child to its parent*/
    {
      ptr1->lchild=new;
      printf("\n Node %d is inserted succussfully LEFT child",item);
    }
    else                /* inserting new node as right child to its parent*/
    {
      ptr1->rchild=new;
      printf("\n Node %d is inserted succussfully Right Child",item);
    }
  }
}
void preorder(struct node *p)
{
 if(p!=NULL)
  {
   printf("\t %d",p->data);
   preorder(p->lchild);
   preorder(p->rchild);
  }
}
void inorder(struct node *p)
{
 if(p!=NULL)
  {
   inorder(p->lchild);
   printf("\t %d",p->data);
   inorder(p->rchild);
  }
}
void postorder(struct node *p)
{
 if(p!=NULL)
  {
   postorder(p->lchild);
   postorder(p->rchild);
   printf("\t %d",p->data);
  }
