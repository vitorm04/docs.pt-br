---
title: Enumeração EApiCategories
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086449"
---
# <a name="eapicategories-enumeration"></a>Enumeração EApiCategories
Descreve as categorias de recursos que o host pode bloquear seja executado no código parcialmente confiável.  
  
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
|`eAll`|Especifica que todos os gerenciados classes e membros que são cobertos por outros `EApiCategories` campos impedido de ser executado em código parcialmente confiável.|  
|`eExternalProcessMgmt`|Especifica que classes gerenciadas e membros que permitem a criação, a manipulação e a destruição de processos externos impedido de ser executado em código parcialmente confiável.|  
|`eExternalThreading`|Especifica que classes gerenciadas e membros que permitem a criação, a manipulação e a destruição de threads externos impedido de ser executado em código parcialmente confiável.|  
|`eMayLeakOnAbort`|Especifica que tipos gerenciados e membros que poderia potencialmente vazar memória no abortar a execução bloqueada em código parcialmente confiável.|  
|`eNoCategory`|Especifica que nenhuma categoria de código gerenciado impedido de ser executado em código parcialmente confiável.|  
|`eSecurityInfrastructure`|Especifica que a infraestrutura de segurança do common language runtime (CLR) ser impedido de que está sendo usado pelo código parcialmente confiável.|  
|`eSelfAffectingProcessMgmt`|Especifica que classes gerenciadas e membros cujos recursos podem afetar o processo hospedado impedido de ser executado em código parcialmente confiável.|  
|`eSelfAffectingThreading`|Especifica que classes gerenciadas e membros cujos recursos podem afetar os threads no processo hospedado impedido de ser executado em código parcialmente confiável.|  
|`eSharedState`|Especifica que classes gerenciadas e membros que expõem o estado compartilhado impedido de ser executado em código parcialmente confiável.|  
|`eSynchronization`|Especifica que as classes de tempo de execução de linguagem e membros que permitem que o código do usuário manter bloqueios comuns impedido de ser executado em código parcialmente confiável.|  
|`eUI`|Especifica que classes gerenciadas e membros que permitem ou exigem interação humana impedido de ser executado em código parcialmente confiável.|  
  
## <a name="remarks"></a>Comentários  
 O [iclrhostprotectionmanager:: Setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) método utiliza um parâmetro de tipo `EApiCategories`.  
  
 O `EApiCategories` enumeração e a `SetProtectedCategories` método estão diretamente relacionados para o gerenciado <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> classe. A classe gerenciada é usada com o <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeração, cujos valores correspondem diretamente para o `EApiCategories` valores, para marcar tipos gerenciados e membros que expõem funcionalidades correspondentes às categorias descritas pelo `EApiCategories`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Hospedando enumerações](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
