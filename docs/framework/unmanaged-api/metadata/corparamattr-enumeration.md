---
title: Enumeração CorParamAttr
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ba2103003e3976e51e82ad6b42315a881582f5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corparamattr-enumeration"></a>Enumeração CorParamAttr
Contém valores que descrevem os metadados de um parâmetro de método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`pdIn`|Especifica que o parâmetro é passado para a chamada do método.|  
|`pdOut`|Especifica se o parâmetro é passado do método de retorno.|  
|`pdOptional`|Especifica que o parâmetro é opcional.|  
|`pdReservedMask`|Reservado para uso interno pelo common language runtime.|  
|`pdHasDefault`|Especifica que o parâmetro tem um valor padrão.|  
|`pdHasFieldMarshal`|Especifica que o parâmetro tem informações de marshaling.|  
|`pdUnused`|Não utilizado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
