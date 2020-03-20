---
title: Método IHostTaskManager::CreateTask
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177994"
---
# <a name="ihosttaskmanagercreatetask-method"></a>Método IHostTaskManager::CreateTask
Solicita que o host crie uma nova tarefa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `stacksize`  
 [em] O tamanho solicitado, em bytes, da pilha solicitada, ou 0 (zero) para o tamanho padrão.  
  
 `pStartAddress`  
 [em] Um ponteiro para a função que a tarefa deve executar.  
  
 `pParameter`  
 [em] Um ponteiro para os dados do usuário a ser passado para a função, ou nulo se a função não tiver parâmetros.  
  
 `ppTask`  
 [fora] Um ponteiro para o endereço de uma instância [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) criado pelo host ou nulo se a tarefa não puder ser criada. A tarefa permanece em um estado suspenso até que seja explicitamente iniciada por uma chamada para [IHostTask:::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
## <a name="return-value"></a>Valor retornado  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`CreateTask`retornou com sucesso.|  
|Host_e_clrnotavailable|O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.|  
|HOST_E_TIMEOUT|A chamada acabou.|  
|HOST_E_NOT_OWNER|O interlocutor não é dono da fechadura.|  
|HOST_E_ABANDONED|Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.|  
|E_FAIL|Uma falha catastrófica desconhecida ocorreu. Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo. Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Não havia memória suficiente para criar a tarefa solicitada.|  
  
## <a name="remarks"></a>Comentários  
 O CLR `CreateTask` chama para solicitar que o host crie uma nova tarefa. O host retorna um `IHostTask` ponteiro de interface para uma instância. A tarefa retornada deve permanecer suspensa até que seja `IHostTask::Start`explicitamente iniciada por uma chamada para .  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
