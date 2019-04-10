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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bf7342157de48e0183537afea2f2e53d1498dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300301"
---
# <a name="iclrtaskreset-method"></a>Método ICLRTask::Reset
Informa o common language runtime (CLR) que o host tiver concluído uma tarefa e permite que o CLR para reutilizar o atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância para representar outra tarefa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `fFull`  
 [in] `true`, se o tempo de execução deve redefinir todos os relacionados a thread estáticos valores além das informações de segurança e a localidade relacionados ao atual `ICLRTask` instância; caso contrário, `false`.  
  
 Se o valor for `true`, o tempo de execução redefine os dados que foram armazenados usando <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`Reset` retornado com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada. com êxito|  
|HOST_E_TIMEOUT|A chamada atingiu o tempo limite.|  
|HOST_E_NOT_OWNER|O chamador não é proprietário do bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo. As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O CLR pode ser recicladas criado anteriormente `ICLRTask` instâncias para evitar a sobrecarga de repetidamente criar novas instâncias toda vez que ele precisa de uma nova tarefa. O host habilita esse recurso chamando `ICLRTask::Reset` em vez de [iclrtask:: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) quando tiver concluído uma tarefa. A lista a seguir resume o ciclo de vida normal de um `ICLRTask` instância:  
  
1. O tempo de execução cria um novo `ICLRTask` instância.  
  
2. A tempo de execução chama [ihosttaskmanager:: Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) para obter uma referência à tarefa atual do host.  
  
3. A tempo de execução chama [ihosttask:: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) para associar a nova instância da tarefa de host.  
  
4. A tarefa é executada e é concluída.  
  
5. O host destrói a tarefa chamando `ICLRTask::ExitTask`.  
  
 `Reset` altera esse cenário de duas maneiras. Na etapa 5 acima, o host chama `Reset` para redefinir a tarefa para um estado limpo e, em seguida, separa o `ICLRTask` instância de seus associados [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância. Se desejado, o host pode também armazenar em cache o `IHostTask` instância para reutilização. Na etapa 1 acima, o tempo de execução recebe um reciclado `ICLRTask` do cache em vez de criar uma nova instância.  
  
 Essa abordagem funciona bem quando o host também tem um pool de tarefas de trabalho reutilizáveis. Quando o host destrói um dos seus `IHostTask` instâncias, ele destrói correspondente `ICLRTask` chamando `ExitTask`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
