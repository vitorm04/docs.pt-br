---
title: Método IHostIoCompletionManager::InitializeHostOverlapped
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2951b408efa39e1ac2afbd7d8ebcb5ea139a8a71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582442"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>Método IHostIoCompletionManager::InitializeHostOverlapped
Fornece o host com uma oportunidade de inicializar quaisquer dados personalizados para acrescentar ao Win32 `OVERLAPPED` estrutura que é usada para solicitações de e/s assíncronas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pvOverlapped`  
 [in] Um ponteiro para o Win32 `OVERLAPPED` estrutura a ser incluído na solicitação de e/s.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não havia memória suficiente disponível para alocar o recurso solicitado.|  
  
## <a name="remarks"></a>Comentários  
 A plataforma Windows funções usam a `OVERLAPPED` estrutura para armazenar o estado para solicitações de e/s assíncronas. O CLR chama o `InitializeHostOverlapped` método para permitir que o host para acrescentar dados personalizados para um `OVERLAPPED` instância.  
  
> [!IMPORTANT]
>  Para obter o início do seu bloco de dados personalizados, hosts devem definir o deslocamento para o tamanho do `OVERLAPPED` estrutura (`sizeof(OVERLAPPED)`).  
  
 Um valor de retorno de E_OUTOFMEMORY indica que o host falhou ao inicializar seus dados personalizados. Nesse caso, o CLR relata um erro e não faz a chamada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [Método GetHostOverlappedSize](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [Interface IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
