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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176494"
---
# <a name="corbindtoruntimeex-function"></a>Função CorBindToRuntimeEx
Habilita hosts não gerenciados para carregar o tempo de execução do idioma comum (CLR) em um processo. O [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) e `CorBindToRuntimeEx` as funções executam a mesma operação, mas a `CorBindToRuntimeEx` função permite definir sinalizadores para especificar o comportamento da CLR.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
 Esta função leva um conjunto de parâmetros que permitem que um host faça o seguinte:  
  
- Especifique a versão do tempo de execução que será carregada.  
  
- Indique se a compilação do servidor ou da estação de trabalho deve ser carregada.  
  
- Controle se a coleta simultânea de lixo ou a coleta de lixo não simultânea é feita.  
  
> [!NOTE]
> A coleta de lixo simultânea não é suportada em aplicativos que executam o emulador WOW64 x86 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada iA-64). Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 [bits, consulte Executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
- Controle se os conjuntos são carregados como neutros em domínio.  
  
- Obtenha um ponteiro de interface para um [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) que pode ser usado para definir opções adicionais para configurar uma instância do CLR antes de ser iniciado.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `pwszVersion`  
 [em] Uma seqüência descrevendo a versão do CLR que você deseja carregar.  
  
 Um número de versão no Quadro .NET consiste em quatro partes separadas por períodos: *major.minor.build.revision*. A seqüência passou como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número da versão (por exemplo, "v1.0.1529").  
  
 Algumas versões do CLR são instaladas com uma declaração de política que especifica compatibilidade com versões anteriores da CLR. Por padrão, o shim `pwszVersion` de inicialização avalia contra as instruções de diretiva e carrega a versão mais recente do tempo de execução compatível com a versão que está sendo solicitada. Um host pode forçar o shim a pular a `pwszVersion` avaliação da diretiva `STARTUP_LOADER_SAFEMODE` e `startupFlags` carregar a versão exata especificada, passando um valor para o parâmetro, conforme descrito abaixo.  
  
 Se o chamador `pwszVersion`especificar nulo para , `CorBindToRuntimeEx` identificar o conjunto de tempos de execução instalados cujos números de versão são inferiores ao tempo de execução .NET Framework 4 e carregar a versão mais recente do tempo de execução a partir desse conjunto. Ele não carregará o .NET Framework 4 ou posterior, e falhará se nenhuma versão anterior estiver instalada. Observe que a passagem nula não dá ao host nenhum controle sobre qual versão do tempo de execução é carregada. Embora essa abordagem possa ser apropriada em alguns cenários, é fortemente recomendável que o host forneça uma versão específica para carregar.  
  
 `pwszBuildFlavor`  
 [em] Uma seqüência que especifica se deve carregar o servidor ou a compilação da estação de trabalho da CLR. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para tirar proveito de vários processadores para coleta de lixo, e a construção da estação de trabalho é otimizada para aplicativos clientes em execução em uma máquina de processador único.  
  
 Se `pwszBuildFlavor` estiver definido como nulo, a construção da estação de trabalho está carregada. Ao ser executado em uma máquina de processador único, a `pwszBuildFlavor` compilação `svr`da estação de trabalho está sempre carregada, mesmo que esteja configurada para . No entanto, `pwszBuildFlavor` `svr` se for definida a coleta de lixo `startupFlags` simultânea (veja a descrição do parâmetro), a compilação do servidor será carregada.  
  
 `startupFlags`  
 [em] Uma combinação de valores da [enumeração STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) Essas bandeiras controlam a coleta simultânea de lixo, `pwszVersion` o código neutro de domínio e o comportamento do parâmetro. O padrão é um único domínio se nenhum sinalizador for definido. Os seguintes valores são válidos:  
  
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
  
 Para descrições dessas bandeiras, consulte a [enumeração STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)  
  
 `rclsid`  
 [em] A `CLSID` coclasse que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou a interface [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Os valores suportados são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [em] A `IID` da interface solicitada `rclsid`de . Os valores suportados são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [fora] O ponteiro de `riid`interface retornado para .  
  
## <a name="remarks"></a>Comentários  
 Se `pwszVersion` especificar uma versão em tempo `CorBindToRuntimeEx` de execução que não existe, retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexto de execução e fluxo da identidade do Windows  
 Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> objeto não flui através de pontos assíncronos, como novos segmentos, pools de segmentos ou retornos de tempo. Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto envolve algumas informações sobre o segmento em execução atualmente e flui-o através de qualquer ponto assíncrono, mas não através dos limites do domínio do aplicativo. Da mesma <xref:System.Security.Principal.WindowsIdentity> forma, o objeto também flui através de qualquer ponto assíncrono. Portanto, a representação atual no segmento, se houver, também flui.  
  
 Você pode alterar o fluxo de duas maneiras:  
  
1. Modificando as <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo por segmento <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>(ver <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> os métodos e métodos).  
  
2. Alterando o modo padrão do processo para o <xref:System.Security.Principal.WindowsIdentity> modo de compatibilidade da versão 1, onde <xref:System.Threading.ExecutionContext> o objeto não flui em nenhum ponto assíncrono, independentemente das configurações do segmento atual. A forma como você altera o modo padrão depende se você usa um executável gerenciado ou uma interface de hospedagem não gerenciada para carregar o CLR:  
  
    1. Para executáveis gerenciados, você `enabled` deve definir o atributo do `true`elemento [ \<legacySPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) para .  
  
    2. Para interfaces de hospedagem `STARTUP_LEGACY_IMPERSONATION` não gerenciadas, defina o sinalizador no parâmetro ao `startupFlags` chamar a `CorBindToRuntimeEx` função.  
  
     O modo de compatibilidade da versão 1 aplica-se a todo o processo e a todos os domínios do aplicativo no processo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
