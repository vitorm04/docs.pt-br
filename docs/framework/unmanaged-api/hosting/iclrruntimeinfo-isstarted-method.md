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
ms.openlocfilehash: 85a7adddf395e07297c8fb6ceab4aa81e0aaf012
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762195"
---
# <a name="iclrruntimeinfoisstarted-method"></a>Método ICLRRuntimeInfo::IsStarted
Indica se o tempo de execução foi iniciado (ou seja, se o [Método ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) foi chamado e teve êxito).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pbStarted`  
 [fora] `true` Se esse tempo de execução for iniciado; caso contrário, `false` .  
  
 `pdwStartupFlags`  
 fora Retorna os sinalizadores que foram usados para iniciar o tempo de execução.  
  
## <a name="return-value"></a>Valor Retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_NOTIMPL|A versão Common Language Runtime (CLR) é anterior à versão do CLR no .NET Framework 4.|  
  
## <a name="remarks"></a>Comentários  
 Esse método não funciona com versões do CLR anteriores à versão do CLR no .NET Framework 4.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRRuntimeInfo](iclrruntimeinfo-interface.md)
- [Interfaces de hospedagem](hosting-interfaces.md)
- [Hospedagem](index.md)
