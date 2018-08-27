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
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935738"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="9689a-102">Diagnosticar erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="9689a-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="9689a-103">Os MDAs (Assistentes para depuração gerenciada) são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9689a-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="9689a-104">Os assistentes geram mensagens informativas sobre eventos de tempo de execução que não podem ser interceptados de outro modo.</span><span class="sxs-lookup"><span data-stu-id="9689a-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="9689a-105">É possível usar MDAs para isolar bugs de aplicativos difíceis de encontrar que ocorrem durante a transição entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9689a-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="9689a-106">Você pode [habilitar ou desabilitar](#enable-and-disable-mdas) todos os MDAs adicionando uma chave no registro do Windows ou definindo uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="9689a-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="9689a-107">Você pode habilitar MDAs específicos usando definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9689a-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="9689a-108">É possível definir configurações adicionais para alguns MDAs individuais no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9689a-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="9689a-109">Como esses arquivos de configuração são analisados quando o tempo de execução é carregado, você deve habilitar o MDA antes da inicialização do aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9689a-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="9689a-110">Não será possível habilitá-lo para aplicativos já iniciados.</span><span class="sxs-lookup"><span data-stu-id="9689a-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="9689a-111">A tabela a seguir lista os MDAs que acompanham o .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9689a-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="9689a-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="9689a-112">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="9689a-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="9689a-113">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[<span data-ttu-id="9689a-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="9689a-114">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="9689a-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="9689a-115">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="9689a-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="9689a-116">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="9689a-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="9689a-117">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="9689a-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="9689a-118">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="9689a-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="9689a-119">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[<span data-ttu-id="9689a-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="9689a-120">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="9689a-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="9689a-121">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="9689a-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="9689a-122">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="9689a-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="9689a-123">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="9689a-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="9689a-124">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="9689a-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="9689a-125">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="9689a-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="9689a-126">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="9689a-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="9689a-127">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="9689a-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="9689a-128">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="9689a-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="9689a-129">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="9689a-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="9689a-130">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="9689a-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="9689a-131">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[<span data-ttu-id="9689a-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="9689a-132">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="9689a-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="9689a-133">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="9689a-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="9689a-134">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="9689a-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="9689a-135">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[<span data-ttu-id="9689a-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="9689a-136">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="9689a-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="9689a-137">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[<span data-ttu-id="9689a-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="9689a-138">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="9689a-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="9689a-139">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[<span data-ttu-id="9689a-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="9689a-140">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="9689a-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="9689a-141">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="9689a-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="9689a-142">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="9689a-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="9689a-143">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[<span data-ttu-id="9689a-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="9689a-144">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="9689a-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="9689a-145">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[<span data-ttu-id="9689a-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="9689a-146">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="9689a-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="9689a-147">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="9689a-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="9689a-148">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="9689a-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="9689a-149">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[<span data-ttu-id="9689a-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="9689a-150">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="9689a-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="9689a-151">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[<span data-ttu-id="9689a-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="9689a-152">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="9689a-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="9689a-153">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

