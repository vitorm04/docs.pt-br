---
title: "Enumeração CorUnmanagedCallingConvention"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorUnmanagedCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnmanagedCallingConvention
helpviewer_keywords: CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f66cb036de8450d4c1b3431b92487260956d47f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a>Enumeração CorUnmanagedCallingConvention
Especifica as convenções de chamada para código não gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|A convenção de chamada de idioma de C.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|A convenção de chamada padrão.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|A "this" convenção de chamada.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|A convenção de chamada "rápida".|  
|`IMAGE_CEE_CS_CALLCONV_C`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Não usado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR não dá suporte a convenção de chamada "rápida" no .NET Framework versão 1.0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
