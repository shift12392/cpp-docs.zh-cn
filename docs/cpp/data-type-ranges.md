---
title: "数据类型范围 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "unsigned"
  - "wchar_t"
  - "char"
  - "signed"
  - "short"
  - "long"
  - "double"
  - "float"
  - "int"
  - "long_double"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "float 关键字 [C++]"
  - "char 关键字 [C++]"
  - "unsigned long"
  - "__wchar_t 关键字 [C++]"
  - "unsigned short int"
  - "enum 关键字"
  - "无符号 char 关键字 [C++]"
  - "Integer 数据类型, 数据类型范围"
  - "int 数据类型"
  - "数据类型 [C++], 范围"
  - "unsigned int"
  - "Short 数据类型"
  - "short int 数据"
  - "有符号类型 [C + +], 数据类型范围"
  - "long long 关键字 [C++]"
  - "long double 关键字 [C++]"
  - "double 数据类型, 数据类型范围"
  - "signed short int"
  - "unsigned short"
  - "调整了大小的整型"
  - "signed int"
  - "signed long int"
  - "signed char 关键字 [C++]"
  - "wchar_t 关键字 [C++]"
  - "long 关键字 [C++]"
  - "范围 [C++]"
  - "无符号类型 [C++], 数据类型范围"
  - "浮点数字, 数据类型范围"
  - "范围 [C++], 数据类型"
  - "long int 关键字 [C++]"
  - "unsigned long int"
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# 数据类型范围
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C++ 32 位和 64 位编译器可识别本文后面的表中的类型。  
  
-   `int` (`unsigned``int`)  
  
-   `__int8` (`unsigned``__int8`)  
  
-   `__int16` (`unsigned``__int16`)  
  
-   `__int32` (`unsigned``__int32`)  
  
-   `__int64` (`unsigned``__int64`)  
  
-   `short` (`unsigned``short`)  
  
-   `long` (`unsigned``long`)  
  
-   `long` `long` (`unsigned``long``long`)  
  
 如果其名称以两个下划线 (`__`) 开始，则数据类型是非标准的。  
  
 下表中指定的范围均包含起始值和结束值。  
  
|类型名称|字节|其他名称|值的范围|  
|---------------|-----------|-----------------|---------------------|  
|int|4|signed|–2,147,483,648 到 2,147,483,647|  
|unsigned int|4|unsigned|0 到 4,294,967,295|  
|__int8|1|char|–128 到 127|  
|unsigned __int8|1|unsigned char|0 到 255|  
|__int16|2|short、short int、signed short int|–32,768 到 32,767|  
|unsigned __int16|2|unsigned short、unsigned short int|0 到 65,535|  
|__int32|4|signed、signed int、int|–2,147,483,648 到 2,147,483,647|  
|unsigned __int32|4|unsigned、unsigned int|0 到 4,294,967,295|  
|__int64|8|long long、signed long long|–9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|  
|unsigned __int64|8|unsigned long long|0 到 18,446,744,073,709,551,615|  
|bool|1|无|false 或 true|  
|char|1|无|-128 到 127（默认）<br /><br /> 0 到 255（当使用 [/J](../build/reference/j-default-char-type-is-unsigned.md) 编译时）|  
|signed char|1|无|–128 到 127|  
|unsigned char|1|无|0 到 255|  
|short|2|short int、signed short int|–32,768 到 32,767|  
|unsigned short|2|unsigned short int|0 到 65,535|  
|long|4|long int、signed long int|–2,147,483,648 到 2,147,483,647|  
|unsigned long|4|unsigned long int|0 到 4,294,967,295|  
|long long|8|无（与 __int64 等效）|–9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|  
|unsigned long long|8|无（与无符号的 __int64 等效）|0 到 18,446,744,073,709,551,615|  
|enum|varies|无|请参阅本文后面的[备注](#bkmkRemarks)|  
|浮动|4|无|3.4E +/- 38（7 位数）|  
|double|8|无|1.7E +/- 308（15 位数）|  
|long double|与 double 相同|无|与 double 相同|  
|wchar_t|2|__wchar_t|0 到 65,535|  
  
 根据使用方式，`__wchar_t` 的变量指定宽字符类型或多字节字符类型。 在字符或字符串常量前使用 `L` 前缀以指定宽字符类型常量。  
  
 `signed` 和 `unsigned` 是可用于任何整型（`bool` 除外）的修饰符。 请注意，对于重载和模板等机制而言，`char`、`signed char` 和 `unsigned char` 是三种不同的类型。  
  
 `int` 和 `unsigned``int` 类型具有四个字节的大小。 但是，由于语言标准允许可移植代码特定于实现，因此该代码不应依赖于 `int` 的大小。  
  
 Visual Studio 中的 C/C++ 还支持按大小分类的整型。 有关详细信息，请参阅 [__int8、\__int16、 \__int32、 \__int64](../cpp/int8-int16-int32-int64.md) 和 [整数限制](../cpp/integer-limits.md)。  
  
 有关每个类型的大小限制的详细信息，请参阅[基本类型](../cpp/fundamental-types-cpp.md)。  
  
 枚举类型的范围因语言上下文和指定的编译器标志而异。 有关详细信息，请参阅 [C 枚举声明](../c-language/c-enumeration-declarations.md)和[枚举](../cpp/enumerations-cpp.md)。  
  
## 另请参阅  
 [关键字](../cpp/keywords-cpp.md)   
 [基本类型](../cpp/fundamental-types-cpp.md)