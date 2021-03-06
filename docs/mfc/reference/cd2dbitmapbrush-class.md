---
title: CD2DBitmapBrush 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8fb0833fc82895f1f32fb5c93a6e6519bfe119c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush 类
ID2D1BitmapBrush 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|已重载。 构造 CD2DBitmapBrush 对象文件中。|  
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|析构函数。 当 D2D 位图画笔对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DBitmapBrush::Create](#create)|创建 CD2DBitmapBrush。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DBitmapBrush::Destroy](#destroy)|销毁 CD2DBitmapBrush 对象。 (重写[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|  
|[CD2DBitmapBrush::Detach](#detach)|分离资源接口从该对象|  
|[CD2DBitmapBrush::Get](#get)|返回 ID2D1BitmapBrush 接口|  
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|获取用于绘制此画笔的位图源|  
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|获取依据画笔水平平铺的那些区域的超出其位图的方法|  
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|获取依据画笔垂直平铺的那些区域的超出其位图的方法|  
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|获取缩放或旋转画笔位图时使用的内插方法|  
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|指定用于绘制此画笔的位图源|  
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|指定如何画笔水平平铺的那些区域的超出其位图|  
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|指定如何画笔垂直平铺的那些区域的超出其位图|  
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|指定使用缩放或旋转画笔位图时的内插模式|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](#commoninit)|初始化对象|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|返回 ID2D1BitmapBrush 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|将存储指向 CD2DBitmap 对象的指针。|  
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|将存储指向 ID2D1BitmapBrush 对象的指针。|  
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|位图画笔属性。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 `CD2DBitmapBrush`  
  
## <a name="requirements"></a>要求  
 **标头：** afxrendertarget.h  
  
##  <a name="dtor"></a>  CD2DBitmapBrush:: ~ CD2DBitmapBrush  
 析构函数。 当 D2D 位图画笔对象被销毁时调用。  
  
```  
virtual ~CD2DBitmapBrush();
```  
  
##  <a name="attach"></a>  CD2DBitmapBrush::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1BitmapBrush* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源接口。 不能为 NULL  
  
##  <a name="cd2dbitmapbrush"></a>  CD2DBitmapBrush::CD2DBitmapBrush  
 构造 CD2DBitmapBrush 对象。  
  
```  
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszImagePath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,  
    CD2DBrushProperties* pBrushProperties = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `pBitmapBrushProperties`  
 一个指向扩展模式和位图画笔的插补模式。  
  
 `pBrushProperties`  
 指向不透明度和画笔的转换的指针。  
  
 `bAutoDestroy`  
 指示该对象将销毁所有者 (pParentTarget)。  
  
 `uiResID`  
 资源的资源 ID 号。  
  
 `lpszType`  
 指向以 null 结尾的字符串，包含的资源类型的指针。  
  
 `sizeDest`  
 位图的目标大小。  
  
 `lpszImagePath`  
 指向以 null 结尾的字符串包含文件的名称。  
  
##  <a name="commoninit"></a>  CD2DBitmapBrush::CommonInit  
 初始化对象  
  
```  
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```  
  
### <a name="parameters"></a>参数  
 `pBitmapBrushProperties`  
 指向位图画笔属性的指针。  
  
##  <a name="create"></a>  CD2DBitmapBrush::Create  
 创建 CD2DBitmapBrush。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 指向该呈现器目标的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="destroy"></a>  CD2DBitmapBrush::Destroy  
 销毁 CD2DBitmapBrush 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DBitmapBrush::Detach  
 分离资源接口从该对象  
  
```  
ID2D1BitmapBrush* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向分离的资源接口指针。  
  
##  <a name="get"></a>  CD2DBitmapBrush::Get  
 返回 ID2D1BitmapBrush 接口  
  
```  
ID2D1BitmapBrush* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1BitmapBrush 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="getbitmap"></a>  CD2DBitmapBrush::GetBitmap  
 获取用于绘制此画笔的位图源  
  
```  
CD2DBitmap* GetBitmap();
```  
  
### <a name="return-value"></a>返回值  
 到 CD2DBitmap 对象或 NULL 如果尚未初始化对象的指针。  
  
##  <a name="getextendmodex"></a>  CD2DBitmapBrush::GetExtendModeX  
 获取依据画笔水平平铺的那些区域的超出其位图的方法  
  
```  
D2D1_EXTEND_MODE GetExtendModeX() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，指定如何画笔水平平铺的那些区域的超出其位图  
  
##  <a name="getextendmodey"></a>  CD2DBitmapBrush::GetExtendModeY  
 获取依据画笔垂直平铺的那些区域的超出其位图的方法  
  
```  
D2D1_EXTEND_MODE GetExtendModeY() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个值，指定如何画笔垂直平铺的那些区域的超出其位图  
  
##  <a name="getinterpolationmode"></a>  CD2DBitmapBrush::GetInterpolationMode  
 获取缩放或旋转画笔位图时使用的内插方法  
  
```  
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 使用缩放或旋转画笔位图时的内插方法  
  
##  <a name="m_pbitmap"></a>  CD2DBitmapBrush::m_pBitmap  
 将存储指向 CD2DBitmap 对象的指针。  
  
```  
CD2DBitmap* m_pBitmap;  
```  
  
##  <a name="m_pbitmapbrush"></a>  CD2DBitmapBrush::m_pBitmapBrush  
 将存储指向 ID2D1BitmapBrush 对象的指针。  
  
```  
ID2D1BitmapBrush* m_pBitmapBrush;  
```  
  
##  <a name="m_pbitmapbrushproperties"></a>  CD2DBitmapBrush::m_pBitmapBrushProperties  
 位图画笔属性。  
  
```  
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;  
```  
  
##  <a name="operator_id2d1bitmapbrush_star"></a>  CD2DBitmapBrush::operator ID2D1BitmapBrush *  
 返回 ID2D1BitmapBrush 接口  
  
```  
operator ID2D1BitmapBrush*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1BitmapBrush 接口或如果尚未初始化对象的 NULL 指针。  
  
##  <a name="setbitmap"></a>  CD2DBitmapBrush::SetBitmap  
 指定用于绘制此画笔的位图源  
  
```  
void SetBitmap(CD2DBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
 `pBitmap`  
 使用画笔的位图源  
  
##  <a name="setextendmodex"></a>  CD2DBitmapBrush::SetExtendModeX  
 指定如何画笔水平平铺的那些区域的超出其位图  
  
```  
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```  
  
### <a name="parameters"></a>参数  
 `extendModeX`  
 一个值，指定如何画笔水平平铺的那些区域的超出其位图  
  
##  <a name="setextendmodey"></a>  CD2DBitmapBrush::SetExtendModeY  
 指定如何画笔垂直平铺的那些区域的超出其位图  
  
```  
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```  
  
### <a name="parameters"></a>参数  
 `extendModeY`  
 一个值，指定如何画笔垂直平铺的那些区域的超出其位图  
  
##  <a name="setinterpolationmode"></a>  CD2DBitmapBrush::SetInterpolationMode  
 指定使用缩放或旋转画笔位图时的内插模式  
  
```  
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```  
  
### <a name="parameters"></a>参数  
 `interpolationMode`  
 使用缩放或旋转画笔位图时的内插模式  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
