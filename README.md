# singlyLL
#include<bits/stdc++.h>
using namespace std;

class Node{
  public: //access modifier
  int data; //the data value
  Node*next; //the pointer to next value
  
  public:
  
  Node(int data1,Node*next1){//constructor
    data=data1; //initialized data with the provided value
    next=next1; //initialized next with the provided
  }
  
  Node(int data1){
    data=data1; //initialize data with the provided value
    next=nullptr; //iniatialize next as null since it's end of the list
  }
  
};

void printLL(Node*head){
  while(head!=nullptr){
    cout<<head->data<<" ";
    head=head->next;
  } cout<<endl;
}

Node*insertAtHead(Node*head,int val){
  Node*temp=new Node(val,head);
  return temp;
}

Node*insertAtTail(Node*head,int val){
  Node*temp=new Node(val);
  Node*headTemp=head;
  
  if(head==NULL) return temp;
  
  while(headTemp->next!=NULL){
    headTemp=headTemp->next;
  }
  headTemp->next=temp;
  return head;
}

Node*deleteTail(Node*head){
  
  if(head==NULL || head->next==NULL) return NULL;
  
  Node*temp=head;
  
  while(temp->next->next!=nullptr){
    temp=temp->next;
  }
  //delete the last node
  delete temp->next;
  
  //set the second last node to nullptr , effectively removing the last node
  temp->next=nullptr; 
  
  return head;
}

int length(Node*head){
  Node*temp=head;
  int count=0;
  
  while(temp!=NULL){
    count++;
    temp=temp->next;
  }
  return count;
}

bool checkPresent(Node*head,int target){
  Node*temp=head;
  
  while(temp!=NULL){
    if(temp->data == target) return true;
    temp=temp->next;
  }
  return false;
}

int main(){
  vector<int>arr={2,5,8,7}; int val=1;
  
  Node*head=new Node(arr[0]);
  head->next=new Node(arr[1]);
  head->next->next=new Node(arr[2]);
  head->next->next->next=new Node(arr[3]);
  
  printLL(head);
  
  head=insertAtHead(head,val);
  
  printLL(head);
  
   head=deleteTail(head);
  
    printLL(head);

  head=insertAtTail(head,9);
  
  printLL(head);
  
  cout<<"Length = "<<length(head)<<endl;
  cout<<"check Present= "<<checkPresent(head,1)<<endl;
  
  return 0;
  
}
