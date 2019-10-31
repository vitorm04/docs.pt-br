---
title: Funções de hospedagem CLR reprovadas
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 62773ce526b1f21c57ab85a106708589fcf92f6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138268"
---
# <a name="deprecated-clr-hosting-functions"></a>Funções de hospedagem CLR reprovadas
Esta seção descreve as funções estáticas globais não gerenciadas que as versões anteriores da API de hospedagem usavam.  
  
 Com exceção das funções de infraestrutura (funções de`_Cor*`), que são usadas somente pelo .NET Framework, essas funções foram preteridas no .NET Framework 4.  
  
## <a name="activation-functions"></a>Funções de ativação  
 [Função ClrCreateManagedInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Preterido. Cria uma instância do tipo gerenciado especificado.  
  
 [Função CoInitializeCor](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Obsoleto. Para inicializar o Common Language Runtime (CLR), use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [Função CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Preterido. Garante que o mecanismo de execução do CLR seja carregado em um processo. Em vez disso, use o método [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .  
  
 [Função CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Preterido. Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML.  
  
 [Função CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Preterido. Permite que hosts não gerenciados carreguem o CLR em um processo.  
  
 [Função CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Preterido. Carrega o CLR em um processo usando informações de versão lidas de um arquivo XML.  
  
 [Função CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Preterido. Permite que hosts não gerenciados carreguem o CLR em um processo e permite que você defina sinalizadores para especificar o comportamento do CLR.  
  
 [Função CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Preterido. Permite que os hosts carreguem uma versão especificada do CLR em um processo.  
  
 [Função GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Preterido. Obtém o número de versão do CLR necessário.  
  
 [Função GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Preterido. Retorna o diretório de instalação do CLR que é carregado no processo.  
  
 [Função GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Preterido. Obtém o endereço da função especificada que é exportada da última versão instalada do CLR.  
  
 [Função GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Preterido. Obtém informações de versão e diretório sobre o CLR solicitado por um aplicativo.  
  
## <a name="clr-version-functions"></a>Funções de versão do CLR  
 As funções nesta seção retornam uma versão do CLR; Eles não ativam o CLR.  
  
 [Função GetCORVersion](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Preterido. Retorna o número de versão do CLR que está sendo executado no processo atual.  
  
 [Função GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Preterido. Obtém as informações de versão do CLR do arquivo especificado, usando o buffer especificado.  
  
 [Função GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Preterido. Obtém o número de versão do CLR solicitado pelo aplicativo especificado. Se essa versão não estiver instalada, o obterá a versão mais recente instalada antes da versão solicitada.  
  
 [Função GetRequestedRuntimeVersionForCLSID](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Preterido. Obtém as informações de versão do CLR apropriadas para a classe com o CLSID especificado.  
  
 [Função GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Preterido. Obtém o número de versão do CLR associado ao identificador de processo especificado.  
  
 [Função LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Preterido. Permite que o host determine qual versão do CLR será usada dentro do processo antes de inicializar explicitamente o CLR.  
  
## <a name="hosting-functions"></a>Funções de hospedagem  
 [Função CallFunctionShim](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Preterido. Faz uma chamada para a função que tem o nome e os parâmetros especificados na biblioteca especificada.  
  
 [Função CoEEShutDownCOM](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Preterido. Descarrega um assembly COM do processo.  
  
 [Função CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Preterido. Desliga o processo atual não gerenciado.  
  
 [Função CorLaunchApplication](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Preterido. Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.  
  
 [Função CorMarkThreadInThreadPool](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Preterido. Marca o thread do pool de threads em execução no momento para a execução do código gerenciado. A partir do .NET Framework versão 2,0, essa função não tem nenhum efeito. Ela não é necessária e pode ser removida do seu código.  
  
 [Função CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Obsoleto. O CLR não pode ser descarregado de um processo.  
  
 [Função CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Obsoleto.  
  
 [Função CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Preterido. Cria um objeto [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) com base nas informações de versão especificadas.  
  
 [Função CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Preterido. Cria um objeto [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .  
  
 [Função DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Preterido. Destrói um objeto [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .  
  
 [Ponteiro de função FExecuteInAppDomainCallback](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Preterido. Aponta para uma função que o CLR chama para executar código gerenciado.  
  
 [Ponteiro de função FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Preterido. Aponta para uma função que o CLR chama para notificar o host de que a inicialização foi iniciada ou concluída.  
  
 [Função GetCLRIdentityManager](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Preterido. Obtém um ponteiro para uma interface que permite que o CLR gerencie identidades.  
  
 [Função LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Preterido. Carrega uma versão especificada de uma .NET Framework DLL.  
  
 [Função LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Preterido. Traduz um valor HRESULT em uma mensagem de erro usando a cultura padrão do thread atual.  
  
 [Função LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Preterido. Traduz um valor HRESULT para uma mensagem de erro apropriada para a cultura especificada.  
  
 [Ponteiro de função LPOVERLAPPED_COMPLETION_ROUTINE](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Preterido. Aponta para uma função que notifica o host quando uma e/s sobreposta (ou seja, assíncrona) para um dispositivo for concluída.  
  
 [Ponteiro de função LPTHREAD_START_ROUTINE](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Preterido. Aponta para uma função que notifica o host que um thread começou a ser executado.  
  
 [Função RunDll32ShimW](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Preterido. Executa o comando especificado.  
  
 [Ponteiro de função WAITORTIMERCALLBACK](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Preterido. Aponta para uma função que notifica o host de que um identificador de espera foi sinalizado ou atingiu o tempo limite.  
  
## <a name="infrastructure-functions"></a>Funções de infraestrutura  
 As funções nesta seção são para uso apenas pelo .NET Framework.  
  
 [Função _CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly de DLL e começa a execução.  
  
 [Função _CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e começa a execução.  
  
 [Função _CorExeMain2](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Executa o ponto de entrada no código mapeado de memória especificado. Essa função é chamada pelo carregador do sistema operacional.  
  
 [Função _CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.  
  
 [Função _CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Valida as imagens de módulo gerenciado e notifica o carregador do sistema operacional depois que elas tiverem sido carregadas.  
  
## <a name="see-also"></a>Consulte também

- [.NET Framework 4 hospedando funções estáticas globais](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
