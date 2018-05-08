---
title: Método ICLRGCManager2::SetGCStartupLimitsEx
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65fbf0bf42f7312ad80b61bf452b62a4d0ff93c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a>Método ICLRGCManager2::SetGCStartupLimitsEx
Define o tamanho de um segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo 0.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
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
|S_OK|`SetGCStartupLimitsEx` retornou com êxito.|  
|HOST_E_CLRNOTAVAILABLE|O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.|  
|HOST_E_TIMEOUT|A chamada foi atingido.|  
|HOST_E_NOT_OWNER|O chamador não possui o bloqueio.|  
|HOST_E_ABANDONED|Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.|  
|E_FAIL|Ocorreu uma falha catastrófica desconhecida. Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo. As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Comentários  
 Os valores que `SetGCStartupLimitsEx` conjuntos podem ser especificados apenas antes que o host é iniciado. Chamadas posteriores para `SetGCStartupLimitsEx` são ignorados.  
  
 Para definir um parâmetro sem afetar o outro, especifique 0 (zero) para o parâmetro que você não deseja alterar.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciamento Automático de Memória](../../../../docs/standard/automatic-memory-management.md)  
 [Coleta de lixo](../../../../docs/standard/garbage-collection/index.md)  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interface ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
