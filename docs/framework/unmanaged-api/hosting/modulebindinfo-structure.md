---
title: Estrutura ModuleBindInfo
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
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a>Estrutura ModuleBindInfo
Fornece informações detalhadas sobre o módulo referenciado e o assembly que o contém.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwAppDomainId`|Um identificador exclusivo para o `IStream` que é retornado por uma chamada para o [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) método do qual o módulo referenciado está ser carregado.|  
|`lpAssemblyIdentity`|Um identificador exclusivo para o assembly que contém o módulo referenciado.|  
|`lpModuleName`|O nome do módulo referenciado.|  
  
## <a name="remarks"></a>Comentários  
 `ModuleBindInfo`é passado como um parâmetro para `IHostAssemblyStore::ProvideModule`. O host fornece o identificador exclusivo `dwAppDomainId` para o common language runtime (CLR). Após uma chamada para o [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) método retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foram mapeadas. Nesse caso, o tempo de execução carrega a cópia existente em vez de remapeamento de fluxo. O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos que são retornados de chamadas para o `IHostAssemblyStore::ProvideAssembly` método. Portanto, o identificador deve ser exclusivo para solicitações do módulo, bem como para solicitações de assembly.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Estrutura AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
