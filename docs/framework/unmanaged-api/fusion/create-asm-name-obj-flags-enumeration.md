---
title: Enumeração CREATE_ASM_NAME_OBJ_FLAGS
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: ee856dbd398d0fa5e3eee7d9b2b2cfc7c7a57ecf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176585"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>Enumeração CREATE_ASM_NAME_OBJ_FLAGS
Especifica os atributos de um objeto [IAssemblyName Interface](iassemblyname-interface.md) quando ele é construído pela função [CreateAssemblyNameObject.](createassemblynameobject-function.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|Indica que o parâmetro passado é uma identidade textual.|  
|`CANOF_SET_DEFAULT_VALUES`|Define alguns valores padrão.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Verifica a regra da assembléia do amigo (apenas nome e chave pública). Este membro é apenas para uso interno.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Uma combinação `CANOF_PARSE_DISPLAY_NAME` de `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` bandeiras. Este membro é apenas para uso interno.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IAssemblyName](iassemblyname-interface.md)
- [Função CreateAssemblyNameObject](createassemblynameobject-function.md)
- [Enumerações Fusion](fusion-enumerations.md)
