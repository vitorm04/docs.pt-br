---
title: "Método ICLRTask::Reset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dc37f47fc01d73ff499ef974a2e11345a95286a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskreset-method"></a>Método ICLRTask::Reset
Informa o common language runtime (CLR) que o host concluiu uma tarefa e habilita o CLR reutilizar atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância para representar outra tarefa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fFull`  
 [in] `true`, se o tempo de execução deve restaurar todos os relacionados ao thread estático valores além das informações de segurança e a localidade relacionadas à atual `ICLRTask` instância; caso contrário, `false`.  
  
 Se o valor for `true`, o tempo de execução redefine os dados que foram armazenados usando <xref:System.Threading.Thread.AllocateDataSlot%2A> ou <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`Reset`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada. com êxito|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O CLR pode reciclar criado anteriormente `ICLRTask` instâncias para evitar a sobrecarga de repetidamente criando novas instâncias toda vez que ele precisa de uma nova tarefa. O host habilita esse recurso chamando `ICLRTask::Reset` em vez de [: Exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) quando ela estiver concluída, uma tarefa. A lista a seguir resume o ciclo de vida normal de uma `ICLRTask` instância:  
  
1.  O tempo de execução cria um novo `ICLRTask` instância.  
  
2.  O tempo de execução chama [Getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) para obter uma referência para a tarefa de host atual.  
  
3.  O tempo de execução chama [: Setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) para associar a nova instância da tarefa de host.  
  
4.  A tarefa executa e concluído.  
  
5.  O host destrói a tarefa chamando `ICLRTask::ExitTask`.  
  
 `Reset`altera esse cenário de duas maneiras. Na etapa 5 acima, as chamadas de host `Reset` para redefinir a tarefa para um estado limpo e, em seguida, separa o `ICLRTask` instância de seus associados [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instância. Se desejado, o host também pode armazenar a `IHostTask` instância para reutilização. Na etapa 1 acima, o tempo de execução recebe uma reciclagem `ICLRTask` do cache em vez de criar uma nova instância.  
  
 Essa abordagem funciona bem quando o host também tem um conjunto de tarefas de trabalho reutilizáveis. Quando o host destrói um dos seus `IHostTask` instâncias, ele destrói correspondente `ICLRTask` chamando `ExitTask`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
