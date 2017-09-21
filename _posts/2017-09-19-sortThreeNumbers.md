---
layout: post
title: Thuật toán sắp xếp 3 số nguyên theo thứ tự giảm dần
tags: [chuyencoding]
author: von
comments: yes
---

 Sắp xếp 3 số nguyên bằng cách sử dụng câu lệnh rẽ nhánh :

```cpp
#include <iostream>

using namespace std;

int main()
{
    int num1, num2, num3 ;
    int swap ;
    cin >> num1 >> num2 >> num3 ;

    // đổi chỗ số lớn nhất lên đầu

    if (num1 < num2)
    {
        swap = num1 ;
        num1 = num2 ;
        num2 = swap ;
    }
    if (num1 < num3)
    {
        swap = num1 ;
        num1 = num3 ;
        num3 = swap ;
    }

    // đổi chỗ 2 số còn lại

    if (num2 < num3)
    {
        swap = num2 ;
        num2 = num3 ;
        num3 = swap ;
    }
    cout<< num1 << " " << num2 << " " << num3 ;
    return 0;
}

```
