---
title: Função CorBindToRuntimeEx
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f31ae29efee9b353c2dcc679724db73da5444e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969424"
---
# <a name="corbindtoruntimeex-function"></a>Função CorBindToRuntimeEx
Permite que hosts não gerenciados carreguem o Common Language Runtime (CLR) em um processo. O [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) e `CorBindToRuntimeEx` as funções executam a mesma operação, `CorBindToRuntimeEx` mas a função permite que você defina sinalizadores para especificar o comportamento do CLR.  
  
 Essa função foi preterida no .NET Framework 4.  
  
 Essa função usa um conjunto de parâmetros que permitem que um host faça o seguinte:  
  
- Especifique a versão do tempo de execução que será carregada.  
  
- Indique se a compilação do servidor ou da estação de trabalho deve ser carregada.  
  
- Controle se a coleta de lixo simultânea ou a coleta de lixo não simultânea está concluída.  
  
> [!NOTE]
> Não há suporte para a coleta de lixo simultânea em aplicativos que executam o emulador x86 WOW64 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada IA-64). Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 bits, consulte [executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Controlar se os assemblies são carregados como domínio neutro.  
  
- Obtenha um ponteiro de interface para um [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) que possa ser usado para definir opções adicionais para configurar uma instância do CLR antes que ela seja iniciada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwszVersion`  
 no Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.  
  
 Um número de versão no .NET Framework consiste em quatro partes separadas por pontos: *Major. Minor. Build. Revision*. A cadeia de caracteres `pwszVersion` passada como deve começar com o caractere "v" seguido pelas três primeiras partes do número de versão (por exemplo, "v 1.0.1529").  
  
 Algumas versões do CLR são instaladas com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR. Por padrão, o Shim de inicialização é `pwszVersion` avaliado em relação a instruções de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada. Um host pode forçar o Shim a ignorar a avaliação da política e carregar a versão exata `pwszVersion` especificada no passando um valor `STARTUP_LOADER_SAFEMODE` de para `startupFlags` o parâmetro, conforme descrito abaixo.  
  
 Se o chamador especificar NULL para `pwszVersion`, `CorBindToRuntimeEx` o identificará o conjunto de tempos de execução instalados cujos números de versão são menores do que o tempo de execução do .NET Framework 4 e carregará a versão mais recente do tempo de execução desse conjunto. Ele não carregará o .NET Framework 4 ou posterior e falhará se nenhuma versão anterior estiver instalada. Observe que a passagem de NULL fornece ao host nenhum controle sobre qual versão do tempo de execução é carregada. Embora essa abordagem possa ser apropriada em alguns cenários, é altamente recomendável que o host forneça uma versão específica para carregar.  
  
 `pwszBuildFlavor`  
 no Uma cadeia de caracteres que especifica se o servidor ou a compilação da estação de trabalho do CLR deve ser carregada. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para aproveitar vários processadores para coletas de lixo e a compilação da estação de trabalho é otimizada para aplicativos cliente em execução em um computador com um único processador.  
  
 Se `pwszBuildFlavor` é definido como NULL, a compilação da estação de trabalho é carregada. Durante a execução em um computador com um único processador, a compilação da estação de trabalho é `pwszBuildFlavor` sempre carregada, `svr`mesmo se estiver definida como. No entanto `pwszBuildFlavor` , se for `svr` definido como e a coleta de lixo simultânea for especificada ( `startupFlags` consulte a descrição do parâmetro), a compilação do servidor será carregada.  
  
 `startupFlags`  
 no Uma combinação de valores da enumeração [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) . Esses sinalizadores controlam a coleta de lixo simultânea, o código de domínio neutro e o comportamento `pwszVersion` do parâmetro. O padrão é domínio único se nenhum sinalizador for definido. Os seguintes valores são válidos:  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 Para obter descrições desses sinalizadores, consulte a enumeração [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
 `rclsid`  
 no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) . Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 no O `IID` da interface solicitada de `rclsid`. Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 fora O ponteiro de interface retornado `riid`para.  
  
## <a name="remarks"></a>Comentários  
 Se `pwszVersion` o especificar uma versão de tempo de execução que `CorBindToRuntimeEx` não existe, o retornará um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexto de execução e fluxo de identidade do Windows  
 Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flui em pontos assíncronos, como novos threads, pools de threads ou retornos de chamada de temporizador. Na versão 2,0 do CLR, um <xref:System.Threading.ExecutionContext> objeto encapsula algumas informações sobre o thread em execução no momento e o flui em qualquer ponto assíncrono, mas não entre os limites do domínio do aplicativo. Da mesma forma <xref:System.Security.Principal.WindowsIdentity> , o objeto também flui em qualquer ponto assíncrono. Portanto, a representação atual no thread, se houver, flui também.  
  
 Você pode alterar o fluxo de duas maneiras:  
  
1. Modificando as <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte os <xref:System.Threading.ExecutionContext.SuppressFlow%2A>métodos <xref:System.Security.SecurityContext.SuppressFlow%2A>, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> ).  
  
2. Alterando o modo padrão do processo para o modo de compatibilidade da versão 1 <xref:System.Security.Principal.WindowsIdentity> , em que o objeto não flui em nenhum ponto assíncrono, <xref:System.Threading.ExecutionContext> independentemente das configurações no thread atual. A maneira como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:  
  
    1. Para executáveis gerenciados, você deve definir `enabled` o atributo `true` [ \<](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) do elemento de > legacyImpersonationPolicy como.  
  
    2. Para interfaces de hospedagem não gerenciadas, defina `STARTUP_LEGACY_IMPERSONATION` o sinalizador `startupFlags` no parâmetro ao chamar a `CorBindToRuntimeEx` função.  
  
     O modo de compatibilidade da versão 1 se aplica a todo o processo e a todos os domínios de aplicativo no processo.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
