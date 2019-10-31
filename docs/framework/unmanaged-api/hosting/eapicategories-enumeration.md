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
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131208"
---
# <a name="eapicategories-enumeration"></a>Enumeração EApiCategories
Descreve as categorias de recursos que o host pode bloquear de ser executado em código parcialmente confiável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`eAll`|Especifica que todas as classes e membros gerenciados que são cobertos por outros `EApiCategories` campos sejam impedidos de serem executados em código parcialmente confiável.|  
|`eExternalProcessMgmt`|Especifica que classes e membros gerenciados que permitem a criação, manipulação e destruição de processos externos sejam impedidos de serem executados em código parcialmente confiável.|  
|`eExternalThreading`|Especifica que classes e membros gerenciados que permitem a criação, manipulação e destruição de threads externos sejam impedidos de serem executados em código parcialmente confiável.|  
|`eMayLeakOnAbort`|Especifica que os tipos gerenciados e membros que poderiam vazar memória em anulação sejam impedidos de serem executados em código parcialmente confiável.|  
|`eNoCategory`|Especifica que nenhuma categoria de código gerenciado será impedida de ser executada em código parcialmente confiável.|  
|`eSecurityInfrastructure`|Especifica que a infraestrutura de segurança Common Language Runtime (CLR) seja impedida de ser usada pelo código parcialmente confiável.|  
|`eSelfAffectingProcessMgmt`|Especifica que classes e membros gerenciados cujos recursos podem afetar o processo hospedado sejam impedidos de serem executados em código parcialmente confiável.|  
|`eSelfAffectingThreading`|Especifica que classes e membros gerenciados cujos recursos podem afetar threads no processo hospedado serão impedidos de serem executados em código parcialmente confiável.|  
|`eSharedState`|Especifica que classes e membros gerenciados que expõem o estado compartilhado sejam impedidos de serem executados em código parcialmente confiável.|  
|`eSynchronization`|Especifica que Common Language Runtime classes e membros que permitem que o código do usuário mantenha bloqueios sejam impedidos de serem executados em código parcialmente confiável.|  
|`eUI`|Especifica que classes e membros gerenciados que permitem ou exigem interação humana são impedidos de serem executados em código parcialmente confiável.|  
  
## <a name="remarks"></a>Comentários  
 O método [ICLRHostProtectionManager:: SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) usa um parâmetro do tipo `EApiCategories`.  
  
 A enumeração `EApiCategories` e o método `SetProtectedCategories` estão diretamente relacionados à classe <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> gerenciada. A classe gerenciada é usada com a enumeração <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, cujos valores correspondem diretamente aos valores de `EApiCategories`, para marcar tipos gerenciados e membros que expõem recursos correspondentes às categorias descritas por `EApiCategories`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
