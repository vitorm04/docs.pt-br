---
title: "Diagnosticando erros com assistentes de depuração gerenciados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EHMDA
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
caps.latest.revision: 63
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8afc1ec3d5a1dab4412b16826bb32829f9b42263
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a>Diagnosticando erros com assistentes de depuração gerenciados
Os MDAs (Assistentes para depuração gerenciada) são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução. Os assistentes geram mensagens informativas sobre eventos de tempo de execução que não podem ser interceptados de outro modo. É possível usar MDAs para isolar bugs de aplicativos difíceis de encontrar que ocorrem durante a transição entre código gerenciado e não gerenciado. É possível habilitar ou desabilitar todos os MDAs adicionando uma chave ao Registro do Windows ou definindo uma variável de ambiente. Você pode habilitar MDAs específicos usando definições de configuração do aplicativo. É possível definir configurações adicionais para alguns MDAs individuais no arquivo de configuração do aplicativo. Como esses arquivos de configuração são analisados quando o tempo de execução é carregado, você deve habilitar o MDA antes da inicialização do aplicativo gerenciado. Não será possível habilitá-lo para aplicativos já iniciados.  
  
> [!NOTE]
>  Quando é habilitado, um MDA permanece ativo mesmo quando o código não está em execução em um depurador. Se um evento de MDA for acionado quando um depurador não estiver presente, a mensagem do evento será apresentada em uma caixa de diálogo de exceção sem tratamento, ainda que não seja uma exceção sem tratamento. Para evitar a caixa de diálogo, remova as configurações de habilitação de MDA quando o código não estiver em execução em um ambiente de depuração.  
  
> [!NOTE]
>  Quando o código estiver em execução no IDE (ambiente de desenvolvimento integrado) do Visual Studio, será possível evitar a exibição da caixa de diálogo da exceção para eventos de MDA específicos. Para fazer isso, no menu **Depurar**, clique em **Exceções**. (Se o menu **Depurar** não contiver um comando **Exceções**, clique em **Personalizar** no menu **Ferramentas** para adicioná-lo.) Na caixa de diálogo **Exceções**, expanda a lista **Assistentes para Depuração Gerenciada** e, em seguida, desmarque a caixa de seleção **Geradas** do MDA individual. Por exemplo, para evitar a caixa de diálogo de exceção de um [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md), desmarque a caixa de seleção **Geradas** ao lado de seu nome na lista **Assistentes para Depuração Gerenciada**. Também é possível usar essa caixa de diálogo para habilitar a exibição de caixas de diálogo de exceção do MDA.  
  
 A tabela a seguir lista os MDAs que acompanham o .NET Framework.  
  
|||  
|-|-|  
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|  
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|  
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|  
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|  
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|  
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|  
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|  
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|  
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|  
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|  
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|  
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|  
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|  
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 Por padrão, o .NET Framework ativa um subconjunto de MDAs para todos os depuradores gerenciados. Exiba o conjunto padrão no Visual Studio clicando em **Exceções** no menu **Depurar** e expandindo a lista **Assistentes para Depuração Gerenciada**.  
  
## <a name="enabling-and-disabling-mdas"></a>Habilitando e desabilitando MDAs  
 É possível habilitar e desabilitar MDAs usando uma chave do Registro, uma variável de ambiente e as definições de configuração do aplicativo. Você deve habilitar a chave do Registro ou a variável de ambiente para usar as definições de configuração do aplicativo.  
  
 No Visual Studio 2005 e em versões posteriores, quando o processo de hospedagem está habilitado, não é possível desabilitar MDAs que estejam no conjunto padrão ou habilitar MDAs que não estejam no conjunto padrão. Como é habilitado por padrão, o processo de hospedagem deve ser desabilitado explicitamente.  
  
 Para desabilitar o processo de hospedagem no Visual Studio, faça o seguinte:  
  
1.  No **Gerenciador de Soluções**, selecione um projeto.  
  
2.  No menu **Projeto**, clique em **Propriedades**.  
  
     A janela **Designer de Projeto** é exibida.  
  
3.  Clique na guia **Depurar**.  
  
