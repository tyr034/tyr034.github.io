---
layout: post
title: Elements of Algorithms 
description: 
category: blog
---

##Introduction:
Problmes are infinite. The only thing we could do is to seize the unchange. 

##Principles: 
<ul>
	<li> There should be one (and preferably only one) obvious way to do it </li>
	<li> If the implementation is hard to explain, it's a bad idea </li> 
</ul>

##Elements:
###Two Pointers:
2Sum/3sum/4Sum

Linked List Cycle

	def hasCycle(head):
 		slow = head 
    	fast = head
    	while fast and fast.next:
        	slow,fast = slow.next,fast.next.next
       	 	if slow is fast:
            	return True 
    	return False 


Intersection of Two Linked Lists

	def getIntersectionNode(headA, headB):
        if headA is None or headB is None:
            return None
        p1,p2,q1,q2 = headA, headA,headB,headB
        lengthA,lengthB = 0, 0
        while p1:
            p1 = p1.next
            lengthA += 1
        while q1:
            q1 = q1.next
            lengthB += 1
        
        if lengthA > lengthB:
            for i in range(lengthA-lengthB):
                p2 = p2.next
        elif lengthB>lengthA:
            for i in range(lengthB-lengthA):
                q2 = q2.next
                
        while p2 and q2:
            if p2 == q2:
                return p2
            p2 = p2.next
            q2 = q2.next
                
        return None

Valid Palindrome

	def isPalindrome(s):
        start = 0
        end = len(s)-1
        while start<end:
            while s[start].isalnum() == False and start < end :
                start +=1
            while s[end].isalnum() == False and start <end:
                end -=1 
            if s[start].lower() != s[end].lower():
                return False
            start +=1
            end -= 1
            
        return True 


Sorting and Rearranging of a List 

###Binary Search:
sqrt(x)

	def sqrt(self, x):
        left = 0
        right = x
        while left <= right :
            m = left + (right-left)//2
            if m*m == x:
                return m 
            elif m*m <x:
                left = m+1
            else:
                right = m-1
        return (left+right)//2

pow(x,n)

	def pow(x, n):
        if n>0:
            return helper(x,n)
        elif n==0:
            return 1
        else:
            res = helper(x,-n)
            return 1/res
        
    def helper(x,n):
        if n==1:
            return x
        if n==2:
            return x*x
        elif n%2==0:
            res = helper(x,n//2)
            return res*res
        else:
            res = helper(x,(n-1)//2)
            return x*res*res

Search in Rotated Sorted Array:
Median of Two Sorted Array,

###For Loop and Recursion (Backtracking): 
Combination Sum: 
Given a set of candidate numbers (C) and a target number (T), find all unique combinations in C where the candidate numbers sums to T. The same repeated number may be chosen from C unlimited number of times
	def combinationSum(self, candidates, target):
        if candidates is None or len(candidates) == 0:
            return None 
        return self.helper(sorted(candidates),target,[],[],0)   
        
    def helper(self,candidates, target,element,res,start):
        if target < 0:
            return 
        if target == 0:
            res.append(element[:])
        for i in range(start,len(candidates)):
            if i>=1 and candidates[i]== candidates[i-1]:
                continue
            self.helper(candidates,target-candidates[i],element+[candidates[i]],res,i)
        return res 
        
Depth-first Search, All Kinds of Path Problems in Tree, Surroned region in a Matrix, Permutations, Combinations, Subsets. 

###Dynamic Programming: 
Maximum Subarray, Buy and Sell Stock 

###Useful Data Structures: 
####HashTable: 
the single most important data structure when you need a O(1) lookup
####Queue/Stack: 
when you need to maintain certain order: Find the first non-repeating characters in a string;
####Priority Queue/ Heap: 
merge K sorted List:
	def mergeKLists(self, lists):
        if lists is None:
            return None 
        h=[]
        dummy = ListNode(0)
        result = dummy
        
        for head in lists:
            if head != None:
                heapq.heappush(h,(head.val,head))
        while h:
            current = heapq.heappop(h)[1]
            dummy.next = current
            dummy = dummy.next
            if current.next is not None:
                heapq.heappush(h,(current.next.val,current.next))
        
        return result.next
        

####Prefix Tree



