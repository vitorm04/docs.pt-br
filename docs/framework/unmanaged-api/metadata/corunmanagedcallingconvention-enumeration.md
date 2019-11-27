---
title: Enumeração CorUnmanagedCallingConvention
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: 58d30e71929d314ee36adb9f83270858ff8a161b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442442"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>Enumeração CorUnmanagedCallingConvention
Especifica as convenções de chamada para código não gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|A Convenção de chamada de linguagem C.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|A Convenção de chamada padrão.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|A Convenção de chamada "This".|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|A Convenção de chamada "Fast".|  
|`IMAGE_CEE_CS_CALLCONV_C`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Não usado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR não oferece suporte à Convenção de chamada "rápida" no .NET Framework versão 1,0.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