4.  Na seção **Habilitar Depuradores**, desmarque a caixa de seleção **Habilitar o processo de hospedagem do Visual Studio**.  
  
 Porém, a desabilitação do processo de hospedagem pode afetar o desempenho. Você pode evitar a necessidade de desabilitar MDAs, impedindo que o Visual Studio exiba a caixa de diálogo MDA sempre que uma notificação for recebida. Para fazer isso, clique em **Exceções** no menu **Depurar**, expanda a lista **Assistentes para Depuração Gerenciada** e, em seguida, marque ou desmarque a caixa de seleção **Geradas** do MDA individual.  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a>Habilitando e desabilitando MDAs usando uma chave do Registro  
 Habilite os MDAs adicionando a subchave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA (digite REG_SZ, valor 1) no Registro do Windows. Copie o exemplo a seguir em um arquivo de texto chamado MDAEnable.reg. Abra o Editor do Registro do Windows (RegEdit.exe) e, no menu **Arquivo**, escolha **Importar**. Selecione o arquivo MDAEnable.reg para habilitar MDAs nesse computador. A definição da subchave com o valor de cadeia de caracteres 1 (e não o valor DWORD 1) habilita a leitura das configurações do MDA por meio do arquivo *ApplicationName.suffix*.mda.config file. (Por exemplo, o arquivo de configuração do MDA para o Bloco de Notas se chamaria notepad.exe.mda.config)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Se o computador estiver executando um aplicativo de 32 bits em um sistema operacional de 64 bits, a chave do MDA deverá ser definida da seguinte forma:  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Consulte [Habilitando e desabilitando MDAs usando definições de configuração específicas ao aplicativo](#appConfig) para obter mais informações. A configuração do Registro pode ser substituída pela variável de ambiente COMPLUS_MDA. Consulte [Habilitando e desabilitando MDAs usando uma variável de ambiente](#envVariable) para obter mais informações.  
  
 Para desabilitar MDAs, defina a subchave do MDA como 0 (zero) usando o Editor do Registro do Windows.  
  
 Por padrão, alguns MDAs são habilitados quando você executa um aplicativo anexado a um depurador, mesmo sem adicionar a chave do Registro. Exemplos de assistentes desse tipo são [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) e [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md). Você pode desabilitar esses assistentes executando o arquivo MDADisable.reg, como descrito antes nesta seção.  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a>Habilitando e desabilitando MDAs usando uma variável de ambiente  
 A ativação do MDA também pode ser controlada pela variável de ambiente COMPLUS_MDA, que substitui a chave do Registro. A cadeia de caracteres COMPLUS_MDA é uma lista delimitada por ponto-e-vírgula, que não diferencia maiúsculas de minúsculas, de nomes de MDA ou outras cadeias de caracteres de controle especiais. A inicialização em um depurador gerenciado ou não gerenciado habilita um conjunto de MDAs por padrão. Isso é feito implicitamente precedendo a lista separada por ponto-e-vírgula de MDAs habilitados por padrão nos depuradores ao valor da variável de ambiente ou da chave do Registro. As cadeias de caracteres de controle especiais são as seguintes:  
  
-   `0` – Desativa todos os MDAs.  
  
-   `1` – Lê as configurações do MDA por meio de *ApplicationName*.mda.config.  
  
-   `managedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável gerenciado é iniciado em um depurador.  
  
-   `unmanagedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável não gerenciado é iniciado em um depurador.  
  
 Se houver configurações conflitantes, as mais recentes substituirão as anteriores:  
  
-   `COMPLUS_MDA=0` desabilita todos os MDAs, incluindo aqueles habilitados implicitamente em um depurador.  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, além de todos os MDAs habilitados implicitamente em um depurador.  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, mas desabilita os MDAs que seriam, de outro modo, habilitados implicitamente em um depurador.  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a>Habilitando e desabilitando MDAs usando definições de configuração específicas do aplicativo  
 É possível habilitar, desabilitar e configurar alguns assistentes individualmente no arquivo de configuração do MDA para o aplicativo. Para habilitar o uso de um arquivo de configuração de aplicativo para configurar MDAs, a chave do Registro do MDA ou a variável de ambiente COMPLUS_MDA deve estar definida. O arquivo de configuração de aplicativo costuma ficar localizado no mesmo diretório do arquivo executável do aplicativo (.exe). O nome de arquivo usa o formato *ApplicationName*.mda.config; por exemplo, notepad.exe.mda.config. Os assistentes habilitados no arquivo de configuração de aplicativo podem ter atributos ou elementos projetados especificamente para controlar esse comportamento do assistente. O exemplo a seguir mostra como habilitar e configurar o [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="*"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="*"/>  
      </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
 O MDA `Marshaling` emite informações sobre o tipo gerenciado em que o marshaling está sendo realizado para um tipo não gerenciado para a transição gerenciado/não gerenciado no aplicativo. O MDA `Marshaling` também pode filtrar os nomes do método e os campos de estrutura fornecidos nos elementos filho `<methodFilter>` e `<fieldFilter>`, respectivamente.  
  
 O exemplo a seguir mostra como habilitar vários MDAs usando as configurações padrão.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion />  
    <invalidCERCall />  
    <openGenericCERCall />  
    <virtualCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
> [!IMPORTANT]
>  Ao especificar mais de um assistente em um arquivo de configuração, você deve listá-los em ordem alfabética. Por exemplo, se quiser habilitar os MDAs `virtualCERCall` e `invalidCERCall`, você deverá adicionar a entrada `<invalidCERCall />` antes da entrada `<virtualCERCall />`. Se as entradas não estiverem em ordem alfabética, será exibida uma mensagem de exceção do arquivo de configuração inválido sem tratamento.  
  
### <a name="mda-output"></a>Saída do MDA  
 A saída do MDA é semelhante à do exemplo a seguir, que mostra a saída do MDA `pInvokeStackImbalance`.  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a>Consulte também  
 [Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md)

