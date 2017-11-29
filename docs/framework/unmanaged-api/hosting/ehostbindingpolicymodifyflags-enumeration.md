---
title: "Enumeração EHostBindingPolicyModifyFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EHostBindingPolicyModifyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EHostBindingPolicyModifyFlags
helpviewer_keywords: EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ff7ec7487be649e353b48e537cf1d8d45f6962
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>Enumeração EHostBindingPolicyModifyFlags
Permite que o host especificar o tipo de redirecionamento, que o common language runtime (CLR) deve ser executadas ao aplicar modificações de política de um assembly de origem para um assembly de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Especifica que o CLR será cadeia de valores da política do assembly de origem para os do assembly de destino.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Especifica que o CLR executará a ação padrão.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Especifica que o CLR definirá os valores de diretiva de assembly de destino para os valores máximos.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Especifica que o CLR substituirá os valores da diretiva de assembly de destino com aqueles o assembly de origem.|  
  
## <a name="remarks"></a>Comentários  
 O [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) método usa um parâmetro do tipo `EHostBindingPolicyModifyFlags`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
