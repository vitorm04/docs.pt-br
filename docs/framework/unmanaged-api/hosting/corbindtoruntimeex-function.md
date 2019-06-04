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
ms.openlocfilehash: 4b45efb634ca9b88768d6e30884085f28ad17b7c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490593"
---
# <a name="corbindtoruntimeex-function"></a>Função CorBindToRuntimeEx
Habilita hosts não gerenciados para carregar o common language runtime (CLR) em um processo. O [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) e `CorBindToRuntimeEx` funções executam a mesma operação, mas o `CorBindToRuntimeEx` função permite que você defina sinalizadores para especificar o comportamento do CLR.  
  
 Essa função foi preterida no .NET Framework 4.  
  
 Essa função usa um conjunto de parâmetros que permitem que um host fazer o seguinte:  
  
- Especifique a versão do tempo de execução que será carregado.  
  
- Indique se a compilação do servidor ou estação de trabalho deve ser carregada.  
  
- Controle se a coleta de lixo simultânea ou coleta de lixo não simultânea é feita.  
  
> [!NOTE]
>  Não há suporte para a coleta de lixo simultânea em aplicativos em execução WOW64 x86 emulator em sistemas de 64 bits que implementam a arquitetura Intel Itanium (chamada anteriormente de IA-64). Para obter mais informações sobre como usar WOW64 em sistemas Windows de 64 bits, consulte [aplicativos de 32 bits em execução](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Controle se os assemblies são carregados como domínio neutro.  
  
- Obter um ponteiro de interface para um [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) que pode ser usado para definir opções adicionais para configurar uma instância do CLR antes que ele é iniciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 [in] Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.  
  
 Um número de versão no .NET Framework consiste em quatro partes separadas por pontos: *Major*. A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número de versão (por exemplo, "v1.0.1529").  
  
 Algumas versões do CLR são instaladas com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR. Por padrão, o shim de inicialização avalia `pwszVersion` contra declarações de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada. Um host pode forçar o shim a ignorar a avaliação de política e carregar a versão exata especificada em `pwszVersion` , passando um valor de `STARTUP_LOADER_SAFEMODE` para o `startupFlags` parâmetro, conforme descrito abaixo.  
  
 Se o chamador especificar null para `pwszVersion`, `CorBindToRuntimeEx` identifica o conjunto de tempo de execução instalado cujos números da versão são menores do que o tempo de execução do .NET Framework 4 e carrega a versão mais recente do tempo de execução a partir desse conjunto. Ele não carregará o .NET Framework 4 ou posterior e falhará se nenhuma versão anterior instalada. Observe que passar null não fornece o host nenhum controle sobre qual versão do tempo de execução é carregada. Embora essa abordagem pode ser apropriada em alguns cenários, é altamente recomendável que o host forneça uma versão específica para carregar.  
  
 `pwszBuildFlavor`  
 [in] Uma cadeia de caracteres que especifica se a carga do servidor ou a compilação de estação de trabalho do CLR. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para tirar proveito de vários processadores para coletas de lixo e a compilação de estação de trabalho é otimizada para aplicativos cliente em execução em um computador de processador único.  
  
 Se `pwszBuildFlavor` é definido como nulo, a compilação de estação de trabalho é carregada. Ao executar em um computador de processador único, a compilação de estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` é definido como `svr`. No entanto, se `pwszBuildFlavor` é definido como `svr` e coleta de lixo simultânea for especificada (consulte a descrição do `startupFlags` parâmetro), a compilação do servidor é carregada.  
  
 `startupFlags`  
 [in] Uma combinação de valores de [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração. Esses sinalizadores de coleta de lixo simultânea, código de domínio neutro e o comportamento do controlam a `pwszVersion` parâmetro. O padrão é domínio único se nenhum sinalizador for definido. Os seguintes valores são válidos:  
  
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
  
 Para obter descrições desses sinalizadores, consulte o [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração.  
  
 `rclsid`  
 [in] O `CLSID` da coclass que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface. Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] O `IID` da interface solicitada do `rclsid`. Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] O ponteiro de interface retornada para `riid`.  
  
## <a name="remarks"></a>Comentários  
 Se `pwszVersion` Especifica uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexto de execução e o fluxo de identidade do Windows  
 Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flua entre pontos assíncronos, como novos threads, pools de threads ou retornos de chamada do temporizador. Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto encapsula algumas informações sobre o thread em execução no momento e fluxos de qualquer ponto assíncrono, mas não nos limites do domínio de aplicativo. Da mesma forma, o <xref:System.Security.Principal.WindowsIdentity> objeto também fluxos em qualquer ponto assíncrono. Portanto, a representação atual no thread, se houver, fluxos muito.  
  
 Você pode alterar o fluxo de duas maneiras:  
  
1. Modificando o <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte a <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> métodos).  
  
2. Alterando o modo de processo padrão para o modo de compatibilidade de versão 1, onde o <xref:System.Security.Principal.WindowsIdentity> objeto não flua entre qualquer ponto assíncrono, independentemente do <xref:System.Threading.ExecutionContext> configurações no thread atual. Como alterar o modo padrão depende se você usar uma interface de hospedagem não gerenciada ou um executável gerenciado para carregar o CLR:  
  
    1. Para executáveis gerenciados, você deve definir a `enabled` atributo o [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elemento a ser `true`.  
  
    2. Para não-gerenciados de interfaces de hospedagem, defina a `STARTUP_LEGACY_IMPERSONATION` sinalizador na `startupFlags` parâmetro ao chamar o `CorBindToRuntimeEx` função.  
  
     O modo de compatibilidade de versão 1 se aplica a todo o processo e para todos os domínios de aplicativo no processo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
