---
layout: post
title: Thuật toán sắp xếp 3 số nguyên theo thứ tự giảm dần
tags: [chuyencoding]
description: >
  Sắp xếp 3 số nguyên bằng cách sử dụng câu lệnh rẽ nhánh.
author: von
comments: yes
---



```cpp
#include <iostream>

using namespace std;

int main()
{
    int num1, num2, num3 ;
    int change_num ;
    cin >> num1 >> num2 >> num3 ;

    // đổi chỗ số lớn nhất lên đầu

    if (num1 < num2)
    {
        change_num = num1 ;
        num1 = num2 ;
        num2 = change_num ;
    }
    if (num1 < num3)
    {
        change_num = num1 ;
        num1 = num3 ;
        num3 = change_num ;
    }

    // đổi chỗ 2 số còn lại

    if (num2 < num3)
    {
        change_num = num2 ;
        num2 = num3 ;
        num3 = change_num ;
    }
    cout<< num1 << " " << num2 << " " << num3 ;
    return 0;
}

```
