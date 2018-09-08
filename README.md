# C Boolean Value

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](#) 
[![Coverage Status](https://img.shields.io/badge/coverage-95%25-green.svg)](https://coveralls.io/r/Snaipe/libcsptr?branch=master)
![Build Status](https://img.shields.io/badge/status-stable-brightgreen.svg)
[![dependencies](https://img.shields.io/badge/dependencies-up%20to%20date-yellowgreen.svg)](#) 
[![size](https://img.shields.io/badge/code%20size-31%20B-blue.svg)](#) 
[![usedby](https://img.shields.io/badge/used%20by-0%20projects-brightgreen.svg)](#) 
[![downloads](https://img.shields.io/badge/downloads-0k%2Fmonth-green.svg)](#) 
[![standard](https://img.shields.io/badge/standard-%3E%3DANSI-green.svg)](#) 
[![Version](https://img.shields.io/badge/version-v1.0-blue.svg)](https://github.com/lduck11007/cBoolType/releases)
[![License](https://img.shields.io/badge/License-WTFPL-blue.svg)](https://github.com/lduck11007/cBoolType/blob/master/LICENSE)

## What this is

This project is an attempt to bring 'true' and 'false' values to the (GCC) C Programming language. This project may work in C++, but no testing has been done.

## Motivations

One of the major factors preventing newer programmers from adopting C is its lack of similarity with higher level languages and constructs. The most noticable difference between C and these more modern languages is likely its lack of reserved `true` and `false` values. By making this, I hope to draw more people to use the C Programming Language.

## Features

*  `True` value
* `False` value

## Installing 

This library can be installed a number of ways.

### Git

```bash
git clone https://github.com/lduck11007/c-bool-value.git
cp c-bool-value/src/cboolvalue.h cboolvalue.h
rm -rf c-bool-value
```

### Curl

```bash
curl https://raw.githubusercontent.com/lduck11007/c-bool-value/master/src/cboolvalue.h > cboolvalue.h
```

### Windows CMD

Create a file labled `get.bat` with the following:

```batch
@Echo OFF
SetLocal EnableDelayedExpansion
Set Var=%1
Set Var=!Var:http://=!
Set Var=!Var:/=,!
Set Var=!Var:%%20=?!
Set Var=!Var: =?!
Call :LOOP !var!
Echo.Downloading: %1 to %~p0!FN!
powershell.exe -Command (new-object System.Net.WebClient).DownloadFile('%1','%~p0!FN!')
GoTo :EOF
:LOOP
If "%1"=="" GoTo :EOF
Set FN=%1
Set FN=!FN:?= !
Shift
GoTo :LOOP
```

In cmd in the same directory or with `PATH` configured, type

```bash
get https://raw.githubusercontent.com/lduck11007/c-bool-value/master/src/cboolvalue.h
```

### Examples

A simple function that returns true or false depending on whether an item is in an array

```c
#include "cboolvalue.h"

int search(char values[], int len, char searchfor){
    int search_at = 0;
    int search_res = false;
    while(search_at < len && search_res == false){
        if(values[search_at] == searchfor)
            search_res = true;
        else
            search_at += 1;
    }
    return search_res;
}
```

For power users and kernel hackers, this can be rewritten as follows for far easier readability.

```c
#include "cboolvalue.h"
#define bool int                    //TODO: learn how typedef works

int search(char values[], int len, char searchfor){
    int search_at = 0;
    bool search_res = false;
    while(search_at < len && search_res == false){
        if(values[search_at] == searchfor)
            search_res = true;
        else
            search_at += 1;
    }
    return search_res;
}
```

It's plain to see that this program is now far easier to read for a programmer of any skill level, and is practically self-documenting.
