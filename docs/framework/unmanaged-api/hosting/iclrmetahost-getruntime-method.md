---
title: Método ICLRMetaHost::GetRuntime
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9889ddf1c03f14835101f31d0a3b264f0016267
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676545"
---
# <a name="iclrmetahostgetruntime-method"></a>Método ICLRMetaHost::GetRuntime
Obtém o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde a uma versão específica do common language runtime (CLR). Esse método substitui o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função usada com o [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sinalizador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwzVersion`  
 [in] A versão de compilação do .NET Framework armazenada nos metadados, no formato "v*um*. *B*[. *X*] ". *Um*, *B*, e *X* são números decimais que correspondem da versão principal, a versão secundária e o número da compilação.  
  
> [!NOTE]
>  Esse parâmetro deve corresponder ao nome de diretório para a versão do .NET Framework, como ele aparece sob C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.  
  
 Os valores de exemplo são "v1.0.3705", "v1.1.4322", "v2.0.50727" e "v4.0. *X*", onde *X* depende do número de compilação instalado. O prefixo "v" é necessário.  
  
 `riid`  
 [in] O identificador para a interface desejada. Atualmente, o único valor válido para esse parâmetro é IID_ICLRRuntimeInfo.  
  
 `ppRuntime`  
 [out] Um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde ao tempo de execução solicitado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pwzVersion` ou `ppRuntime` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 Esse método consistentemente interage com interfaces herdadas, como o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface e herdado funções como preteridas `CorBindTo*` funções (consulte [preterido hospedando funções CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) na API de hospedagem do .NET Framework 2.0). Ou seja, tempos de execução que são carregados com a API herdada são visíveis para a nova API e tempos de execução que são carregados com a nova API são visíveis para a API herdada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Interfaces e coclasses de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [Interfaces de hospedagem CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
