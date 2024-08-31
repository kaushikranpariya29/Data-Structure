#include<iostream>
using namespace std;

class node
{
    public:
        int data;
        node *next;
        node *prev;

        node()
        {
            data = 0;
            next = NULL;
            prev = NULL;
        }
};

class doublelinklist
{
    node *head = NULL;
    node *temp, *prev, *newnode, *ptr;

    public:
        void insertatfirst(int data)
        {
            if(head == NULL)
            {
                newnode = new node();
                newnode -> data = data;
                head = newnode;
            }
            else
            {
                newnode = new node();
                newnode -> data = data;
                newnode -> next = head;
                head -> prev = newnode;
                head = newnode;
            }
        }
        void insertatlast(int data)
        {
            if(head == NULL)
            {
                newnode = new node();
                newnode -> data = data;
                head = newnode;
            }
            else
            {
                temp = head;
                while(temp -> next != NULL)
                {
                    temp = temp -> next;
                }
                newnode = new node();
                newnode -> data = data;

                temp -> next = newnode;
                newnode -> prev = temp;
            }
        }
        void insertatuserchoice()
        {
            int count=0;
            int pos;
            int data; 

            temp = head;
            while(temp -> next != NULL)
            {
                count++;
                temp = temp -> next;
            }
            count++;
            cout << "count = " << count << endl;

            cout << "Enter position = ";
            cin >> pos;

            if((count + 1) >= pos && pos > 0)
            {
                if(pos == 1)
                {
                    cout << "Enter your data = ";
                    cin >> data;

                    insertatfirst(data);
                }
                else if(pos == (count + 1))
                {
                    cout << "Enter your data = ";
                    cin >> data;

                    insertatlast(data);
                }
                else
                {
                    temp = head;
                    for(int i=1 ; i<pos ; i++)
                    {
                        prev = temp;
                        temp = temp -> next;
                    }
                    newnode = new node();

                    cout << "Enter your data = ";
                    cin >> newnode -> data;
                    
                    newnode -> next = temp;
                    newnode -> prev = prev;
                    temp -> prev = newnode;
                    prev -> next = newnode;
                }
            }
        }
        void deleteatfirst()
        {
            if(head == NULL)
            {
                cout << "There is no element in linklist" << endl;
            }
            else
            {
                temp = head;
                head = temp -> next;
                head -> prev = NULL;
                delete temp;
            }
        }
        void deleteatlast()
        {
            if(head == NULL)
            {
                cout << "There is no element in linklist" << endl;
            }
            else
            {
                temp = head;
                while(temp -> next != NULL)
                {
                    prev = temp;
                    temp = temp -> next;
                }
                prev -> next = NULL;
                delete temp;
            }
        }
        void deleteatuserchoice()
        {
            int count=0;
            int pos;
            temp = head;
            while(temp -> next != NULL)
            {
                count++;
                temp = temp -> next;
            }
            count++;
            cout << "Count = " << count << endl;

            cout << "Enter position = ";
            cin >> pos;

            if(count >= pos && pos > 0)
            {
                if(pos == 1)
                {
                    deleteatfirst();
                }
                else if(pos == count)
                {
                    deleteatlast();
                }
                else
                {
                    temp = head;
                    for(int i=1 ; i<pos ; i++)
                    {
                        prev = temp;
                        temp = temp -> next;
                    }

                    prev -> next = temp -> next;
                    temp -> next -> prev = prev;
                    delete temp;
                }
            }
        }
        void display()
        {
            temp = head;
            while(temp != NULL)
            {
                cout << temp -> data << " ";
                temp = temp -> next;
            }
            cout << endl;
        }

        void search(int data)
        {
            int found = 0;
            int count = 1;
            
            temp = head;
            
            while(temp != NULL)
            {
                if(temp -> data == data)
                {
                    found = 1;
                    break;
                }
                else
                {
                    count++;
                    temp = temp -> next;
                }
            }
            if(found == 1)
            {
                cout << "KEY found at position :: " << count << endl;
            }
            else
            {
                cout << "KEY not found" << endl;
            }
        }
        void sorting()
        {
            temp = head;
            while(temp != NULL)
            {
                if(prev -> data > temp -> data)
                {
                    ptr = temp;
                    temp = prev;
                    prev = ptr; 
                }
                prev = temp;
                temp = temp -> next;
            }
        }
};

int main()
{
    doublelinklist obj;
    int data, ch;

    do
    {
        cout << "press 1 to insert at first" << endl;
        cout << "Press 2 to insert at last" << endl;
        cout << "Press 3 to insert at user choice" << endl;
        cout << "Press 4 to delete at first" << endl;
        cout << "Press 5 to delete at last" << endl;
        cout << "Press 6 to delete at user choice" << endl;
        cout << "Press 7 to display" << endl;
        cout << "Press 8 to search" << endl;
        cout << "Press 9 to sort data" << endl;
        cout << "Press 0 to exit" << endl;

        cout << "Enter your choice = ";
        cin >> ch;

        switch(ch)
        {
            case 1:
                cout << "Enter your data = ";
                cin >> data;

                obj.insertatfirst(data);
                break;
            case 2:
                cout << "Enter your data = ";
                cin >> data;

                obj.insertatlast(data);
                break;
            case 3:
                obj.insertatuserchoice();
                break;
            case 4:
                obj.deleteatfirst();
                break;
            case 5:
                obj.deleteatlast();
                break;
            case 6:
                obj.deleteatuserchoice();
                break;
            case 7:
                obj.display();
                break;
            case 8:
                cout << "Enter element = ";
                cin >> data;
                
                obj.search(data);
                break;
            case 9:
                obj.sorting();
        }
    } while (ch!=0);
    
    return 0;
}