---
title: Função GetRequestedRuntimeInfo
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f37be8e3d2e92147e9f13954ab64396062ade2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getrequestedruntimeinfo-function"></a>Função GetRequestedRuntimeInfo
Obtém a versão e informações de diretório sobre o common language runtime (CLR) solicitado por um aplicativo.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pExe`  
 [in] O nome do aplicativo.  
  
 `pwszVersion`  
 [in] Uma cadeia de caracteres que especifica o número de versão do tempo de execução.  
  
 `pConfigurationFile`  
 [in] O nome do arquivo de configuração que está associado com `pExe`.  
  
 `startupFlags`  
 [in] Um ou mais o [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) valores de enumeração.  
  
 `runtimeInfoFlags`  
 [in] Um ou mais o [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) valores de enumeração.  
  
 `pDirectory`  
 [out] Um buffer que contém o caminho do diretório no tempo de execução após a conclusão bem-sucedida.  
  
 `dwDirectory`  
 [in] O comprimento do buffer de diretório.  
  
 `dwDirectoryLength`  
 [out] Um ponteiro para o comprimento da cadeia de caracteres de caminho de diretório.  
  
 `pVersion`  
 [out] Um buffer que contém o número de versão do tempo de execução após a conclusão bem-sucedida.  
  
 `cchBuffer`  
 [in] O comprimento do buffer de cadeia de caracteres de versão.  
  
 `dwlength`  
 [out] Um ponteiro para o comprimento da cadeia de caracteres de versão.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|ERROR_INSUFFICIENT_BUFFER|O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.<br /><br /> - ou -<br /><br /> O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.|  
  
## <a name="remarks"></a>Comentários  
 O `GetRequestedRuntimeInfo` método retorna informações de tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.  
  
 No .NET Framework versão 2.0, você pode obter informações sobre a versão mais recente instalada usando o `GetRequestedRuntimeInfo` método da seguinte maneira:  
  
-   Especifique o `pExe`, `pwszVersion`, e `pConfigurationFile` parâmetros como null.  
  
-   Especifique o sinalizador de RUNTIME_INFO_UPGRADE_VERSION o `RUNTIME_INFO_FLAGS` enumerações para o `runtimeInfoFlags` parâmetro.  
  
 O `GetRequestedRuntimeInfo` método não retorna a versão mais recente do CLR nas seguintes circunstâncias:  
  
-   Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma versão específica do CLR. Observe que o .NET Framework usará o arquivo de configuração, mesmo se você especificar null para o `pConfigurationFile` parâmetro.  
  
-   O [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) método foi chamado para especificar uma versão anterior do CLR.  
  
-   Um aplicativo que foi compilado para uma versão anterior do CLR está sendo executado.  
  
 Para o `runtimeInfoFlags` parâmetro, você pode especificar apenas uma das constantes de arquitetura do `RUNTIME_INFO_FLAGS` enumeração por vez:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [Função GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
