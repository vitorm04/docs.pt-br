---
title: Função CorBindToRuntime
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138305"
---
# <a name="corbindtoruntime-function"></a>Função CorBindToRuntime
Permite que hosts não gerenciados carreguem o Common Language Runtime (CLR) em um processo.  
  
 Essa função foi preterida no .NET Framework 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwszVersion`  
 no Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.  
  
 Um número de versão no .NET Framework consiste em quatro partes separadas por pontos: *Major. Minor. Build. Revision*. A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número de versão (por exemplo, "v 1.0.1529").  
  
 Algumas versões do CLR são instaladas com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR. Por padrão, o Shim de inicialização avalia `pwszVersion` em relação a instruções de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada. Um host pode forçar o Shim a ignorar a avaliação da política e carregar a versão exata especificada em `pwszVersion` passando um valor de `STARTUP_LOADER_SAFEMODE` para o parâmetro `flags`, conforme descrito abaixo.  
  
 Se o chamador especificar NULL para `pwszVersion`, a versão mais recente do tempo de execução será carregada. A passagem de NULL fornece ao host nenhum controle sobre qual versão do tempo de execução está carregada. Embora essa abordagem possa ser apropriada em alguns cenários, é altamente recomendável que o host forneça uma versão específica para carregar.  
  
 `pwszBuildFlavor`  
 no Uma cadeia de caracteres que especifica se o servidor ou a compilação da estação de trabalho do CLR deve ser carregada. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para aproveitar vários processadores para coletas de lixo e a compilação da estação de trabalho é otimizada para aplicativos cliente em execução em um computador com um único processador.  
  
 Se `pwszBuildFlavor` for definido como NULL, a compilação da estação de trabalho será carregada. Durante a execução em um computador com um único processador, a compilação da estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` estiver definida como `svr`. No entanto, se `pwszBuildFlavor` for definido como `svr` e a coleta de lixo simultânea for especificada (consulte a descrição do parâmetro `flags`), a compilação do servidor será carregada.  
  
 `rclsid`  
 no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) . Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 no A `IID` da interface solicitada do `rclsid`. Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 fora O ponteiro de interface retornado para `riid`.  
  
## <a name="remarks"></a>Comentários  
 Se `pwszVersion` especificar uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` retornará um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexto de execução e fluxo de identidade do Windows  
 Na versão 1 do CLR, o objeto <xref:System.Security.Principal.WindowsIdentity> não flui em pontos assíncronos, como novos threads, pools de threads ou retornos de chamada de temporizador. Na versão 2,0 do CLR, um objeto <xref:System.Threading.ExecutionContext> encapsula algumas informações sobre o thread em execução no momento e o flui em qualquer ponto assíncrono, mas não entre os limites do domínio do aplicativo. Da mesma forma, o objeto <xref:System.Security.Principal.WindowsIdentity> também flui em qualquer ponto assíncrono. Portanto, a representação atual no thread, se houver, flui também.  
  
 Você pode alterar o fluxo de duas maneiras:  
  
1. Modificando as configurações de <xref:System.Threading.ExecutionContext> para suprimir o fluxo por thread (consulte os métodos <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>).  
  
2. Alterando o modo padrão do processo para o modo de compatibilidade da versão 1, em que o objeto <xref:System.Security.Principal.WindowsIdentity> não flui em nenhum ponto assíncrono, independentemente das configurações de <xref:System.Threading.ExecutionContext> no thread atual. A maneira como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:  
  
    1. Para executáveis gerenciados, você deve definir o atributo `enabled` do elemento [\<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) como `true`.  
  
    2. Para interfaces de hospedagem não gerenciadas, defina o sinalizador `STARTUP_LEGACY_IMPERSONATION` no parâmetro `flags` ao chamar a função `CorBindToRuntimeEx`.  
  
     O modo de compatibilidade da versão 1 se aplica a todo o processo e a todos os domínios de aplicativo no processo.  
  
## <a name="remarks"></a>Comentários  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e `CorBindToRuntime` executam a mesma operação, mas a função `CorBindToRuntimeEx` permite que você defina sinalizadores para especificar o comportamento do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
