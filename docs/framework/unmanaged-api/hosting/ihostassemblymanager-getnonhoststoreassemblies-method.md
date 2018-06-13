---
title: Método IHostAssemblyManager::GetNonHostStoreAssemblies
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0da548d5d5cc22eb6754859a802afa4d82fac89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438383"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>Método IHostAssemblyManager::GetNonHostStoreAssemblies
Obtém um ponteiro de interface para um [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) que representa a lista de assemblies que o host espera o common language runtime (CLR) para carregar.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppReferenceList`  
 [out] Um ponteiro para o endereço de um `ICLRAssemblyReferenceList` que contém uma lista de referências a assemblies para carregar o CLR espera que o host.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não havia memória suficiente criar a lista de referências para a solicitação `ICLRAssemblyReferenceList`.|  
  
## <a name="remarks"></a>Comentários  
 O CLR resolve referências usando o seguinte conjunto de diretrizes:  
  
-   Primeiro, a lista de referências de assembly retornado pela consulta `GetNonHostStoreAssemblies`.  
  
-   Se o assembly é exibido na lista, o CLR associa a ele normalmente.  
  
-   Se o assembly não aparecem na lista e o host fornece uma implementação de [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), o CLR chama [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) para permitir que o host fornecer o assembly para associar a.  
  
-   Caso contrário, o CLR não vincular ao assembly.  
  
 Se o host define `ppReferenceList` como nula, os testes do primeiro CLR chama o cache de assembly global, `ProvideAssembly`e, em seguida, testes da base do aplicativo para resolver uma referência de assembly.  
  
> [!NOTE]
>  Na inicialização, o CLR chama `GetNonHostStoreAssemblies` apenas uma vez. O método não é chamado novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
