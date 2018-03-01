---
title: "Função CorBindToRuntimeHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6d69f39aa74665843b0bf91407e764ea67f41d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimehost-function"></a>Função CorBindToRuntimeHost
Permite que os hosts carregar uma versão especificada do common language runtime (CLR) em um processo.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwszVersion`  
 [in] Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.  
  
 Um número de versão do .NET Framework consiste em quatro partes separadas por pontos: *Revision*. A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido as primeiras três partes do número de versão (por exemplo, "v1.0.1529").  
  
 Algumas versões do CLR são instalados com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR. Por padrão, a correção de inicialização avalia `pwszVersion` em declarações de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada. Um host pode forçar a correção para ignorar a avaliação de política e carregar a versão exata especificada no `pwszVersion` passando um valor de STARTUP_LOADER_SAFEMODE para o `startupFlags` parâmetro.  
  
 Se `pwszVersion` é `null,` o método não carregar qualquer versão do CLR. Em vez disso, ele retorna CLR_E_SHIM_RUNTIMELOAD, que indica que ele não pôde carregar o tempo de execução.  
  
 `pwszBuildFlavor`  
 [in] Uma cadeia de caracteres que especifica se a carga do servidor ou a compilação de estação de trabalho do CLR. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para tirar proveito de vários processadores para coletas de lixo e a compilação de estação de trabalho é otimizada para aplicativos de cliente em execução em um computador com processador único.  
  
 Se `pwszBuildFlavor` for definido como null, a compilação de estação de trabalho está carregada. Quando em execução em um computador com processador único, a compilação de estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` é definido como `svr`. No entanto, se `pwszBuildFlavor` é definido como `svr` e coleta de lixo simultânea for especificada (consulte a descrição do `startupFlags` parâmetro), a compilação do servidor é carregada.  
  
> [!NOTE]
>  Não há suporte para a coleta de lixo simultânea em aplicativos em execução o WOW64 x86 emulador em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamado de IA-64). Para obter mais informações sobre como usar o WOW64 em sistemas de 64 bits do Windows, consulte [aplicativos em execução de 32 bits](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).  
  
 `pwszHostConfigFile`  
 [in] O nome de um arquivo de configuração de host que especifica a versão do CLR para carregar. Se o nome do arquivo não incluir um caminho totalmente qualificado, o arquivo deve para estar no mesmo diretório que o executável que está fazendo a chamada.  
  
 `pReserved`  
 [in] Reservado para extensibilidade futura.  
  
 `startupFlags`  
 [in] Um conjunto de sinalizadores que controla o comportamento de coleta de lixo simultânea e código de domínio neutro de `pwszVersion` parâmetro. O padrão é o único domínio se nenhum sinalizador for definido. Para obter uma lista de valores com suporte, consulte o [enumeração STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface. Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] O `IID` da interface que você está solicitando. Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Um ponteiro de interface para a versão do tempo de execução que foi carregada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
