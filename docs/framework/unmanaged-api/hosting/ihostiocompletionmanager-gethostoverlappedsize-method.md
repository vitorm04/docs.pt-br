---
title: Método IHostIoCompletionManager::GetHostOverlappedSize
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: a97009a4ebc834d867dddcc350033c550364ea42
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804746"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>Método IHostIoCompletionManager::GetHostOverlappedSize
Obtém o tamanho de qualquer dado personalizado que o host pretende acrescentar às solicitações de e/s.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pcbSize`  
 fora Um ponteiro para o número de bytes que o Common Language Runtime (CLR) deve alocar além do tamanho do objeto do Win32 `OVERLAPPED` .  
  
## <a name="return-value"></a>Valor Retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize`retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Todas as chamadas de e/s assíncronas para APIs da plataforma Windows usam um `OVERLAPPED` objeto Win32, que fornece informações como a posição do ponteiro do arquivo. Para manter o estado, os aplicativos que fazem chamadas de e/s assíncronas normalmente adicionam dados personalizados à estrutura. `GetHostOverlappedSize`e [IHostIoCompletionManager:: InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) fornecem uma oportunidade para o host incluir esses dados personalizados.  
  
 O CLR chama o `GetHostOverlappedSize` método para determinar o tamanho dos dados personalizados que o host pretende acrescentar ao `OVERLAPPED` objeto.  
  
> [!NOTE]
> `GetHostOverlappedSize`é chamado apenas uma vez. Os dados personalizados do host devem ter o mesmo tamanho para cada solicitação de e/s.  
  
> [!IMPORTANT]
> O tamanho do `OVERLAPPED` objeto em si não é incluído no valor de `pcbSize` .  
  
 Para obter mais informações sobre a `OVERLAPPED` estrutura, consulte a documentação da plataforma Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Threading.NativeOverlapped>
- [Interface ICLRIoCompletionManager](iclriocompletionmanager-interface.md)
- [Interface IHostIoCompletionManager](ihostiocompletionmanager-interface.md)
