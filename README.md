# Shortest-Distance-between-given-strings-in-a-sentence-C-.

Three strings are given as an input.In which first line contains a sentence,second and third line contains a word from the given string.We need to find the shortest position between the strings.
(eg):the pond king frog kernel quick king the
king
kernel
(o/p):2

The below code contains the solution for the problem implemented using structures

//Below is the code

#include <stdio.h>
#include<stdlib.h>
#include<string.h>
int p=1;
struct node{
    char s[100];
    int pos;
    struct node * next;
};
struct node *head=NULL;
struct node *tail=NULL;
void insert(char s1[]){
    struct node *temp=malloc(sizeof *temp);
    strcpy(temp->s,s1);
    if(head==NULL){
        head=tail=temp;
        temp->pos=p;
        tail->next=NULL;
        p++;
    }
    else{
        temp->pos=p;
        tail->next=temp;
        temp->next=NULL;
        tail=tail->next;
        p++;
    }
}
void display(){
    struct node *temp=malloc(sizeof *temp);
    temp=head;
    while(temp!=NULL){
        printf("%s ",temp->s);
        printf("%d ",temp->pos);
        temp=temp->next;
    }
    /*printf("%s ",temp->s);
    printf("%d ",temp->pos);*/
}
void find(char s1[],char s2[]){
    struct node *temp=malloc(sizeof *temp);
    int diff=p;
    temp=head;
    while(temp!=NULL){
        if(strcmp(temp->s,s1)==0){
            struct node *temp2=malloc(sizeof *temp2);
            temp2=head;
            while(temp2!=NULL){
                if(strcmp(temp2->s,s2)==0){
                    int diff1=temp->pos-temp2->pos;
                    diff1=abs(diff1);
                    if(diff1<diff){
                        diff=diff1;
                    }
                }
                temp2=temp2->next;
            }
            //printf("%s",temp->s);
            
        }
        
        temp=temp->next;
    }
    //printf("%s %s",s1,s2);
    printf("%d",diff);
}
int main() {
    // Write C code here
    char str[100];
    char str2[100];
    char str3[100];
    scanf("%[^\n]\n%[^\n]\n%[^\n]",str,str2,str3);
    int i=0;
    while(str[i]!='\0'){
        int j=0;
        char str1[100]="";
        while(str[i]!=' ' && str[i]!='\0'){
            str1[j]=str[i];
            j++;
            i++;
        }
        insert(str1);
        //printf("%s",str1);
        i++;
    }
    //display();
    find(str2,str3);
    return 0;
}
