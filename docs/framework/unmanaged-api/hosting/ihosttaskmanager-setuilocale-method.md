---
title: "Método IHostTaskManager::SetUILocale"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c29687d430187577ac25d8d2a007785632989ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetuilocale-method"></a>Método IHostTaskManager::SetUILocale
Notifica o host que o common language runtime (CLR) alterou a localidade do usuário (UI) de interface ou cultura, a tarefa em execução no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `lcid`  
 [in] O valor do identificador de localidade que mapeia para o idioma e cultura geográfica recentemente atribuída.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetUILocale`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|O host não permite que o código de usuário gerenciado para alterar a cultura de interface do usuário.|  
  
## <a name="remarks"></a>Comentários  
 O tempo de execução chama `SetUILocale` quando o valor da <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> propriedade é alterada pelo código gerenciado. Esse método fornece uma oportunidade para o host executar qualquer mecanismos pode ter para sincronização de localidades. Se um host não permite a localidade de interface do usuário a ser alterada de código gerenciado ou não implementa um mecanismo para sincronizar localidades, ele deverá retornar E_NOTIMPL deste método.  
  
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
 [Método SetLocale](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
