# LeetCode-23-Merge-k-sorted-linked-lists
合并K个排序链表(刷爆难题-4)

题目链接：https://leetcode-cn.com/problems/merge-k-sorted-lists/


    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None

    class Solution:
        def mergeKLists(self, lists: List[ListNode]) -> ListNode:
            def func(list1,list2):
                res=ListNode(-1)
                temp=res
                while list1 and list2 :
                    if list1.val<=list2.val:
                        a=list1
                        temp.next=a
                        list1=list1.next
                    else:
                        a=list2
                        temp.next=a
                        list2=list2.next
                    temp=temp.next
                if list1:
                    temp.next=list1
                elif list2:
                    temp.next=list2
                return res.next
            n=len(lists)
            if n==0:
                return None
            while n>1:
                new=func(lists[0],lists[-1])
                lists[0]=new
                del lists[-1]
                n-=1
            return lists[0]
