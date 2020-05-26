---
title: Método IHostAssemblyManager::GetAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805078"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a>Método IHostAssemblyManager::GetAssemblyStore
Obtém um ponteiro de interface para um [IHostAssemblyStore](ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ppAssemblyStore`  
 fora Um ponteiro de função para uma `IHostAssemblyStore` instância, ou NULL, se o host não implementar `IHostAssemblyStore` .  
  
## <a name="return-value"></a>Valor Retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetAssemblyStore`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|O host não fornece uma implementação de `IHostAssemblyStore` .|  
  
## <a name="remarks"></a>Comentários  
 `IHostAssemblyStore`fornece métodos que permitem que um host se associe a assemblies e módulos independentemente do CLR. Normalmente, os hosts fornecem armazenamentos de assembly para permitir que os assemblies sejam carregados a partir de formatos diferentes do sistema de arquivos.  
  
> [!NOTE]
> Se o host não implementar `IHostAssemblyStore` , `GetAssemblyStore` deverá retornar um valor HRESULT de E_NOINTERFACE e deverá definir `ppAssemblyStore` como NULL.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IHostAssemblyManager](ihostassemblymanager-interface.md)
- [Interface IHostAssemblyStore](ihostassemblystore-interface.md)
