---
layout: post
title: Where is the Nth from the end of LinkedList ?
subtitle: How can I find the Nth from the end of LinkedList
category: Extenstion Of DataStructure
tags: [list]
permalink: /2016/07/08/Utilization_Of_LinkedList1/
---

# how to look for Nth node from the end of Linked List 
(끝에서 n번째 노드를 찾아 보자.)

## basic method -> 가장 무식한 방법

 just searching for list with brute-force method.
 
 in other words,
 
 while searching for Linked List, calculate what times is in Linked list
 
 -> 리스트틀 탐색하면서 현재 노드가 몇번째인지 계산을 한다. 

```c
 struct ListNode searchingFunction (struct ListNode * head, int Nth)
 {
   struct ListNode * temp = head;
   
   for( ; temp != NULL ; temp = temp -> next)  /// location of current list node 
   {
      int count1 = 0; 
      for(structure Listnode temp2 = temp ; temp2 != NULL ; temp2 = temp2 -> next) // calculate what times from the end of list
      {
         count1++;
      }
      
      if (count1 == Nth)
        break;
   }
   return temp;
 }
```

## improving the above method more

 way to improving the time complexity a little bit 
 -> 약간의  시간 복잡도를 향상시키는 방법
 
 use ths hash table -> <location of node, address of Node> == <key, value> of hash table 
 
 while making hash table, you can notice the length of list, so You can calculate location of Nth.
 
 -> 해쉬 테이블을 만들면서 리스트의 길이 M 
 
 -> location of Nth = M-n+1를 이용해서 바로 hash table을 계산 하면된다. 
 
 -> 즉, hash table을 만드는데 시간이 필요하여 위의 방법보다 시간복잡도는 향상한다. 
 
 -> but, space complexity is bad than above method.

```c
 void MakeHashTable(struct List* head)
 {
    struct List * temp = head;
    int count = 0;
     for( ; temp != NULL ; temp = temp -> next;
         arr[count++] = temp; // hash table
 }
```
 
## how do you have to look for better way than hash table. 

  -> as first method, don't use double for statement
  
  -> just use the one for statement 
  
  -> 이중 for문을 만들어서 하기 보다는 하나의 for문으로 전체의 길이를 구하면 된다. 
  
  -> after that, M-n+1 을 이용해서 위치 탐색을 하면 끝.
  
  -> 이 방법은 무식한 방법 보다 시간복잡도 훨씬 낮고, 해쉬 테이블 만큼 공간 복잡도가 낮다. 
  
  -> i.e with the total of length of list, use M-n+1 
  
## improving the above method

  -> the above method is two times of for statement.
  
  -> but you can do looking for and calculating the total of length of list 
  
  -> use tow pointer ----pNthNode and pTemp 
  
    ptemp - pNthNode == Nth and ptemp == the end of list.
    
   -> 여기서 두 포인터의 차가 Nth이면 된다. 
 
```c
 int WhichOneIsNth(struct List * head, int Nth)
 {
   struct List * pNthNode = head;
   struct List * pTemp = NULL;
   int count =0;
   
   for (pTmep = head ; pTemp == NULL;) {
       
       count++;
       
       if ( Nth - count > 0 )
           pNthNode = pNthNode -> temp;
           
       pTemp = pTemp -> next;
   }
   
   if ( count >= Nth)
       return PNthnode;
   
   return 0;
   
 }
```

 the above way is how you can calculate 
