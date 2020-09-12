---
title: 数组中重复的数字-剑指offer
date: 2020-09-11 20:31:41
tags:
 -数组
 -剑指offer
 -牛客网
categories: 剑指offer
---

# 数组中重复的数字

## description

 在一个长度为n的数组里的所有数字都在0到n-1的范围内。 数组中某些数字是重复的，但不知道有几个数字是重复的。也不知道每个数字重复几次。请找出数组中任意一个重复的数字。 例如，如果输入长度为7的数组{2,3,1,0,2,5,3}，那么对应的输出是第一个重复的数字2。 



<!--more-->



## solution



0到n-1共n个元素，元素取值范围为0到n-1，如果没有重复元素，排序完则numbers[i] = i;如果当前

i的位置的值已经与i相等，即numbers[i] = i，再出现一个number与i相等，则认为该numbers为重复值。

```java
public class Solution {
    // Parameters:
    //    numbers:     an array of integers
    //    length:      the length of array numbers
    //    duplication: (Output) the duplicated number in the array number,length of duplication array is 1,so using duplication[0] = ? in implementation;
    //                  Here duplication like pointor in C/C++, duplication[0] equal *duplication in C/C++
    //    这里要特别注意~返回任意重复的一个，赋值duplication[0]
    // Return value:       true if the input is valid, and there are some duplications in the array number
    //                     otherwise false
    public boolean duplicate(int numbers[],int length,int [] duplication) {
        int i;
        for(i = 0; i < length; i++ ) {
            while(numbers[i] != i) {
                if(numbers[i] == numbers[numbers[i]]) {
                    duplication[0] = numbers[i];
                    return true;
                }
                int t = numbers[numbers[i]];
                numbers[numbers[i]] = numbers[i];
                numbers[i] = t;
                /*在写交换数组元素代码时，不能写成
                int t = numbers[i];
                numbers[i] = numbers[numbers[i]];
                numbers[numbers[i]] = t;
                因为第二行的numbers[i]已经发生改变，不再是之前的数值，所以会时间超限
                */
                
            }
        }
        return false;
    }
}
```

