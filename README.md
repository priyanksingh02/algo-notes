# Topics

## Linked List

### Middle element

```cpp
// 1 2 [3] 4 5
// 1 2 3 [4] 5 6
ListNode * mid(ListNode * head) {
    if(!head) return head;
    auto fast = head;
    auto slow = head;
    while(fast and fast->next) {
        fast = fast->next->next;
        slow = slow->next;
    }
    return slow;
}

// 1 2 [3] 4 5
// 1 2 [3] 4 5 6
ListNode * mid(ListNode * head) {
    if(!head or !head->next) return head;
    auto fast = head;
    auto slow = head;
    while(fast and fast->next and fast->next->next) {
        fast = fast->next->next;
        slow = slow->next;
    }
    return slow;
}

```

### Reverse List

```cpp
// Iterative
ListNode * rev(ListNode * head) {
    ListNode * ans;
    while(head) {
        auto tmp = head;
        head = head->next;
        tmp->next = ans;
        ans = tmp;
    }
    return ans;
}

// Recursive
ListNode * rev(ListNode * head) {
    if(!head or !head->next) return head;
    auto newhead= rev(head->next);
    head->next->next = head;
    head->next = nullptr;
    return newhead;
}
```

### Cycle 

```cpp
bool cycle(ListNode * head) {
    if(!head) return false;
    auto fast = head;
    auto slow = head;
    while(fast and fast->next) {
        fast = fast->next->next;
        slow = slow->next;
        if(fast == slow)
            return true;
    }
    return false;
}