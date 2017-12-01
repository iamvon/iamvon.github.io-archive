---
layout: post
title: Tính toán với số nguyên rất lớn - phép Cộng (Phần 1)
tags: [chuyencoding]
description: >
  Series bài viết về các phép toán thực hiện với các số nguyên rất lớn (Code C++)
author: von
---
```cpp
#include <bits/stdc++.h>

using namespace std ;

int charToInt(char a)
{
  return int(a - '0') ;
}

char intToChar(int a)
{
  return char(a + '0') ;
}

void add(string &a, string &b)
{
  string result ;
  int sum = 0, temp = 0 ;
  int len_a = a.length() ;
  int len_b = b.length() ;
  int n ;
  if (len_a > len_b)
  {
    for(int i = 0; i < len_a - len_b; i++)
    {
      b = '0' + b ;
    }
    n = len_a ;
  }
  else
  {
    for(int i = 0; i < len_b - len_a; i++)
    {
      a = '0' + a ;
    }
    n = len_b ;
  }

  for(int i = n - 1; i >= 0; i--)
   {
      sum = (charToInt(a[i]) + charToInt(b[i]) + temp) % 10 ;
      temp = (charToInt(a[i]) + charToInt(b[i]) + temp) / 10 ;
      result = intToChar(sum) + result ;
   }
   cout << endl ;
   cout << result ;
}

int main()
{
    string a, b ;
    cin >> a >> b ;
    add(a,b) ;
    return 0;
}

```
