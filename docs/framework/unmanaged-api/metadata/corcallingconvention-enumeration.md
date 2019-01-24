---
title: Enumeração CorCallingConvention
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c27669c8473bd52d3b82a14d570340ac38d1e07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523240"
---
# <a name="corcallingconvention-enumeration"></a>Enumeração CorCallingConvention
Contém valores que descrevem os tipos de convenções de chamada que são feitas no código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Indica uma convenção de chamada padrão.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Indica que o método utiliza um número variável de parâmetros.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Indica que a chamada é para um campo.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Indica que a chamada é para um método de local.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Indica que a chamada é para uma propriedade.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Indica que a chamada não gerenciada.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Indica uma instanciação de método genérico.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Indica uma chamada de PInvoke de 64 bits para um método que usa um número variável de parâmetros.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Descreve um valor inválido de 4 bits.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Indica que a convenção de chamada é descrita pelos bits inferior a quatro.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Indica que o bit superior descreve um `this` parâmetro.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Indica que um `this` parâmetro é descrito explicitamente na assinatura.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Indica uma assinatura de método genérico com um número explícito de argumentos de tipo. Isso precede uma contagem de parâmetros comuns.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
