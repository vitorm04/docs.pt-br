---
title: Enumeração EBindPolicyLevels
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 635cf7c4e8ff715096728414506b4a7e683727b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704206"
---
# <a name="ebindpolicylevels-enumeration"></a>Enumeração EBindPolicyLevels
Fornece sinalizadores para especificar o nível no qual aplicar ou modificar a diretiva de assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|Especifica que a política deve ser aplicada no nível de administrador.|  
|`ePolicyLevelApp`|Especifica que a política deve ser aplicada no nível do aplicativo.|  
|`ePolicyLevelHost`|Especifica que a política deve ser aplicada no nível do host.|  
|`ePolicyLevelNone`|Não especifica que nenhum sinalizador de nível de política.|  
|`ePolicyLevelPublisher`|Especifica que a política deve ser aplicada no nível do publicador.|  
|`ePolicyLevelRetargetable`|Especifica que política deve ser aplicável em níveis de variável.|  
|`ePolicyPortability`|Especifica que a política deve oferecer suporte a portabilidade entre implementações de um assembly do .NET Framework. Consulte a [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) elemento do arquivo de configuração.|  
|`ePolicyUnifiedToCLR`|Especifica que política deve ser unificada do common language runtime (CLR).|  
  
## <a name="remarks"></a>Comentários  
 Essa enumeração é passada para métodos do [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface para especificar as alterações na política de aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
