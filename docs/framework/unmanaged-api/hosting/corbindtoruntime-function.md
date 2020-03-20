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
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176507"
---
# <a name="corbindtoruntime-function"></a>Função CorBindToRuntime
Habilita hosts não gerenciados para carregar o tempo de execução do idioma comum (CLR) em um processo.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
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
  
## <a name="parameters"></a>parâmetros  
 `pwszVersion`  
 [em] Uma seqüência descrevendo a versão do CLR que você deseja carregar.  
  
 Um número de versão no Quadro .NET consiste em quatro partes separadas por períodos: *major.minor.build.revision*. A seqüência passou como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número da versão (por exemplo, "v1.0.1529").  
  
 Algumas versões do CLR são instaladas com uma declaração de política que especifica compatibilidade com versões anteriores da CLR. Por padrão, o shim `pwszVersion` de inicialização avalia contra as instruções de diretiva e carrega a versão mais recente do tempo de execução compatível com a versão que está sendo solicitada. Um host pode forçar o shim a pular a `pwszVersion` avaliação da diretiva `STARTUP_LOADER_SAFEMODE` e `flags` carregar a versão exata especificada, passando um valor para o parâmetro, conforme descrito abaixo.  
  
 Se o chamador `pwszVersion`especificar nulo para , a versão mais recente do tempo de execução será carregada. Passar nulo não dá ao host controle sobre qual versão do tempo de execução é carregada. Embora essa abordagem possa ser apropriada em alguns cenários, é fortemente recomendável que o host forneça uma versão específica para carregar.  
  
 `pwszBuildFlavor`  
 [em] Uma seqüência que especifica se deve carregar o servidor ou a compilação da estação de trabalho da CLR. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para tirar proveito de vários processadores para coleta de lixo, e a construção da estação de trabalho é otimizada para aplicativos clientes em execução em uma máquina de processador único.  
  
 Se `pwszBuildFlavor` estiver definido como nulo, a construção da estação de trabalho está carregada. Ao ser executado em uma máquina de processador único, a `pwszBuildFlavor` compilação `svr`da estação de trabalho está sempre carregada, mesmo que esteja configurada para . No entanto, `pwszBuildFlavor` `svr` se for definida a coleta de lixo `flags` simultânea (veja a descrição do parâmetro), a compilação do servidor será carregada.  
  
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
  
    2. Para interfaces de hospedagem `STARTUP_LEGACY_IMPERSONATION` não gerenciadas, defina o sinalizador no parâmetro ao `flags` chamar a `CorBindToRuntimeEx` função.  
  
     O modo de compatibilidade da versão 1 aplica-se a todo o processo e a todos os domínios do aplicativo no processo.  
  
## <a name="remarks"></a>Comentários  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` e executar a mesma `CorBindToRuntimeEx` operação, mas a função permite definir sinalizadores para especificar o comportamento da CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
