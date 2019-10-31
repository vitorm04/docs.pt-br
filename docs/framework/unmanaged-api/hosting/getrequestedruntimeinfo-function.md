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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136320"
---
# <a name="getrequestedruntimeinfo-function"></a>Função GetRequestedRuntimeInfo
Obtém informações de versão e diretório sobre o Common Language Runtime (CLR) solicitado por um aplicativo.  
  
 Essa função foi preterida no .NET Framework 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parâmetros  
 `pExe`  
 no O nome do aplicativo.  
  
 `pwszVersion`  
 no Uma cadeia de caracteres que especifica o número de versão do tempo de execução.  
  
 `pConfigurationFile`  
 no O nome do arquivo de configuração associado a `pExe`.  
  
 `startupFlags`  
 no Um ou mais dos valores de enumeração [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
 `runtimeInfoFlags`  
 no Um ou mais dos valores de enumeração [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) .  
  
 `pDirectory`  
 fora Um buffer que contém o caminho do diretório para o tempo de execução após a conclusão bem-sucedida.  
  
 `dwDirectory`  
 no O comprimento do buffer de diretório.  
  
 `dwDirectoryLength`  
 fora Um ponteiro para o comprimento da cadeia de caracteres do caminho do diretório.  
  
 `pVersion`  
 fora Um buffer que contém o número de versão do tempo de execução após a conclusão bem-sucedida.  
  
 `cchBuffer`  
 no O comprimento do buffer de cadeia de caracteres da versão.  
  
 `dwlength`  
 fora Um ponteiro para o comprimento da cadeia de caracteres da versão.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|ERROR_INSUFFICIENT_BUFFER|O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.<br /><br /> - ou -<br /><br /> O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.|  
  
## <a name="remarks"></a>Comentários  
 O método `GetRequestedRuntimeInfo` retorna informações de tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.  
  
 Na versão .NET Framework 2,0, você pode obter informações sobre a versão instalada mais recente usando o método `GetRequestedRuntimeInfo` da seguinte maneira:  
  
- Especifique os parâmetros `pExe`, `pwszVersion`e `pConfigurationFile` como NULL.  
  
- Especifique o sinalizador RUNTIME_INFO_UPGRADE_VERSION nas enumerações de `RUNTIME_INFO_FLAGS` para o parâmetro `runtimeInfoFlags`.  
  
 O método `GetRequestedRuntimeInfo` não retorna a versão mais recente do CLR nas seguintes circunstâncias:  
  
- Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma versão CLR específica. Observe que o .NET Framework usará o arquivo de configuração mesmo se você especificar NULL para o parâmetro `pConfigurationFile`.  
  
- O método [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) foi chamado especificando uma versão anterior do CLR.  
  
- Um aplicativo que foi compilado para uma versão anterior do CLR está em execução no momento.  
  
 Para o parâmetro `runtimeInfoFlags`, você pode especificar apenas uma das constantes de arquitetura da enumeração `RUNTIME_INFO_FLAGS` de cada vez:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Função GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
