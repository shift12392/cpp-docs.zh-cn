---
title: delete 运算符 （C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- delete_cpp
dev_langs:
- C++
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3b523f5c10cbd28dfb2d584ea8241bc1518cf925
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="delete-operator-c"></a>delete 运算符 (C++)
释放内存块。  
  
## <a name="syntax"></a>语法  
  
```  
[::] delete cast-expression  
[::] delete [ ] cast-expression  
```  
  
## <a name="remarks"></a>备注  
 *cast-expression*参数必须是指向以前使用[new 运算符](../cpp/new-operator-cpp.md)创建对象时分配的内存块。 **删除**运算符的结果类型为`void`，因此不会返回一个值。 例如：  
  
```  
CDialog* MyDialog = new CDialog;  
// use MyDialog  
delete MyDialog;  
```  
  
 如果一个对象不是**new**出来的，使用**delete**销毁它，其行为不可预知。 但是，你可以使用**delete**值 0 的指针。 此设置意味着，当**new**在失败时，删除失败的结果都返回 0**新**操作不会造成损害。 请参阅[新和 delete 运算符](../cpp/new-and-delete-operators.md)有关详细信息。  
  
 **新**和**删除**运算符可以还用于内置类型，包括数组。 如果 `pointer` 指的是某一数组，请在 `pointer` 前放置空括号：  
  
```  
int* set = new int[100];  
//use set[]  
delete [] set;  
```  
  
 使用**删除**对象上的运算符将释放其内存。 在删除对象后取消引用指针的程序可能会产生不可预知的结果或崩溃。  
  
 当**删除**是用于释放 C++ 类对象的内存，该对象的析构函数之前调用 （如果该对象具有析构函数），将释放该对象的内存。  
  
 如果操作数**删除**运算符是一个可修改的左值，删除该对象后，其值未定义。  
  
## <a name="using-delete"></a>使用 delete  
 有两个语法变体[delete 运算符](../cpp/delete-operator-cpp.md)： 一个针对单一对象，另一个用于对象的数组。 以下代码片段演示了它们之间的差异：  
  
```  
// expre_Using_delete.cpp  
struct UDType   
{  
};  
  
int main()  
{  
   // Allocate a user-defined object, UDObject, and an object  
   //  of type double on the free store using the  
   //  new operator.  
   UDType *UDObject = new UDType;  
   double *dObject = new double;  
   // Delete the two objects.  
   delete UDObject;  
   delete dObject;   
   // Allocate an array of user-defined objects on the  
   // free store using the new operator.  
   UDType (*UDArr)[7] = new UDType[5][7];  
   // Use the array syntax to delete the array of objects.  
   delete [] UDArr;  
}  
```  
  
 以下两种情况会生成未定义的结果：在对象中使用 delete 的数组形式 (delete [ ])，并在数组中使用 delete 的非数组形式。  
  
## <a name="example"></a>示例  
 有关使用的示例**删除**，请参阅[new 运算符](../cpp/new-operator-cpp.md)。  
  
## <a name="how-delete-works"></a>delete 的工作方式  
 Delete 运算符调用的函数**运算符 delete**。  
  
 对于不是类类型的对象 ([类](../cpp/class-cpp.md)，[结构](../cpp/struct-cpp.md)，或[联合](../cpp/unions.md))，调用全局 delete 运算符。 对于类类型的对象，如果删除表达式以一元范围解析运算符 (::) 开始，则会在全局范围中解析释放函数的名称。 否则，delete 运算符将在释放内存之前为对象调用析构函数（如果指针不为 null）。 可为每个类定义 delete 运算符；如果给定类不存在这种定义，则会调用全局 delete 运算符。 如果删除表达式用于释放其静态对象具有虚拟析构函数的类对象，则将通过对象的动态类型的虚拟析构函数解析释放函数。  
  
## <a name="see-also"></a>请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)   
 
