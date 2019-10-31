---
title: Método IHostAssemblyStore::ProvideModule
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: eed09a8149a21140ad61133f29391f86cb0fb929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124468"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>Método IHostAssemblyStore::ProvideModule
Resolve um módulo dentro de um assembly ou um arquivo de recurso vinculado (mas não um inserido).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pBindInfo`  
 no Um ponteiro para uma instância [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) que descreve o <xref:System.AppDomain>, o assembly e o nome do módulo solicitados do módulo.  
  
 `pdwModuleId`  
 fora Um ponteiro para um identificador exclusivo para o `IStream` que contém o módulo carregado.  
  
 `ppStmModuleImage`  
 fora Um ponteiro para o endereço de um objeto `IStream`, que contém a imagem executável portátil (PE) a ser carregada, ou NULL se o módulo não foi encontrado.  
  
 `ppStmPDB`  
 fora Um ponteiro para o endereço de um objeto `IStream`, que contém as informações de depuração do programa (PDB) para o módulo solicitado, ou NULL se não foi possível encontrar o arquivo. pdb.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`ProvideModule` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Não foi possível localizar o assembly ou recurso vinculado solicitado.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` não é grande o suficiente para conter o identificador que o host deseja retornar.|  
  
## <a name="remarks"></a>Comentários  
 O valor de identidade retornado para `pdwModuleId` é especificado pelo host. Os identificadores devem ser exclusivos dentro do tempo de vida de um processo. O CLR usa esse valor como o identificador exclusivo para o fluxo associado. Ele verifica cada valor em relação aos valores de `pAssemblyId` retornados por chamadas para [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) e em relação aos valores de `pdwModuleId` retornados por outras chamadas para `ProvideModule`. Se o host retornar o mesmo valor de identificador para outra `IStream`, o CLR verificará se o conteúdo desse fluxo já foi mapeado. Nesse caso, o CLR carrega a cópia existente da imagem em vez de mapear uma nova. Portanto, o identificador também não deve se sobrepor aos identificadores de assembly retornados de `ProvideAssembly`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
