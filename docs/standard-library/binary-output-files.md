---
title: 二进制输出文件 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdb101620b1a61f3a29057ee408cf9e89d38f9e8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="binary-output-files"></a>二进制输出文件

流最初专为文本设计，因此默认输出模式为文本。 在文本模式下，换行符 (十六进制 10) 将扩展到回车换行符 （仅限 16 位）。 扩展可能会引发如下所示的问题：

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

你可能希望此程序输出字节序列 { 99, 0, 10, 0 }；相反，它输出了 { 99, 0, 13, 10, 0 }，从而导致程序预测二进制输入的问题。 如果需要真正的二进制输出，其中写入的字符未经转译，则可以使用 [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) 构造函数 openmode 参数指定二进制输出：

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>请参阅

[输出流](../standard-library/output-streams.md)<br/>
