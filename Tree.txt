#include<iostream>
using namespace std;

class node{
    public:
        char data;
        node *left;
        node *right;

        node(){
            data = ' ';
            left = NULL;
            right = NULL;
        }
};

void inorder(node *ptr){
    if(ptr != NULL){
        inorder(ptr -> left);
        cout << ptr -> data << " ";
        inorder(ptr -> right);
    }
}

void preorder(node *ptr){
    if(ptr != NULL){
    	cout << ptr -> data << " ";
        preorder(ptr -> left);
        preorder(ptr -> right);
    }
}

void postorder(node *ptr){
    if(ptr != NULL){
        postorder(ptr -> left);
        postorder(ptr -> right);
        cout << ptr -> data << " ";
    }
}

int main() {
	node *root_a, *b, *c, *d, *e, *g;
	
	root_a = new node();
	root_a->data = 'A';
	b = new node();
	b->data = 'B';
	c = new node();
	c->data = 'C';
	d = new node();
	d->data = 'D';
	e = new node();
	e->data = 'E';
	g = new node();
	g->data = 'G';
	
	
	root_a->left = b;
	root_a->right = c;
	
	b->left = d;
	b->right = e;
	
	c->right = g; 
	
	postorder(root_a);
}

