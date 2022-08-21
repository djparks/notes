# Most Common Katas
Most Common Programming Interview Questions in 2019
March 25, 2019

In this article we are going to discuss the most common programming and software engineering related interview questions. Usually these programming interview questions have something to do with algorithms and data structures (and not specific frameworks). The most common interview questions are the following:
palindrome problem
integer reversion problem
anagram problem
reversing an array problem
finding middle node of a linked list problem
reversing a linked list problem
how to verify heap properties problem
#1 INTERVIEW QUESTION – PALINDROME
First of all what is a palindrome? A palindrome is a word, phrase, number, or other sequence of characters which reads the same backward as forward.
By definition, we can say that the first character of a palindrome is the same as the last one. So a better approach is to compare characters same units away from the middle character of the original string.

So we have to use 3 indexes: i, j and k. In every iteration we compare item with index i to item with index j. If there is a mismatch, we know that the string is not a palindrome. This is why it is more efficient than the first approach. Here we have to consider the optimal amount of characters (first approach reverses the string then checks whether the characters are matching or not). Take a look at the implementation:
public static boolean palindrome(String s) {

        int i = 0;
        int j = s.length()-1;
        int k = (i+j)/2;

        for(int index = i;index<=k;index++) {

                if( s.charAt(i) == s.charAt(j) ) {
                        i++;
                        j--;
                } else {
                        return false;
                }
        }

        return true;
}
This approach is quite efficient even when the sequence is not a palindrome. Whenever the characters are not matching we immediately return false. So it has sublinear running time in these cases.
#2 INTERVIEW QUESTION – INTEGER REVERSION
The problem is that we have to reverse an integer. Note that it is not a string so we have to use different operations. What we can do is using the modulo (%) operator to get the last digit in every iteration. We make as many iterations as the number of digits and we keep updating the result accordingly.
public void reverse(int n) {

   int reversed = 0;
   int remainder = 0;

   while(n>0) {
      //get the last digit of the integer n
      remainder = n%10;
      //get rid of the last digit
      n = n/10;
      //append that digit to the solution
      reversed = reversed*10+remainder;
   }

   return reversed;
}
First we define the reversed integer which is the solution we are after. We keep iterating until the original n integer is greater than 0. In every iteration we get the last digit: we can do it with the help of the mod (%) operator. We have to make sure we keep discarding the last digit of the n integer. This is why to use n/10. And of course we have to keep appending the remainder to the solution. We have to deal with the decimals so thats why we use reversed*10+remainder.
#3 INTERVIEW QUESTION – ANAGRAM
Anagram problem is another often programming interview question. So what is this problem exactly? An anagram is word or phrase formed by rearranging the letters of a different word or phrase typically using all the original letters exactly once. For example: silent and listen are anagrams because they contain the exact same letters.
There are several solutions to this problem but the most popular one is to sort the strings alphabetically. After sorting we just have to check whether the letters with the same indexes are matching or not.
public void isAnagram(char[] s1, char[] s2) {

   if(s1.length!=s2.length) return false;

   Arrays.sort(s1);
   Arrays.sort(s2);

   for(int i=0;i<s1.length;i++)
      if(s1[i]!=s2[i])
        return false;

   return true;
}
As you can see the bottleneck is the sorting procedure because it has O(NlogN) running time. The for loop has O(N) linear running time complexity when checking whether the letters are matchin or not. Thats why the final running time complexity is O(NlogN)+O(N)=O(NlogN).
#4 INTERVIEW QUESTION – REVERSING AN ARRAY
The problem is that we have to reverse a T[] array in O(N) linear running time complexity and we want to make sure the algorithm is in-place (so there is no need for extra memory). So if the input is [1,2,3,4,5] then the output should be [5,4,3,2,1].
The naive solution would be to allocate a new array and copy the items one by one but in reverse order. But this algorithm would not be in-place because we need another array.
So a better approach is to track the first item of the array with index startIndex and the last item of the array with index endIndex. We keep swapping item startIndex and endItem until we hit the middle item (which is in its final position). We hit the middle item when the two pointers are pointing to the same array slot.

