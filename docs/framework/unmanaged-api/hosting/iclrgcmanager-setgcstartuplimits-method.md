---
title: "Método ICLRGCManager::SetGCStartupLimits"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1fd0c31fd6f988d4ee36bfe140b95ec258d4214e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a>Método ICLRGCManager::SetGCStartupLimits
Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.  
  
> [!IMPORTANT]
>  Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], você pode definir o tamanho do segmento e o tamanho máximo de geração 0 para valores maior `DWORD` usando o [Iclrgcmanager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `SegmentSize`  
 [in] O tamanho especificado de um segmento de coleta de lixo.  
  
 O tamanho do segmento mínimo é de 4 MB. Segmentos podem ser aumentada em incrementos de 1 MB ou maior.  
  
 `MaxGen0Size`  
 [in] O tamanho máximo especificado para a geração 0.  
  
 O tamanho mínimo de geração 0 é 64 KB.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimits`retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Os valores que `SetGCStartupLimits` conjuntos podem ser especificados somente uma vez. Chamadas posteriores para `SetGCStartupLimits` são ignorados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento Automático de Memória](../../../../docs/standard/automatic-memory-management.md)  
 [Coleta de lixo](../../../../docs/standard/garbage-collection/index.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interface ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
