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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178147"
---
# <a name="getrequestedruntimeinfo-function"></a>Função GetRequestedRuntimeInfo
Obtém informações de versão e diretório sobre o tempo de execução do idioma comum (CLR) solicitado por um aplicativo.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `pExe`  
 [em] O nome da aplicação.  
  
 `pwszVersion`  
 [em] Uma seqüência especificando o número da versão do tempo de execução.  
  
 `pConfigurationFile`  
 [em] O nome do arquivo de `pExe`configuração que está associado a .  
  
 `startupFlags`  
 [em] Um ou mais dos valores [de enumeração STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
  
 `runtimeInfoFlags`  
 [em] Um ou mais dos valores de enumeração [RUNTIME_INFO_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)  
  
 `pDirectory`  
 [fora] Um buffer que contém o caminho do diretório para o tempo de execução após a conclusão bem sucedida.  
  
 `dwDirectory`  
 [em] A duração do buffer do diretório.  
  
 `dwDirectoryLength`  
 [fora] Um ponteiro para o comprimento da seqüência do caminho do diretório.  
  
 `pVersion`  
 [fora] Um buffer que contém o número da versão do tempo de execução após a conclusão bem sucedida.  
  
 `cchBuffer`  
 [em] O comprimento do buffer de string da versão.  
  
 `dwlength`  
 [fora] Um ponteiro para o comprimento da seqüência de versão.  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com sucesso.|  
|Error_insufficient_buffer|O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.<br /><br /> - ou -<br /><br /> O buffer de versão não é grande o suficiente para armazenar a seqüência de versões.|  
  
## <a name="remarks"></a>Comentários  
 O `GetRequestedRuntimeInfo` método retorna informações em tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.  
  
 Na versão 2.0 do .NET Framework, você pode obter informações `GetRequestedRuntimeInfo` sobre a versão instalada mais recente usando o método da seguinte forma:  
  
- Especifique os `pExe` `pwszVersion`parâmetros e `pConfigurationFile` os parâmetros como nulos.  
  
- Especifique a `RUNTIME_INFO_FLAGS` bandeira RUNTIME_INFO_UPGRADE_VERSION `runtimeInfoFlags` nas enumerações para o parâmetro.  
  
 O `GetRequestedRuntimeInfo` método não retorna a versão CLR mais recente nas seguintes circunstâncias:  
  
- Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma determinada versão CLR. Observe que o .NET Framework usará o arquivo de `pConfigurationFile` configuração mesmo se você especificar nulo para o parâmetro.  
  
- O método [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) foi chamado especificando uma versão CLR anterior.  
  
- Um aplicativo que foi compilado para uma versão CLR anterior está atualmente em execução.  
  
 Para `runtimeInfoFlags` o parâmetro, você pode especificar apenas uma `RUNTIME_INFO_FLAGS` das constantes de arquitetura da enumeração de cada vez:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Função GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
