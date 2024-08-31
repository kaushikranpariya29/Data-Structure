#include<iostream>
using namespace std;

class node
{
    public:
        int data;
        node* next;

        node()
        {
            data = 0;
            next = NULL;
        }
};

class linklist
{
    node *head = NULL;
    node *newnode, *temp, *prev;

    public:
        void insertatfirst(int data)
        {
            if(head == NULL)
            {
                newnode = new node();
                newnode -> data = data;
                head = newnode;
                newnode -> next = head;
            }
            else
            {
                newnode = new node();
                newnode -> data = data;

                temp = head;
                while(temp -> next != head)
                {
                    temp = temp -> next;
                }
                newnode -> next = head;
                head = newnode;
                temp -> next = head;
            }
        }
        void insertatlast(int data)
        {
            if(head == NULL)
            {
                newnode = new node();
                newnode -> data = data;
                head = newnode;
                newnode -> next = head;
            }
            else
            {
                temp = head;
                while(temp -> next != head)
                {
                    prev = temp;
                    temp = temp -> next;
                }
                newnode = new node();
                newnode -> data = data;
                temp -> next = newnode;
                newnode -> next = head;
            }
        }
        void insertatuserchoice()
        {
            int count = 0;
            int pos;
            int data;
            temp = head;
            while(temp -> next != head)
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
                    cout << "Enter your data = ";
                    cin >> data;
                    insertatfirst(data);
                }
                else if(pos == count)
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
                    prev -> next = newnode;
                }
            }
        }
        void deletefromfirst()
        {
            if(head == NULL)
            {
                cout << "Linklist is empty" << endl;
            }
            else
            {
                temp = head;
                while(temp -> next != head)
                {
                    temp = temp -> next;
                }
                temp -> next = head -> next;
                temp = head;
                head = temp -> next;
                delete temp;
            }
        }
        void deletefromlast()
        {
            temp = head;
            while(temp -> next != head)
            {
                prev = temp;
                temp = temp -> next;
            }
            prev -> next = head;
            delete temp;
        }
        void deletefromuserchoice()
        {
            int count = 0;
            int pos;
            temp = head;
            while(temp -> next != head)
            {
                count++;
                temp  = temp -> next;
            }
            count++;
            cout << "Count = " << count << endl;

            cout << "Enter position = ";
            cin >> pos;

            if(count >= pos && pos > 0)
            {
                if(pos == 1)
                {
                    deletefromfirst();
                }
                else if(pos == count)
                {
                    deletefromlast();
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
                    delete temp;

                }
            }
        }
        void display()
        {
            temp = head;
            while(temp -> next != head)
            {
                cout << temp -> data << " ";
                temp = temp -> next;
            }
            cout << temp -> data << endl;
        }
};

int main()
{
    int ch, data;
    linklist obj;

    do
    {
        cout << "Press 0 to exit" << endl;
        cout << "Press 1 to insert at first" << endl;
        cout << "Press 2 to insert at last" << endl;
        cout << "Press 3 to insert at user choice" << endl;
        cout << "Press 4 to delete at first" << endl;
        cout << "Press 5 to delete at last" << endl;
        cout << "Press 6 to delete at user choice" << endl;
        cout << "Press 7 to display" << endl;

        cout << "Enter your choice = ";
        cin >> ch;

        switch(ch)
        {
            case 1:
                cout << "Enter you data = ";
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
                obj.deletefromfirst();
                break;
            case 5:
                obj.deletefromlast();
                break;
            case 6:
                obj.deletefromuserchoice();
                break;
            case 7:
                obj.display();
                break;
        }
    } while (ch!=0);
    
}