---
title: Enumeração EHostBindingPolicyModifyFlags
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616236"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>Enumeração EHostBindingPolicyModifyFlags
Permite que o host especifique o tipo de redirecionamento que o Common Language Runtime (CLR) deve executar ao aplicar as modificações de política de um assembly de origem a um assembly de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Especifica que o CLR encadeará os valores de política do assembly de origem para aqueles do assembly de destino.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Especifica que o CLR executará a ação padrão.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Especifica que o CLR definirá os valores de política do assembly de destino para os valores máximos.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Especifica que o CLR substituirá os valores de política do assembly de destino pelos do assembly de origem.|  
  
## <a name="remarks"></a>Comentários  
 O método [ICLRHostBindingPolicyManager:: ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) usa um parâmetro do tipo `EHostBindingPolicyModifyFlags` .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md)
- [Hospedando enumerações](hosting-enumerations.md)
