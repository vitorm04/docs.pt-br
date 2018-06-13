---
title: Função CorBindToRuntimeByCfg
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd7a1fd7bdd7e143ab89d509c4c70026d3f22c4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431858"
---
# <a name="corbindtoruntimebycfg-function"></a>Função CorBindToRuntimeByCfg
Carrega o common language runtime (CLR) em um processo usando as informações de versão que é lido de um arquivo XML.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCfgStream`  
 [in] Um ponteiro para um `IStream` objeto que lê o arquivo XML.  
  
 `reserved`  
 [in] Reservado para uso futuro. Use 0 (zero) como valor.  
  
 `startupFlags`  
 [in] Um valor de [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração que especifica o comportamento de inicialização do CLR.  
  
 `rclsid`  
 [in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface. Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] O `IID` da `ICorRuntimeHost` ou `ICLRRuntimeHost` interface. Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Um ponteiro para o endereço da interface retornado.  
  
## <a name="remarks"></a>Comentários  
 O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão. Para obter mais informações sobre os arquivos XML, consulte [esquema de arquivo de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
