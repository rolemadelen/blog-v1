---
title: 'Doubly Linked List'
posttitle: 'Linked List'
postsubtitle: 'Part 03: Doubly Linked List'
date: '2022-07-31 17:50:00'
updated: '2022-10-24 06:00:00'
tags:
  - linked list
lang: en
about: dev
---

# What is a Doubly Linked List?

A **doubly linked list** is a linear collection of data elements in which the order of the element is determined not by its physical address in the memory, but by references (or links) each element points to.

![Doubly Linked List](/images/posts/linked-list/doubly-linked-list.svg)

The structure of the element or a node in a doubly linked list consists of a data and two references: `previous` and `next`. Having two references -- `preivous` and `next` allows for simpler insertion and removal of elements in any position in the list. Also we can easily traverse the list in reverse order.

Drawback of using doubly linked list is that it consumes more memory because of the extra information in the node.

## Complexity

| Space | Access | Search | Insertion | Deletion |
| :---: | :----: | :----: | :-------: | :------: |
| O(n)  |  O(n)  |  O(n)  |   O(1)    |   O(n)   |

## Pseudocode of Basic Operations

Click [here](https://github.com/rolemadelen/typescript-algorithms/blob/main/src/data-structures/doubly-linked-list/DoublyLinkedList.ts) to view the full source code Doubly Linked List implementation.

### prepend

```text
prepend(head, tail, value) → void
    Pre: head is the 1st node in the list
         tail is the last node in the list
         value is the value we're going to insert
    Post: a new node has been inserted at the head of the list

    n      ← Node(value)
    n.next ← head

    IF (head != ø)
        head.prev ← n
    END IF

    IF (tail == ø)
        tail ← n
    END IF

    head ← n
END prepend
```

### append

```text
append(head, tail, value) → void
    Pre: head is the 1st node in the list
         tail is the last node in the list
         value is the value we're going to insert in the list
    Post: a new node has been inserted at the end of the list

    n      ← Node(value)
    n.prev ← tail

    IF (tail != ø)
        tail.next ← n
    END IF
    tail ← n

    IF (head == ø)
        head ← n
    END IF
END append
```

### deleteHead

```text
deleteHead(head, tail, del) → Node
    Pre: head is the first node in the list
         tail is the last node in the list
         del stores a node to be deleted
    Post: head has been replaced

    del ← ø

    IF (head == tail)
        del  ← head
        head ← ø
        tail ← ø
    ELSE IF (head != ø)
        del       ← head
        head      ← head.next
        head.prev ← ø
    END IF

    return del
END
```

### deleteTail

```text
deleteTail(head, tail, del) → Node
    Pre: head is the first node in the list
         tail is the last node in the list
         del stores a node to be deleted
    Post: tail has been replaced

        del ← ø

    IF (tail == head)
        del  ← tail
        head ← ø
        tail ← ø
    ELSE IF (tail != ø)
        del       ← head
        tail      ← tail.prev
        tail.next ← ø
    END IF

    return del
END
```

### delete

```text
delete(head, tail, value) → Node | ø
    Pre: head is the 1st node in the list
         tail is the last node in the list
         value is the value we're going to remove from the list
    Post: a node is removed from the list and returned; otherwise, return ø

    // FIND returns the node with a given value or ø
    node ← find(value)

    IF (node)
        IF (node.prev && node.next)
            node.prev.next ← node.next;
            node.next.prev ← node.prev;
            return node;
        ELSE IF (node == head && node == tail)
            head ← ø
            tail ← ø
        ELSE IF (node == head)
            head       ← head.next
            head?.prev ← ø
        ELSE IF (node == tail)
            tail       ← tail.prev
            tail?.next ← ø
        END IF
    END IF

    return node
END delete
```

### Reverse Traversal

```text
reverseTraversal(tail)
    Pre: tail points to the last node in the list
    Post: a list has been traversed in reverse order

    n ← tail
    WHILE (n != ø)
        print n.value
        n ← n.prev
    END WHILE
END reverseTraversal
```

## Problems

Linked list related problems selected from [Leetcode](https://leetcode.com/tag/linked-list/).

|       #       | Problem                                           | Difficulty |
| :-----------: | :------------------------------------------------ | :--------- |
|    [2][i2]    | Add Two Numbers                                   | Medium     |
|   [19][i19]   | Remove Nth Node From End of List                  | Medium     |
|   [21][i21]   | Merge Two Sorted Lists                            | Easy       |
|   [23][i23]   | Merge k Sorted Lists                              | Hard       |
|   [83][i83]   | Remove Duplicates from Sorted List                | Easy       |
|  [141][i141]  | Linked List Cycle                                 | Easy       |
|  [146][i146]  | LRU Cache                                         | Medium     |
|  [160][i160]  | Intersection of Two Linked Lists                  | Easy       |
|  [203][i203]  | Remove Linked List Elements                       | Easy       |
|  [206][i206]  | Reverse Linked List                               | Easy       |
|  [234][i234]  | Palindrome Linked List                            | Easy       |
|  [237][i237]  | Delete Node in a Linked List                      | Easy       |
|  [432][i432]  | All O`one Data Structure                          | Hard       |
|  [876][i876]  | Middle of the Linked List                         | Easy       |
| [1206][i1206] | Convert Binary Number in a Linked List to Integer | Easy       |
| [1290][i1290] | Design Skiplist                                   | Hard       |
| [1669][i1669] | Merge In Between Linked Lists                     | Medium     |
| [2181][i2181] | Merge Nodes in Between Zeros                      | Medium     |

[i2]: https://leetcode.com/problems/add-two-numbers/
[i19]: https://leetcode.com/problems/remove-nth-node-from-end-of-list/
[i21]: https://leetcode.com/problems/merge-two-sorted-lists/
[i23]: https://leetcode.com/problems/merge-k-sorted-lists/
[i83]: https://leetcode.com/problems/remove-duplicates-from-sorted-list/
[i141]: https://leetcode.com/problems/linked-list-cycle/
[i146]: https://leetcode.com/problems/lru-cache/
[i160]: https://leetcode.com/problems/intersection-of-two-linked-lists/
[i203]: https://leetcode.com/problems/remove-linked-list-elements/
[i206]: https://leetcode.com/problems/reverse-linked-list/
[i234]: https://leetcode.com/problems/palindrome-linked-list/
[i237]: https://leetcode.com/problems/delete-node-in-a-linked-list/
[i432]: https://leetcode.com/problems/all-oone-data-structure/
[i876]: https://leetcode.com/problems/middle-of-the-linked-list/
[i1206]: https://leetcode.com/problems/convert-binary-number-in-a-linked-list-to-integer/
[i1290]: https://leetcode.com/problems/design-skiplist/
[i1669]: https://leetcode.com/problems/merge-in-between-linked-lists/
[i2181]: https://leetcode.com/problems/merge-nodes-in-between-zeros/

## See also

- [What is a Linked List](./what-is-a-linked-list)
- [Singly Linked List](./singly-linked-list)
- [Circular Linked List](./circular-linked-list)
