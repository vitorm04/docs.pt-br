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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff308a81282a1cc14c35583daf9cbb057149e556
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178445"
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
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|A convenção de chamada do idioma do C.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|A convenção de chamada padrão.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|A "this" convenção de chamada.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|A convenção de chamada "rápida".|  
|`IMAGE_CEE_CS_CALLCONV_C`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Não usado.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Não usado.|  
  
## <a name="remarks"></a>Comentários  
 O CLR não oferece suporte a convenção de chamada "rápida" no .NET Framework versão 1.0.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
