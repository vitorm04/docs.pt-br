---
title: Diagnosticando erros com assistentes de depuração gerenciados
ms.date: 08/14/2018
f1_keywords:
- EHMDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740942"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Diagnosticar erros com assistentes de depuração gerenciados

Os MDAs (Assistentes para depuração gerenciada) são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução. Os assistentes geram mensagens informativas sobre eventos de tempo de execução que não podem ser interceptados de outro modo. É possível usar MDAs para isolar bugs de aplicativos difíceis de encontrar que ocorrem durante a transição entre código gerenciado e não gerenciado.

Você pode [habilitar ou desabilitar](#enable-and-disable-mdas) todos os MDAs adicionando uma chave no registro do Windows ou definindo uma variável de ambiente. Você pode habilitar MDAs específicos usando definições de configuração do aplicativo. É possível definir configurações adicionais para alguns MDAs individuais no arquivo de configuração do aplicativo. Como esses arquivos de configuração são analisados quando o tempo de execução é carregado, você deve habilitar o MDA antes da inicialização do aplicativo gerenciado. Não será possível habilitá-lo para aplicativos já iniciados.

A tabela a seguir lista os MDAs que acompanham o .NET Framework:

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

Por padrão, o .NET Framework ativa um subconjunto de MDAs para todos os depuradores gerenciados. Você pode exibir o conjunto padrão no Visual Studio escolhendo **Windows** > **configurações de exceção** sobre a **depurar** menus e expandindo o **Assistentes para depuração gerenciada** lista.

![Janela de configurações de exceção no Visual Studio](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Habilitar e desabilitar MDAs

É possível habilitar e desabilitar MDAs usando uma chave do Registro, uma variável de ambiente e as definições de configuração do aplicativo. Você deve habilitar a chave do Registro ou a variável de ambiente para usar as definições de configuração do aplicativo.

> [!TIP]
> Em vez de desabilitar MDAs, você pode impedir que o Visual Studio exibindo a caixa de diálogo MDA sempre que uma notificação é recebida. Para fazer isso, escolha **Windows** > **configurações de exceção** sobre a **depurar** menu, expanda o **Managed Debugging Assistants**e, em seguida, selecione ou desmarque as **interromper quando lançada** caixa de seleção do MDA individual.

### <a name="registry-key"></a>Chave do Registro

Para habilitar MDAs, adicione a **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** subchave (digite REG_SZ, valor 1) no registro do Windows. Copie o exemplo a seguir em um arquivo de texto denominado *Mdaenable*. Abra o Editor do registro do Windows (RegEdit.exe) e para o **arquivo** menu escolher **importação**. Selecione o *Mdaenable* arquivo para habilitar MDAs nesse computador. Definição da subchave como valor de cadeia de caracteres de **1** (não o valor de DWORD **1**) permite a leitura das configurações do MDA do *Suffix*. arquivo MDA. Por exemplo, o arquivo de configuração do MDA para o bloco de notas seria nomeado Notepad.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Se o computador estiver executando um aplicativo de 32 bits em um sistema operacional de 64 bits, a chave do MDA deverá ser definida da seguinte forma:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Ver [definições de configuração específicas do aplicativo](#application-specific-configuration-settings) para obter mais informações. A configuração do Registro pode ser substituída pela variável de ambiente COMPLUS_MDA. Ver [variável de ambiente](#environment-variable) para obter mais informações.

Para desabilitar MDAs, defina a subchave do MDA para **0** (zero) usando o Editor de registro do Windows.

Por padrão, alguns MDAs são habilitados quando você executa um aplicativo anexado a um depurador, mesmo sem adicionar a chave do Registro. Você pode desabilitar esses assistentes executando o *Mdadisable* conforme descrito anteriormente nesta seção do arquivo.

### <a name="environment-variable"></a>Variável de ambiente

A ativação do MDA também pode ser controlada pela variável de ambiente COMPLUS_MDA, que substitui a chave do Registro. A cadeia de caracteres COMPLUS_MDA é uma lista delimitada por ponto-e-vírgula, que não diferencia maiúsculas de minúsculas, de nomes de MDA ou outras cadeias de caracteres de controle especiais. A inicialização em um depurador gerenciado ou não gerenciado habilita um conjunto de MDAs por padrão. Isso é feito implicitamente precedendo a lista separada por ponto-e-vírgula de MDAs habilitados por padrão nos depuradores ao valor da variável de ambiente ou da chave do Registro. As cadeias de caracteres de controle especiais são as seguintes:

- `0` – Desativa todos os MDAs.

- `1` – Lê as configurações do MDA por meio de *ApplicationName*.mda.config.

- `managedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável gerenciado é iniciado em um depurador.

- `unmanagedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável não gerenciado é iniciado em um depurador.

Se houver configurações conflitantes, as mais recentes substituirão as anteriores:

- `COMPLUS_MDA=0` desabilita todos os MDAs, incluindo aqueles habilitados implicitamente em um depurador.

- `COMPLUS_MDA=gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, além de todos os MDAs habilitados implicitamente em um depurador.

- `COMPLUS_MDA=0;gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, mas desabilita os MDAs que seriam, de outro modo, habilitados implicitamente em um depurador.

### <a name="application-specific-configuration-settings"></a>Definições de configuração específicas do aplicativo

É possível habilitar, desabilitar e configurar alguns assistentes individualmente no arquivo de configuração do MDA para o aplicativo. Para habilitar o uso de um arquivo de configuração de aplicativo para configurar MDAs, a chave do Registro do MDA ou a variável de ambiente COMPLUS_MDA deve estar definida. O arquivo de configuração de aplicativo costuma ficar localizado no mesmo diretório do arquivo executável do aplicativo (.exe). O nome de arquivo usa o formato *ApplicationName*.mda.config; por exemplo, notepad.exe.mda.config. Os assistentes habilitados no arquivo de configuração de aplicativo podem ter atributos ou elementos projetados especificamente para controlar esse comportamento do assistente.

O exemplo a seguir mostra como habilitar e configurar o [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):

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

O MDA `Marshaling` emite informações sobre o tipo gerenciado em que o marshaling está sendo realizado para um tipo não gerenciado para a transição gerenciado/não gerenciado no aplicativo. O `Marshaling` MDA também pode filtrar os nomes do método e campos da estrutura fornecidos nos **methodFilter** e **fieldFilter** elementos filho, respectivamente.

O exemplo a seguir mostra como habilitar vários MDAs usando suas configurações padrão:

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
> Ao especificar mais de um assistente em um arquivo de configuração, você deve listá-los em ordem alfabética. Por exemplo, se quiser habilitar os MDAs `virtualCERCall` e `invalidCERCall`, você deverá adicionar a entrada `<invalidCERCall />` antes da entrada `<virtualCERCall />`. Se as entradas não estiverem em ordem alfabética, será exibida uma mensagem de exceção do arquivo de configuração inválido sem tratamento.

## <a name="mda-exceptions"></a>Exceções de MDA

Quando um MDA está habilitado, ele está ativo, mesmo quando seu código não está em execução em um depurador. Se um evento de MDA for acionado quando um depurador não estiver presente, a mensagem do evento será apresentada em uma caixa de diálogo de exceção sem tratamento, ainda que não seja uma exceção sem tratamento. Para evitar a caixa de diálogo, remova as configurações de habilitação de MDA quando o código não estiver em execução em um ambiente de depuração.

Quando o código é executado no ambiente de desenvolvimento integrado (IDE) do Visual Studio, você pode evitar a caixa de diálogo de exceção que é exibida para os eventos MDA específicos. Para fazer isso, nos **Debug** menu, escolha **Windows** > **configurações de exceção**. No **configurações de exceção** janela, expanda o **assistentes para depuração gerenciada** lista e, em seguida, desmarque as **interromper quando lançada** caixa de seleção do MDA individual. Você também pode usar essa caixa de diálogo para *habilitar* a exibição de caixas de diálogo de exceção do MDA.

## <a name="mda-output"></a>Saída do MDA

Saída do MDA é semelhante ao exemplo a seguir, que mostra a saída do `PInvokeStackImbalance` MDA:

**Uma chamada para a função PInvoke ' MDATest! MDATest.Program::StdCall' tem tenha desequilibrado a pilha. Isso provavelmente ocorre porque a assinatura gerenciada de PInvoke não coincide com a assinatura de destino não gerenciado. Verifique se a convenção de chamada e os parâmetros da assinatura PInvoke correspondem a assinatura não gerenciada de destino.**

## <a name="see-also"></a>Consulte também

- [Depuração, rastreamento e criação de perfil](../../../docs/framework/debug-trace-profile/index.md)
