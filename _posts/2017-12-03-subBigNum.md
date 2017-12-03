---
layout: post
title: Tính toán với số nguyên rất lớn - phép Trừ (Phần 2)
tags: [chuyencoding]
description: >
  Series bài viết về các phép toán thực hiện với các số nguyên rất lớn (Code C++)
author: von
---
Phép trừ 2 số nguyên dương rất lớn (a - b) :                    

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

void removeZeroSuperfluous(string &input)
{
  int n = input.length(), i = 0 ;
  while(i < n)
  {
    if(input[i] != '0')
    {
      break ;
    }
    input.erase(0,1) ;
  }
}

string returnSubResult(string &longer, string &shorter, int n)
{
  int temp = 0, digit = 0 ;
  string result ;
  for(int i = n - 1; i >= 0; i--)
   {
      if (charToInt(longer[i]) > charToInt(shorter[i]))
      {
        digit = charToInt(longer[i]) - charToInt(shorter[i]) ;
        temp = 0 ;
        result = intToChar(digit) + result ;
        shorter[i-1] = intToChar(charToInt(shorter[i-1]) + temp) ;
      }
      else if (charToInt(longer[i]) < charToInt(shorter[i]))
      {
        digit = ((charToInt(longer[i])+10) - charToInt(shorter[i]))%10 ;
        temp = 1 ;
        result = intToChar(digit) + result ;
        shorter[i-1] = intToChar(charToInt(shorter[i-1]) + temp) ;
      }
      else
      {
        digit = charToInt(longer[i]) - charToInt(shorter[i]) ;
        temp = 0 ;
        result = intToChar(digit) + result ;
      }
   }
   removeZeroSuperfluous(result) ;
   return result ;
}

void sub(string &a, string &b)
{
  removeZeroSuperfluous(a) ;
  removeZeroSuperfluous(b) ;
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
     result = returnSubResult(a,b,n) ;
     cout << endl ;
     cout << result ;
  }
  else if (len_a < len_b)
  {
    for(int i = 0; i < len_b - len_a; i++)
    {
      a = '0' + a ;
    }
    n = len_b ;
     result = returnSubResult(b,a,n) ;
     cout << endl ;
     cout << '-' + result ;
  }

else
{
  int check = 0 ; // suppose a > b
  n = len_a ;
  // check whether b > a or not
  for(int i = 0; i < n; i++)
  {
    if(charToInt(b[i]) > charToInt(a[i]))
    {
      check = 1 ; // b > a
      break ;
    }
    else if(charToInt(b[i]) < charToInt(a[i]))
    {
      break ; // a > b
    }
  }
  if (check == 0)
  {
   result = returnSubResult(a,b,n) ;
   cout << endl ;
   cout << result ;
 }
 else if (check == 1)
 {
    result = returnSubResult(b,a,n) ;
    cout << endl ;
    cout << '-' + result ;
 }
}
}

int main()
{
    string a, b ;
    cin >> a >> b ;
    sub(a,b) ;
    return 0;
}
```
