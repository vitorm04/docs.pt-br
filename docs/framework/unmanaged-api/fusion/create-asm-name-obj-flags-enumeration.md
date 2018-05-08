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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2997bb90f2d9034de398b901fcbd6265dcb59998
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="createasmnameobjflags-enumeration"></a>Enumeração CREATE_ASM_NAME_OBJ_FLAGS
Especifica os atributos de uma [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objeto quando ele é construído pelo [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Verifica a regra de assembly friend (somente o nome e a chave pública). Esse membro é somente para uso interno.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Uma combinação da `CANOF_PARSE_DISPLAY_NAME` e `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` sinalizadores. Esse membro é somente para uso interno.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Função CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [Enumerações de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
