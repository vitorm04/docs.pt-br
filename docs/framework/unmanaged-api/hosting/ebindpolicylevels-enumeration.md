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
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ebindpolicylevels-enumeration"></a>Enumeração EBindPolicyLevels
Fornece os sinalizadores para especificar o nível no qual aplicar ou modificar a diretiva de assembly.  
  
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
|`ePolicyLevelNone`|Não especifica os sinalizadores nenhum nível de política.|  
|`ePolicyLevelPublisher`|Especifica que a política deve ser aplicada no nível do publicador.|  
|`ePolicyLevelRetargetable`|Especifica que política deve ser aplicável em níveis de variável.|  
|`ePolicyPortability`|Especifica que a política deve oferecer suporte portabilidade entre implementações de um assembly do .NET Framework. Consulte o [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) elemento do arquivo de configuração.|  
|`ePolicyUnifiedToCLR`|Especifica que deve ser unificada política para que o common language runtime (CLR).|  
  
## <a name="remarks"></a>Comentários  
 Essa enumeração é passada para métodos do [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface para especificar as alterações na política de aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
