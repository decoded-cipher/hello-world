#include<iostream.h>
#include<stdlib.h>
#include<conio.h>
typedef struct bin
{
	int data;
	struct bin *l,*r;
}node;
class tree
{
public:
void insert(node*,node*);
void inorder(node*);
void preorder(node*);
void postorder(node*);
node *getnode()
{
node *t;
t=new node ;
t->l=NULL;
t->r=NULL;
return t;
}
};
  void tree::inorder(node *t)
{
	if(t!=NULL)
	{
		inorder(t->l);
		cout<<t->data<<" ";
		inorder(t->r);
	}
}
  void tree::preorder(node *t)
{
	if(t!=NULL)
	{
	 cout<<t->data<<" ";
	preorder(t->l);
	preorder(t->r);
	}
}
      void tree::postorder(node *t)
{
	if(t!=NULL)
	{
	postorder(t->l);
	postorder(t->r);
	cout<<t->data<<" ";
	}
}
void tree::insert(node *root,node *new1)
{
char c;
cout<<"\n\t\t\t Insert to the right or left of "<<root->data;
c=getche();
if(c=='r')
{
if(root->r==NULL)
root->r=new1;
else
insert(root->r,new1);
}
else
{
     if(root->l==NULL)
      root->l=new1;
else
      insert(root->l,new1);
 }
 }


	void main()
	{
	int choice;
	char ans='n';
	node *new1,*root;

	clrscr();
	tree t1;
	root=NULL;
	while(1){
	clrscr();
	cout<<"\n\n\n\t\t TREE TRAVERSAL    \n";
	cout<<"\n\t\t  1.Create\n";
	cout<<"\n\t\t  2.Preorder\n";
	cout<<"\n\t\t  3.Inorder\n";
	cout<<"\n\t\t  4.Postorder\n";
	cout<<"\n\t\t  5.exit ";
	cout<<"\n\n\t Enter The Option : ";
		cin>>choice;
	switch(choice)
	{
			case 1:
			{        clrscr();
				do
					{
					new1=t1.getnode();
					cout<<"\n\t\t\ Enter the node :";
					cin>>new1->data;
					if(root==NULL)
					root=new1;
					else
					t1.insert(root,new1);
					cout<<"\n\n\t\t\t Do You Want To Continue  : ";
					ans=getche();
					}while(ans=='y');
					break;

			}
			case 2:
			{
				clrscr();
				if(root==NULL)
				cout<<"Tree not exist";
				else
				{
				       cout<<"\n\n\n\t\t\t****PREORDER TRAVERSAL****\n\n\n\t";
				       t1.preorder(root);
				}
				getch();
				break;
			 }
			case 3:
			{
				clrscr();
				if(root==NULL)
				cout<<"Tree not exist";
				else
				{
					cout<<"\n\n\n\t\t\t****INORDER TRAVERSAL****\n\n\t";
					t1.inorder(root);
				}
				getch();
				break;
			 }
			case 4:
			{
				clrscr();
				if(root==NULL)
				cout<<"Tree not exist";
				else
				{
					cout<<"\n\n\n\t\t\t****POSTORDER TRAVERSAL****\n\n\n\t";
					t1.postorder(root);
				}

				getch();
				break;

			}
			case 5:
				exit(1);


	}
	clrscr();
	}
			getch();}
