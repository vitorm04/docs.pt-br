---
title: Método ICLRTask::SetTaskIdentifier
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a561c54f2d004d073fdfffffdb59cb2b5189e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435674"
---
# <a name="iclrtasksettaskidentifier-method"></a>Método ICLRTask::SetTaskIdentifier
Instrui o common language runtime (CLR) para associar o valor do identificador especificado da tarefa representada pela atual [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Asked`  
 [in] O identificador exclusivo para o common language runtime associar com a tarefa representada por atual `ICLRTask` instância.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetTaskIdentifier` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O host pode associar um identificador com uma tarefa para ajudar a integrar o CLR e o host em um ambiente de depuração. O identificador não tem nenhum significado para o CLR. O CLR transmite-o para um aplicativo do depurador. O depurador pode usar esse identificador para associar a uma pilha de chamadas do host de uma pilha de chamadas CLR e habilitar as informações de rastreamento do respectivos a ser unificado quando exibido na interface do usuário do depurador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
