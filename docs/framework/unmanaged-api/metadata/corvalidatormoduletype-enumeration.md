---
title: Enumeração CorValidatorModuleType
ms.date: 03/30/2017
api_name:
- CorValidatorModuleType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorValidatorModuleType
helpviewer_keywords:
- CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bed418d96658e29328cf2ce6bba445639b437f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750763"
---
# <a name="corvalidatormoduletype-enumeration"></a>Enumeração CorValidatorModuleType
Especifica o tipo de um módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|O módulo é um tipo inválido.|  
|`ValidatorModuleTypeMin`|O valor mínimo do `CorValidatorModuleType` enum.|  
|`ValidatorModuleTypePE`|O módulo é um arquivo executável portátil (PE).|  
|`ValidatorModuleTypeObj`|O módulo é um arquivo. obj.|  
|`ValidatorModuleTypeEnc`|O módulo é uma sessão do depurador de editar e continuar.|  
|`ValidatorModuleTypeIncr`|O módulo é aquele que foi compilado incrementalmente.|  
|`ValidatorModuleTypeMax`|O valor máximo da `CorValidatorModuleType` enum.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
