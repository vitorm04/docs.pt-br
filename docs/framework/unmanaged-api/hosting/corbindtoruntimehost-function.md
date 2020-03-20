---
title: Função CorBindToRuntimeHost
ms.date: 03/30/2017
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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176481"
---
# <a name="corbindtoruntimehost-function"></a>Função CorBindToRuntimeHost
Permite que os hosts carreguem uma versão especificada do tempo de execução do idioma comum (CLR) em um processo.  
  
 Esta função foi depreciada no Quadro .NET 4.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
  
## <a name="parameters"></a>parâmetros  
 `pwszVersion`  
 [em] Uma string que descreve a versão do CLR que você deseja carregar.  
  
 Um número de versão no Quadro .NET consiste em quatro partes separadas por períodos: *major.minor.build.revision*. A seqüência passou como `pwszVersion` deve começar com o caractere "v" seguido pelas três primeiras partes do número da versão (por exemplo, "v1.0.1529").  
  
 Algumas versões do CLR são instaladas com uma declaração de política que especifica compatibilidade com versões anteriores da CLR. Por padrão, o shim `pwszVersion` de inicialização avalia contra as instruções de diretiva e carrega a versão mais recente do tempo de execução compatível com a versão que está sendo solicitada. Um host pode forçar o shim a pular a `pwszVersion` avaliação da diretiva e `startupFlags` carregar a versão exata especificada, passando um valor de STARTUP_LOADER_SAFEMODE para o parâmetro.  
  
 Se `pwszVersion` `null,` for o método não carregar nenhuma versão do CLR. Em vez disso, ele retorna CLR_E_SHIM_RUNTIMELOAD, o que indica que ele não conseguiu carregar o tempo de execução.  
  
 `pwszBuildFlavor`  
 [em] Uma seqüência que especifica se deve carregar o servidor ou a compilação da estação de trabalho da CLR. Os valores válidos são `svr` e `wks`. A compilação do servidor é otimizada para tirar proveito de vários processadores para coleta de lixo, e a construção da estação de trabalho é otimizada para aplicativos clientes em execução em uma máquina de processador único.  
  
 Se `pwszBuildFlavor` estiver definido como nulo, a construção da estação de trabalho está carregada. Ao ser executado em uma máquina de processador único, a `pwszBuildFlavor` compilação `svr`da estação de trabalho está sempre carregada, mesmo que esteja configurada para . No entanto, `pwszBuildFlavor` `svr` se for definida a coleta de lixo `startupFlags` simultânea (veja a descrição do parâmetro), a compilação do servidor será carregada.  
  
> [!NOTE]
> A coleta de lixo simultânea não é suportada em aplicativos que executam o emulador WOW64 x86 em sistemas de 64 bits que implementam a arquitetura Intel Itanium (anteriormente chamada iA-64). Para obter mais informações sobre como usar o WOW64 em sistemas Windows de 64 [bits, consulte Executando aplicativos de 32 bits](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 [em] O nome de um arquivo de configuração host que especifica a versão do CLR para carregar. Se o nome do arquivo não incluir um caminho totalmente qualificado, o arquivo é assumido como sendo no mesmo diretório que o executável que está fazendo a chamada.  
  
 `pReserved`  
 [em] Reservado para a extensibilidade futura.  
  
 `startupFlags`  
 [em] Um conjunto de bandeiras que controla a coleta de lixo `pwszVersion` simultânea, o código neutro de domínio e o comportamento do parâmetro. O padrão é um único domínio se nenhum sinalizador for definido. Para obter uma lista de valores suportados, consulte a [enumeração STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [em] A `CLSID` coclasse que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou a interface [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Os valores suportados são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.  
  
 `riid`  
 [em] A `IID` interface que você está solicitando. Os valores suportados são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.  
  
 `ppv`  
 [fora] Um ponteiro de interface para a versão do tempo de execução que foi carregado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [Interface ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
