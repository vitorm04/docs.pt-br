---
title: Método ICLRTask::Reset
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124636"
---
# <a name="iclrtaskreset-method"></a>Método ICLRTask::Reset
Informa o Common Language Runtime (CLR) que o host concluiu uma tarefa e permite que o CLR reutilize a instância [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) atual para representar outra tarefa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fFull`  
 [in] `true`, se o tempo de execução deve redefinir todos os valores estáticos relacionados ao thread, além das informações de segurança e localidade relacionadas à instância de `ICLRTask` atual; caso contrário, `false`.  
  
 Se o valor for `true`, o tempo de execução redefinirá os dados que foram armazenados usando <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`Reset` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada. com êxito|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo. As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O CLR pode reciclar instâncias de `ICLRTask` criadas anteriormente para evitar a sobrecarga de criar novas instâncias repetidamente toda vez que precisar de uma nova tarefa. O host habilita esse recurso chamando `ICLRTask::Reset` em vez de [ICLRTask:: ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) quando tiver concluído uma tarefa. A lista a seguir resume o ciclo de vida normal de uma instância de `ICLRTask`:  
  
1. O tempo de execução cria uma nova instância de `ICLRTask`.  
  
2. O tempo de execução chama [IHostTaskManager:: GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) para obter uma referência à tarefa de host atual.  
  
3. O tempo de execução chama [IHostTask:: SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) para associar a nova instância à tarefa do host.  
  
4. A tarefa é executada e concluída.  
  
5. O host destrói a tarefa chamando `ICLRTask::ExitTask`.  
  
 `Reset` altera esse cenário de duas maneiras. Na etapa 5 acima, o host chama `Reset` para redefinir a tarefa para um estado limpo e, em seguida, dissocia a instância `ICLRTask` de sua instância [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) associada. Se desejar, o host também pode armazenar em cache a instância de `IHostTask` para reutilização. Na etapa 1 acima, o tempo de execução efetua pull de um `ICLRTask` reciclado do cache em vez de criar uma nova instância.  
  
 Essa abordagem funciona bem quando o host também tem um pool de tarefas de trabalho reutilizáveis. Quando o host destrói uma de suas instâncias de `IHostTask`, ele destrói o `ICLRTask` correspondente chamando `ExitTask`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
