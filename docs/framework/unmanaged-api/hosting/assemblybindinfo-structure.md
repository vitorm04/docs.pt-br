---
title: Estrutura AssemblyBindInfo
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 385ccc7a63fb5eb27ae7bdda5bdcf13c750eb667
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="assemblybindinfo-structure"></a>Estrutura AssemblyBindInfo
Fornece informações detalhadas sobre o assembly referenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwAppDomainId`|Um identificador exclusivo para o `IStream` retornado por uma chamada para [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), do qual o assembly referenciado está ser carregado.|  
|`lpReferencedIdentity`|Um identificador exclusivo para o assembly referenciado.|  
|`lpPostPolicyIdentity`|O identificador do assembly referenciado após a aplicação de quaisquer valores de política de associação.|  
|`ePolicyLevel`|Uma da [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) valores que indicam quais políticas de controle de versão, se houver, devem ser aplicadas para o assembly referenciado.|  
  
## <a name="remarks"></a>Comentários  
 O host fornece o identificador exclusivo `dwAppDomainId` para o common language runtime (CLR). Após uma chamada para `IHostAssemblyStore::ProvideAssembly` retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foram mapeadas. Nesse caso, o tempo de execução carrega a cópia existente em vez de remapeamento de fluxo. O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos retornados de chamadas para [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). Portanto, o identificador deve ser exclusivo para solicitações de módulo e de assembly.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [Estrutura ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
