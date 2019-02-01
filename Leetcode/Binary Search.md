# Binary Search

### <a name="index"></a>Index
 [Index](#index)
 [Edge case](#edge\ case)
 [Big sorted array](#big)
### Template
```java
start + 1 < end
mid = start + (end - start)/2
A[mid] == < >
A[start] A[end] ? target
```

### Meaning

[1,2,3,4,5,6] target =0;
[1,3]

[1,2,3,4,5,6] target = 7;
[3,6]
- ##### Left and right both less than target
- ##### Left and right both bigger than target
- ##### Left is always less or equal than the target; Right is always bigger or equal than the target

 
### Edge case
| 0      | 1 | 2     |
| :---        |    :----:   |          ---: |
| 3      | 3       | 5   |

##### 1. If the length is even, mid will choose the left one of the mid
start = 0, end = 1, mid = start + (end - start )/2 = 0

start = 0, end = 2, mid = start + (end - start )/2 = 1


start = 0, end = 3, mid = start + (end - start )/2 = 1

##### 2. (start + 1 < end) vs (start < end)
Why cannot write 
```jave
while ( start < end)
```
| 0      | 1 | 
| :---        |    :----:   | 
| 1      | 2       | 
start =0;
end = 1;
mid = 0;
start = mid = 0;
It still go into while(start < end)
loop forever!


- Example

1.
 | 0      | 1 | 2     |3|4|5|6|
| :---        |    :----:   |          ---: |         ---: |         ---: |         ---: |---: |
| 1      | 2       | 3   |3   |5   |6   |7   |
| s     | -       | -   |m   |-   |-   |e   |

--
 | 0      | 1 | 2     |3|4|5|6|
| :---        |    :----:   |          ---: |         ---: |         ---: |         ---: |---: |
| 1      | 2       | 3   |3   |5   |6   |7   |
| s     | m       | -   |e   |-   |-   |-   |

--
 | 0      | 1 | 2     |3|4|5|6|
| :---        |    :----:   |          ---: |         ---: |         ---: |         ---: |---: |
| 1      | 2       | 3   |3   |5   |6   |7   |
| -     | s       | m   |e   |-   |-   |-   |

2.

 | 0      | 1 | 2     |3|4|5|6|
| :---        |    :----:   |          ---: |         ---: |         ---: |         ---: |---: |
| 1      | 1       | 1   |1   |1   |1   |1   |
| s     | -       | -   |m   |-   |-   |e   |

--
  | 0      | 1 | 2     |3|4|5|6|
| :---        |    :----:   |          ---: |         ---: |         ---: |         ---: |---: |
| 1      | 1       | 1   |1   |1   |1   |1   |
| s     | m       | -   |e   |-   |-   |-   |

--
  | 0      | 1 | 2     |3|4|5|6|
| :---        |    :----:   |          ---: |         ---: |         ---: |         ---: |---: |
| 1      | 1       | 1   |1   |1   |1   |1   |
| s     | e       | -   |-   |-   |-   |-   |

#### Time Complexity

T(n) = T(n/2) +O (1) = O(Log(n))

Tips:

1 + 2 + 4 +8 +...+ 2^k = 2^(k+1) -1

### First position
### Last position
### Search 2d matrix
  - Search last row that [0] < target
### <a name="big"></a>Big sorted array
