---
layout: post
title: Tính toán với số nguyên rất lớn - phép Trừ (Phần 1)
tags: [chuyencoding]
description: >
  Series bài viết về các phép toán thực hiện với các số nguyên rất lớn (Code C++)
author: von
---
Phép trừ 2 số nguyên dương rất lớn (a > b):                    

```cpp
include <bits/stdc++.h>

using namespace std ;

int charToInt(char a)
{
  return int(a - '0') ;
}

char intToChar(int a)
{
  return char(a + '0') ;
}

void sub(string &a, string &b)
{
  string result ;
  int digit = 0, temp = 0 ;
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
      if (charToInt(a[i]) >= charToInt(b[i]))
      {
        digit = charToInt(a[i]) - (charToInt(b[i]) + temp) ;
        temp = 0 ;
        result = intToChar(digit) + result ;
      }
      else if (charToInt(a[i]) < charToInt(b[i]))
      {
        digit = ((charToInt(a[i])+10) - (charToInt(b[i]) + temp))%10 ;
        temp = 1 ;
        result = intToChar(digit) + result ;
      }
   }
   cout << endl ;
   cout << result ;
}

int main()
{
    string a, b ;
    cin >> a >> b ;
    sub(a,b) ;
    return 0;
}
```
