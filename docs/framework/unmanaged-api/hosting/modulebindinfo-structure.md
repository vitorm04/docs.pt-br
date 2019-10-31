---
title: Estrutura ModuleBindInfo
ms.date: 03/30/2017
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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133742"
---
# <a name="modulebindinfo-structure"></a>Estrutura ModuleBindInfo
Fornece informações detalhadas sobre o módulo referenciado e o assembly que o contém.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwAppDomainId`|Um identificador exclusivo para o `IStream` retornado por uma chamada para o método [IHostAssemblyStore::P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) do qual o módulo referenciado deve ser carregado.|  
|`lpAssemblyIdentity`|Um identificador exclusivo para o assembly que contém o módulo referenciado.|  
|`lpModuleName`|O nome do módulo referenciado.|  
  
## <a name="remarks"></a>Comentários  
 `ModuleBindInfo` é passado como um parâmetro para `IHostAssemblyStore::ProvideModule`. O host fornece o identificador exclusivo `dwAppDomainId` para o Common Language Runtime (CLR). Após uma chamada para o método [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) retorna, o tempo de execução usa o identificador para determinar se o conteúdo do `IStream` foi mapeado. Nesse caso, o tempo de execução carrega a cópia existente em vez de remapear o fluxo. O tempo de execução também usa esse identificador como uma chave de pesquisa para fluxos que são retornados de chamadas para o método `IHostAssemblyStore::ProvideAssembly`. Portanto, o identificador deve ser exclusivo para solicitações de módulo, bem como para solicitações de assembly.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. idl  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Estrutura AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
