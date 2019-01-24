---
title: Método ICLRRuntimeInfo::IsStarted
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb23a8e4237ff9b4b217458150c1f04956e439ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526581"
---
# <a name="iclrruntimeinfoisstarted-method"></a>Método ICLRRuntimeInfo::IsStarted
Indica se o tempo de execução foi iniciado (ou seja, se o [método iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) foi chamado e foi concluída com êxito).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbStarted`  
 [out] `true` se esse tempo de execução for iniciado; caso contrário, `false`.  
  
 `pdwStartupFlags`  
 [out] Retorna os sinalizadores que foram usados para iniciar o tempo de execução.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_NOTIMPL|A versão do common language runtime (CLR) é anterior à versão do CLR no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].|  
  
## <a name="remarks"></a>Comentários  
 Esse método não funciona com versões do CLR anterior à versão do CLR no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
