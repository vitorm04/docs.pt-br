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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d70f7dd872cefbadce56c577ce2ecc9cbcb663b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765855"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>Enumeração EHostBindingPolicyModifyFlags
Permite que o host especificar o tipo de redirecionamento, que o common language runtime (CLR) deve executar ao aplicar as modificações de política de um assembly de origem para um assembly de destino.  
  
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
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Especifica que o CLR será encadear os valores da política do assembly de origem para as do assembly de destino.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Especifica que o CLR executará a ação padrão.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Especifica que o CLR definirá os valores da política do assembly de destino para os valores máximos.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Especifica que o CLR substituirá os valores da diretiva de assembly de destino com as do assembly de código-fonte.|  
  
## <a name="remarks"></a>Comentários  
 O [iclrhostbindingpolicymanager:: Modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) método utiliza um parâmetro de tipo `EHostBindingPolicyModifyFlags`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
