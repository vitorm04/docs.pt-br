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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36b15c607026ea9ce583ecda02bcb8ac43900310
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435745"
---
# <a name="corbindtoruntime-function"></a>Função CorBindToRuntime
Habilita a hosts não gerenciados para carregar o common language runtime (CLR) em um processo.  
  
 Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pwszVersion`  
 [in] Uma cadeia de caracteres que descreve a versão do CLR que você deseja carregar.  
  
 Um número de versão do .NET Framework consiste em quatro partes separadas por pontos: *Revision*. A cadeia de caracteres passada como `pwszVersion` deve começar com o caractere "v" seguido as primeiras três partes do número de versão (por exemplo, "v1.0.1529").  
  
 Algumas versões do CLR são instalados com uma declaração de política que especifica a compatibilidade com versões anteriores do CLR. Por padrão, a correção de inicialização avalia `pwszVersion` em declarações de política e carrega a versão mais recente do tempo de execução que é compatível com a versão que está sendo solicitada. Um host pode forçar a correção para ignorar a avaliação de política e carregar a versão exata especificada no `pwszVersion` passando um valor de `STARTUP_LOADER_SAFEMODE` para o `flags` parâmetro, conforme descrito abaixo.  
  
 Se o chamador especificar null para `pwszVersion`, a versão mais recente do tempo de execução é carregada. Passando null não fornece o host nenhum controle sobre qual versão do tempo de execução é carregado. Embora essa abordagem pode ser apropriada em alguns cenários, é altamente recomendável que o host de fornece uma versão específica para carregar.  
  
 `pwszBuildFlavor`  
 [in] Uma cadeia de caracteres que especifica se a carga do servidor ou a compilação de estação de trabalho do CLR. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para tirar proveito de vários processadores para coletas de lixo e a compilação de estação de trabalho é otimizada para aplicativos de cliente em execução em um computador com processador único.  
  
 Se `pwszBuildFlavor` for definido como null, a compilação de estação de trabalho está carregada. Quando em execução em um computador com processador único, a compilação de estação de trabalho é sempre carregada, mesmo se `pwszBuildFlavor` é definido como `svr`. No entanto, se `pwszBuildFlavor` é definido como `svr` e coleta de lixo simultânea for especificada (consulte a descrição do `flags` parâmetro), a compilação do servidor é carregada.  
  
 `rclsid`  
 [in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface. Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] O `IID` da interface solicitada de `rclsid`. Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] O ponteiro de interface retornado para `riid`.  
  
## <a name="remarks"></a>Comentários  
 Se `pwszVersion` Especifica uma versão de tempo de execução que não existe, `CorBindToRuntimeEx` retorna um valor HRESULT de CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Contexto de execução e o fluxo de identidade do Windows  
 Na versão 1 do CLR, o <xref:System.Security.Principal.WindowsIdentity> não fluxo do objeto pelos pontos assíncronos como novos threads, pools de threads ou retornos de chamada timer. Na versão 2.0 do CLR, um <xref:System.Threading.ExecutionContext> objeto envolve algumas informações sobre o thread em execução no momento e fluxos de em qualquer ponto assíncrono, mas não nos limites do domínio de aplicativo. Da mesma forma, o <xref:System.Security.Principal.WindowsIdentity> objeto também passa em qualquer ponto assíncrono. Portanto, a representação atual no thread, se houver, fluxos muito.  
  
 Você pode alterar o fluxo de duas maneiras:  
  
1.  Modificando o <xref:System.Threading.ExecutionContext> configurações para suprimir o fluxo em uma base por thread (consulte o <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, e <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> métodos).  
  
2.  Alterando o modo de processo padrão para o modo de compatibilidade de versão 1, onde o <xref:System.Security.Principal.WindowsIdentity> não fluxo do objeto em qualquer ponto assíncrono, independentemente do <xref:System.Threading.ExecutionContext> configurações no thread atual. Como alterar o modo padrão depende se você usar uma interface de hospedagem não gerenciada ou um executável gerenciado para carregar o CLR:  
  
    1.  Executáveis gerenciados, você deve definir o `enabled` atributo do [ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) elemento `true`.  
  
    2.  Para não gerenciado interfaces de hospedagem, defina o `STARTUP_LEGACY_IMPERSONATION` sinalizador no `flags` parâmetro ao chamar o `CorBindToRuntimeEx` função.  
  
     O modo de compatibilidade de versão 1 se aplica a todo o processo e todos os domínios de aplicativo no processo.  
  
## <a name="remarks"></a>Comentários  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e `CorBindToRuntime` executar a mesma operação, mas o `CorBindToRuntimeEx` função permite que você defina os sinalizadores para especificar o comportamento do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
