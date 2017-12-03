---
layout: post
title: Tính toán với số nguyên rất lớn - phép Trừ (Phần 2)
tags: [chuyencoding]
description: >
  Series bài viết về các phép toán thực hiện với các số nguyên rất lớn (Code C++)
author: von
---
Phép trừ 2 số nguyên dương rất lớn :                    

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
  else if (len_a < len_b)
  {
    for(int i = 0; i < len_b - len_a; i++)
    {
      a = '0' + a ;
    }
    n = len_b ;
    for(int i = n - 1; i >= 0; i--)
     {
        if (charToInt(b[i]) >= charToInt(a[i]))
        {
          digit = charToInt(b[i]) - (charToInt(a[i]) + temp) ;
          temp = 0 ;
          result = intToChar(digit) + result ;
        }
        else if (charToInt(b[i]) < charToInt(a[i]))
        {
          digit = ((charToInt(b[i])+10) - (charToInt(a[i]) + temp))%10 ;
          temp = 1 ;
          result = intToChar(digit) + result ;
        }
     }
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
 else if (check == 1)
 {
   for(int i = n - 1; i >= 0; i--)
    {
       if (charToInt(b[i]) >= charToInt(a[i]))
       {
         digit = charToInt(b[i]) - (charToInt(a[i]) + temp) ;
         temp = 0 ;
         result = intToChar(digit) + result ;
       }
       else if (charToInt(b[i]) < charToInt(a[i]))
       {
         digit = ((charToInt(b[i])+10) - (charToInt(a[i]) + temp))%10 ;
         temp = 1 ;
         result = intToChar(digit) + result ;
       }
    }
    cout << endl ;
    cout << '-' + result ;
 }
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