It is quite a fast algorithm because we just have to consider N/2 items so the running time complexity is O(N). And as you can see there is no need for extra memory which means the algorithm is in-place.
#5 INTERVIEW QUESTION – MIDDLE NODE IN LINKED LIST
Another crucial programming interview question has something to do with linked lists. How to find the middle node of a linked list in O(N) linear running time and without the need for extra memory? The naive approach is to consider all nodes in the list but we can do better with 2pointers (references).
Let’s use 2 references: both of them are pointing to the first node at the beginning. The first pointer traverses the linked list one node at a time. But the second pointer traverses the linked list two nodes at a time. Which means it is twice as fast as the first one. When the second pointer hits the last node the first pointer points to the middle node.

What about the implementation? We just have to create 2 pointers accordingly. When the faster pointer reaches the last node in the linked list: we return with the node where the slower pointer is pointing to.

public Node getMiddleNode() {

   Node fastPointer = this.head;
   Node slowPointer = this.head;

   while(fastPointer.getNextNode() != null && fastPointer.getNextNode().getNextNode() != null) {
      fastPointer = fastPointer.getNextNode().getNextNode();
      slowPointer = slowPointer.getNextNode();
   }

   return slowPointer;
}
#6 INTERVIEW QUESTION – REVERSE LINKED LIST
Reversing a linked list is a common programming related interview question again. How to do it exactly? We just have to update the references. We need to store a pointer (reference) to the actual node, one pointer to the previous node and one final pointer to the next node. If we have these references then we just have to consider every node in the linked list and update the references accordingly.

public void reverse() {

        Node currentNode = this.head;
        Node previousNode = null;
        Node nextNode = null;

        while(currentNode!=null) {
           nextNode = currentNode.getNextNode();
           currentNode.setNextNode(previousNode);
           previousNode = currentNode;
           currentNode = nextNode;
        }

        this.head = previousNode;
}
So we just have to create 3 references: currentNode, previousNode and nextNode. The algorithm terminates when the currentNode is pointing to a null. In every iteration we have to update the references as in the animation.
As you can see this implementation has O(N) linear running time complexity which is quite favourable. And whats more important this implementation does not need extra memory (except for the 3 references but this complexity does not depend on N – it has the value 3 so a constant).
#6 INTERVIEW QUESTION – HEAP PROPERTIES
The last common programming interview question has something to do with heap data structures. If this is the first time you meet with heaps I suggest taking a look at this article. Heaps are basically tree like structures but unlike binary search trees there are order as far as the children are concerned.
Of course there are some rules. These rules are called heap-properties:
completeness: we construct heaps from left to right accross each row. There are no missing values (binary search trees may have missing values). Of course the last row may not be completely full.
every node can have 2 children: left child and right child
max heap: the parent node is alway greater than the values of the children (but the children are not necessarily ordered). It means the root node is the item with maximum value.
So this is a heap: in a max heap the root node has the largest value. The parent node is always greater than the children. We can represent a heap with the help of a simple one-dimensional array. The root node has index 0. The left child has index 2*i+1 and the right child’s index is 2*i+2.
So what about the interview question? The problem is that we have to check whether a given heap is valid or not (so the heap properties are not violated). We just have to check whether the parent node is greater than the children. And basically thats all.
How many items we have to consider? We know for sure that leaf nodes do not have children at all. So we have to check the nodes where 2*i+2≤N where N is the size of the array. Otherwise we would check the children of leaf nodes.

public boolean isMaxHeap(int[] heap) {

        //if node with index i -> 2*i+2>=N then we know it is a leaf node and
        //there is no need to check leaf nodes. So there are (N-2)/2 non leaf nodes
        //we have to consider and check
        for(int i=0;i<=(heap.length-2)/2;i++){
            //if the left child or right child is greater than the parent: the heap
            //properties are violated so return false
            if(heap[i]<heap[2*i+1] || heap[i]<heap[2*i+2])
               return false;
        }

        return true;
}
\What is running time complexity of this algorithm? We have to check (N-2)/2 nodes which means this algorithm has O(N) linear running time complexity. We can check (without the need for extra memory) whether a heap is valid or not in linear time.