---
title: Método IActionOnCLREvent::OnEvent
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28178cca27c257e480a7c5ec87c1925af7de4f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iactiononclreventonevent-method"></a>Método IActionOnCLREvent::OnEvent
Executa os retornos de chamada em eventos registrados por meio de uma chamada para o [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `event`  
 [in] Uma da [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) valores, que indica o tipo de evento.  
  
 `data`  
 [in] Um ponteiro para um objeto que contém detalhes sobre `event`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`OnEvent` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Se um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para qualquer método de hospedagem retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 O `data` parâmetro é um ponteiro para um objeto do tipo especificado. Se o `event` parâmetro é `Event_DomainUnload`, `data` é o identificador numérico para o <xref:System.AppDomain> que foi descarregado. O host pode levar a ação apropriada usando o identificador como uma chave.  
  
 Se `event` é `Event_MDAFired`, `data` é um ponteiro para um [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instância que contém a mensagem de saída de um gerenciado depuração MDA (Assistente). MDAs são um recurso do CLR que ajudam os desenvolvedores com depuração, ao gerar mensagens XML sobre eventos que são difíceis de interceptação. Essas mensagens podem ser especialmente úteis na depuração de transições entre código gerenciado e não gerenciado. Para obter mais informações, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Enumeração EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interface ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [Estrutura MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
