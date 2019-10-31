---
title: Interface ICLRMetaHost
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: bb760f4923cc3530a28bc68180db743ee468b51d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140905"
---
# <a name="iclrmetahost-interface"></a>Interface ICLRMetaHost
Fornece métodos que retornam uma versão específica do Common Language Runtime (CLR) com base em seu número de versão, listar todos os CLRs instalados, listar todos os tempos de execução que são carregados em um processo especificado, descobrir a versão do CLR usada para compilar um assembly, sair de um processo com um desligamento de tempo de execução limpo e a associação de API herdada de consulta.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateInstalledRuntimes](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Retorna uma enumeração que contém um ponteiro de interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) válido para cada versão do CLR instalada em um computador.|  
|[Método EnumerateLoadedRuntimes](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Retorna uma enumeração que contém um ponteiro de interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) válido para cada CLR que é carregado em um determinado processo. Esse método substitui [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[Método ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Tenta desligar todos os tempos de execução carregados normalmente e, em seguida, encerra o processo. Substitui a função [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) .|  
|[Método GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Obtém a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que corresponde a uma versão CLR específica. Esse método substitui a função [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) usada com o sinalizador [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .|  
|[Método GetVersionFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Obtém a versão de compilação de .NET Framework original do assembly (armazenada nos metadados), dado seu caminho de arquivo. Esse método substitui [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[Método QueryLegacyV2RuntimeBinding](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Retorna uma interface que representa um tempo de execução ao qual a política de ativação herdada foi associada, por exemplo, usando o atributo `useLegacyV2RuntimeActivationPolicy` na entrada do arquivo de configuração do [elemento de > de inicialização de\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , pelo uso direto das APIs de ativação herdadas ou por chamando o método [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .|  
|[Método RequestRuntimeLoadedNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Garante um retorno de chamada para o ponteiro de função especificado quando uma versão do CLR é carregada pela primeira vez, mas ainda não foi iniciada. Esse método substitui [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Comentários  
 A única maneira de obter uma instância dessa interface é chamando a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) da seguinte maneira:  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
