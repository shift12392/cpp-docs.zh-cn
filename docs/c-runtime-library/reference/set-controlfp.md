---
title: _set_controlfp | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_controlfp
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_controlfp
- _set_controlfp
dev_langs:
- C++
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2647e9719c2aa3fe303393fcc1da55de0385581
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="setcontrolfp"></a>_set_controlfp

设置浮点控制字。

## <a name="syntax"></a>语法

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>参数

*newControl*<br/>
新的控制字位值。

*掩码*<br/>
要设置的新控制字位掩码。

## <a name="return-value"></a>返回值

无。

## <a name="remarks"></a>备注

**_Set_controlfp**函数是类似于 **_control87**，但它仅将浮点控制字设置为*newControl*。 值中的位表示浮点控制状态。 浮点控制状态允许程序在浮点数学包中更改精度、舍入和无穷模式。 你也可以屏蔽或取消屏蔽浮点异常使用 **_set_controlfp**。 有关详细信息，请参阅 [_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)。

使用编译时，此函数已弃用[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)因为公共语言运行时仅支持默认的浮点精度。

## <a name="requirements"></a>要求

|例程|必需的标头|兼容性|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|仅限 x86 处理器|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
