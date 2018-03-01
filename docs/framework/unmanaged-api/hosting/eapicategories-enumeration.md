---
title: "Enumeração EApiCategories"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 630a3048072ed7b19b3250e75aca3b31e4dd7df7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="eapicategories-enumeration"></a>Enumeração EApiCategories
Descreve as categorias de recursos que o host pode bloquear a execução de código parcialmente confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eAll`|Especifica que todos os gerenciados classes e membros que são cobertos por outros `EApiCategories` campos bloquear a execução de código parcialmente confiável.|  
|`eExternalProcessMgmt`|Especifica que classes gerenciadas e membros que permitem a criação, manipulação e destruição de processos externos bloquear a execução de código parcialmente confiável.|  
|`eExternalThreading`|Especifica que classes gerenciadas e membros que permitem a criação, manipulação e destruição de segmentos externos bloquear a execução de código parcialmente confiável.|  
|`eMayLeakOnAbort`|Especifica que tipos gerenciados e membros que potencialmente podem causar o vazamento de memória em Anular bloquear a execução de código parcialmente confiável.|  
|`eNoCategory`|Especifica que nenhuma categoria de código gerenciado bloquear a execução de código parcialmente confiável.|  
|`eSecurityInfrastructure`|Especifica que a infraestrutura de segurança do common language runtime (CLR) impedido de ser usado por código parcialmente confiável.|  
|`eSelfAffectingProcessMgmt`|Especifica que classes gerenciadas e membros cujos recursos podem afetar o processo hospedado bloquear a execução de código parcialmente confiável.|  
|`eSelfAffectingThreading`|Especifica que classes gerenciadas e membros cujos recursos podem afetar os threads do processo hospedado bloquear a execução de código parcialmente confiável.|  
|`eSharedState`|Especifica que classes gerenciadas e membros que expõem o estado compartilhado bloquear a execução de código parcialmente confiável.|  
|`eSynchronization`|Especifica que classes de tempo de execução de linguagem e membros que permitem que o código do usuário manter bloqueios comuns bloquear a execução de código parcialmente confiável.|  
|`eUI`|Especifica que classes gerenciadas e membros que permitem ou exigem interação humana bloquear a execução de código parcialmente confiável.|  
  
## <a name="remarks"></a>Comentários  
 O [Iclrhostprotectionmanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) método usa um parâmetro do tipo `EApiCategories`.  
  
 O `EApiCategories` enumeração e `SetProtectedCategories` método estão diretamente relacionadas ao gerenciado <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe. A classe gerenciada é usada com o <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeração, cujos valores correspondem diretamente para o `EApiCategories` valores, para marcar tipos gerenciados e membros que expõem os recursos correspondentes às categorias descritas pelo `EApiCategories`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