<span data-ttu-id="9689a-154">Por padrão, o .NET Framework ativa um subconjunto de MDAs para todos os depuradores gerenciados.</span><span class="sxs-lookup"><span data-stu-id="9689a-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="9689a-155">Você pode exibir o conjunto padrão no Visual Studio escolhendo **Windows** > **configurações de exceção** sobre a **depurar** menus e expandindo o **Assistentes para depuração gerenciada** lista.</span><span class="sxs-lookup"><span data-stu-id="9689a-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Janela de configurações de exceção no Visual Studio](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="9689a-157">Habilitar e desabilitar MDAs</span><span class="sxs-lookup"><span data-stu-id="9689a-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="9689a-158">É possível habilitar e desabilitar MDAs usando uma chave do Registro, uma variável de ambiente e as definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9689a-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="9689a-159">Você deve habilitar a chave do Registro ou a variável de ambiente para usar as definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9689a-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="9689a-160">Em vez de desabilitar MDAs, você pode impedir que o Visual Studio exibindo a caixa de diálogo MDA sempre que uma notificação é recebida.</span><span class="sxs-lookup"><span data-stu-id="9689a-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="9689a-161">Para fazer isso, escolha **Windows** > **configurações de exceção** sobre a **depurar** menu, expanda o **Managed Debugging Assistants**e, em seguida, selecione ou desmarque as **interromper quando lançada** caixa de seleção do MDA individual.</span><span class="sxs-lookup"><span data-stu-id="9689a-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="9689a-162">Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="9689a-162">Registry Key</span></span>

<span data-ttu-id="9689a-163">Para habilitar MDAs, adicione a **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** subchave (digite REG_SZ, valor 1) no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="9689a-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="9689a-164">Copie o exemplo a seguir em um arquivo de texto denominado *Mdaenable*. Abra o Editor do registro do Windows (RegEdit.exe) e para o **arquivo** menu escolher **importação**.</span><span class="sxs-lookup"><span data-stu-id="9689a-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="9689a-165">Selecione o *Mdaenable* arquivo para habilitar MDAs nesse computador.</span><span class="sxs-lookup"><span data-stu-id="9689a-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="9689a-166">Definição da subchave como valor de cadeia de caracteres de **1** (não o valor de DWORD **1**) permite a leitura das configurações do MDA do *Suffix*. arquivo MDA.</span><span class="sxs-lookup"><span data-stu-id="9689a-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="9689a-167">Por exemplo, o arquivo de configuração do MDA para o bloco de notas seria nomeado Notepad.</span><span class="sxs-lookup"><span data-stu-id="9689a-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="9689a-168">Se o computador estiver executando um aplicativo de 32 bits em um sistema operacional de 64 bits, a chave do MDA deverá ser definida da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="9689a-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="9689a-169">Ver [definições de configuração específicas do aplicativo](#application-specific-configuration-settings) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9689a-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="9689a-170">A configuração do Registro pode ser substituída pela variável de ambiente COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="9689a-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="9689a-171">Ver [variável de ambiente](#environment-variable) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="9689a-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="9689a-172">Para desabilitar MDAs, defina a subchave do MDA para **0** (zero) usando o Editor de registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="9689a-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="9689a-173">Por padrão, alguns MDAs são habilitados quando você executa um aplicativo anexado a um depurador, mesmo sem adicionar a chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="9689a-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="9689a-174">Você pode desabilitar esses assistentes executando o *Mdadisable* conforme descrito anteriormente nesta seção do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9689a-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="9689a-175">Variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="9689a-175">Environment Variable</span></span>

<span data-ttu-id="9689a-176">A ativação do MDA também pode ser controlada pela variável de ambiente COMPLUS_MDA, que substitui a chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="9689a-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="9689a-177">A cadeia de caracteres COMPLUS_MDA é uma lista delimitada por ponto-e-vírgula, que não diferencia maiúsculas de minúsculas, de nomes de MDA ou outras cadeias de caracteres de controle especiais.</span><span class="sxs-lookup"><span data-stu-id="9689a-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="9689a-178">A inicialização em um depurador gerenciado ou não gerenciado habilita um conjunto de MDAs por padrão.</span><span class="sxs-lookup"><span data-stu-id="9689a-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="9689a-179">Isso é feito implicitamente precedendo a lista separada por ponto-e-vírgula de MDAs habilitados por padrão nos depuradores ao valor da variável de ambiente ou da chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="9689a-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="9689a-180">As cadeias de caracteres de controle especiais são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="9689a-180">The special control strings are the following:</span></span>

- <span data-ttu-id="9689a-181">`0` – Desativa todos os MDAs.</span><span class="sxs-lookup"><span data-stu-id="9689a-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="9689a-182">`1` – Lê as configurações do MDA por meio de *ApplicationName*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="9689a-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="9689a-183">`managedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável gerenciado é iniciado em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9689a-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="9689a-184">`unmanagedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável não gerenciado é iniciado em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9689a-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="9689a-185">Se houver configurações conflitantes, as mais recentes substituirão as anteriores:</span><span class="sxs-lookup"><span data-stu-id="9689a-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="9689a-186">`COMPLUS_MDA=0` desabilita todos os MDAs, incluindo aqueles habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9689a-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="9689a-187">`COMPLUS_MDA=gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, além de todos os MDAs habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9689a-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="9689a-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, mas desabilita os MDAs que seriam, de outro modo, habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9689a-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="9689a-189">Definições de configuração específicas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9689a-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="9689a-190">É possível habilitar, desabilitar e configurar alguns assistentes individualmente no arquivo de configuração do MDA para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9689a-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="9689a-191">Para habilitar o uso de um arquivo de configuração de aplicativo para configurar MDAs, a chave do Registro do MDA ou a variável de ambiente COMPLUS_MDA deve estar definida.</span><span class="sxs-lookup"><span data-stu-id="9689a-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="9689a-192">O arquivo de configuração de aplicativo costuma ficar localizado no mesmo diretório do arquivo executável do aplicativo (.exe).</span><span class="sxs-lookup"><span data-stu-id="9689a-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="9689a-193">O nome de arquivo usa o formato *ApplicationName*.mda.config; por exemplo, notepad.exe.mda.config. Os assistentes habilitados no arquivo de configuração de aplicativo podem ter atributos ou elementos projetados especificamente para controlar esse comportamento do assistente.</span><span class="sxs-lookup"><span data-stu-id="9689a-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="9689a-194">O exemplo a seguir mostra como habilitar e configurar o [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="9689a-194">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span></span>

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

<span data-ttu-id="9689a-195">O MDA `Marshaling` emite informações sobre o tipo gerenciado em que o marshaling está sendo realizado para um tipo não gerenciado para a transição gerenciado/não gerenciado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9689a-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="9689a-196">O `Marshaling` MDA também pode filtrar os nomes do método e campos da estrutura fornecidos nos **methodFilter** e **fieldFilter** elementos filho, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9689a-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="9689a-197">O exemplo a seguir mostra como habilitar vários MDAs usando suas configurações padrão:</span><span class="sxs-lookup"><span data-stu-id="9689a-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="9689a-198">Ao especificar mais de um assistente em um arquivo de configuração, você deve listá-los em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="9689a-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="9689a-199">Por exemplo, se quiser habilitar os MDAs `virtualCERCall` e `invalidCERCall`, você deverá adicionar a entrada `<invalidCERCall />` antes da entrada `<virtualCERCall />`.</span><span class="sxs-lookup"><span data-stu-id="9689a-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="9689a-200">Se as entradas não estiverem em ordem alfabética, será exibida uma mensagem de exceção do arquivo de configuração inválido sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="9689a-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="9689a-201">Exceções de MDA</span><span class="sxs-lookup"><span data-stu-id="9689a-201">MDA exceptions</span></span>

<span data-ttu-id="9689a-202">Quando um MDA está habilitado, ele está ativo, mesmo quando seu código não está em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="9689a-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="9689a-203">Se um evento de MDA for acionado quando um depurador não estiver presente, a mensagem do evento será apresentada em uma caixa de diálogo de exceção sem tratamento, ainda que não seja uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="9689a-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="9689a-204">Para evitar a caixa de diálogo, remova as configurações de habilitação de MDA quando o código não estiver em execução em um ambiente de depuração.</span><span class="sxs-lookup"><span data-stu-id="9689a-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="9689a-205">Quando o código é executado no ambiente de desenvolvimento integrado (IDE) do Visual Studio, você pode evitar a caixa de diálogo de exceção que é exibida para os eventos MDA específicos.</span><span class="sxs-lookup"><span data-stu-id="9689a-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="9689a-206">Para fazer isso, nos **Debug** menu, escolha **Windows** > **configurações de exceção**.</span><span class="sxs-lookup"><span data-stu-id="9689a-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="9689a-207">No **configurações de exceção** janela, expanda o **assistentes para depuração gerenciada** lista e, em seguida, desmarque as **interromper quando lançada** caixa de seleção do MDA individual.</span><span class="sxs-lookup"><span data-stu-id="9689a-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="9689a-208">Você também pode usar essa caixa de diálogo para *habilitar* a exibição de caixas de diálogo de exceção do MDA.</span><span class="sxs-lookup"><span data-stu-id="9689a-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="9689a-209">Saída do MDA</span><span class="sxs-lookup"><span data-stu-id="9689a-209">MDA Output</span></span>

<span data-ttu-id="9689a-210">Saída do MDA é semelhante ao exemplo a seguir, que mostra a saída do `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="9689a-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="9689a-211">**Uma chamada para a função PInvoke ' MDATest! MDATest.Program::StdCall' tem tenha desequilibrado a pilha. Isso provavelmente ocorre porque a assinatura gerenciada de PInvoke não coincide com a assinatura de destino não gerenciado. Verifique se a convenção de chamada e os parâmetros da assinatura PInvoke correspondem a assinatura não gerenciada de destino.**</span><span class="sxs-lookup"><span data-stu-id="9689a-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="9689a-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9689a-212">See also</span></span>

- [<span data-ttu-id="9689a-213">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="9689a-213">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
