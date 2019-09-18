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
ms.openlocfilehash: 6cb2a240a2e7e82b7015eb7a6d99c2117fa63045
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052897"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="883e0-102">Diagnosticar erros com assistentes de depuração gerenciados</span><span class="sxs-lookup"><span data-stu-id="883e0-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="883e0-103">Os MDAs (Assistentes para depuração gerenciada) são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="883e0-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="883e0-104">Os assistentes geram mensagens informativas sobre eventos de tempo de execução que não podem ser interceptados de outro modo.</span><span class="sxs-lookup"><span data-stu-id="883e0-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="883e0-105">É possível usar MDAs para isolar bugs de aplicativos difíceis de encontrar que ocorrem durante a transição entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="883e0-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="883e0-106">Você pode [habilitar ou desabilitar](#enable-and-disable-mdas) todos os MDAs adicionando uma chave ao registro do Windows ou configurando uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="883e0-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="883e0-107">Você pode habilitar MDAs específicos usando definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="883e0-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="883e0-108">É possível definir configurações adicionais para alguns MDAs individuais no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="883e0-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="883e0-109">Como esses arquivos de configuração são analisados quando o tempo de execução é carregado, você deve habilitar o MDA antes da inicialização do aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="883e0-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="883e0-110">Não será possível habilitá-lo para aplicativos já iniciados.</span><span class="sxs-lookup"><span data-stu-id="883e0-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="883e0-111">A tabela a seguir lista os MDAs que acompanham o .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="883e0-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="883e0-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="883e0-112">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="883e0-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="883e0-113">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="883e0-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="883e0-114">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="883e0-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="883e0-115">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="883e0-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="883e0-116">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="883e0-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="883e0-117">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="883e0-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="883e0-118">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="883e0-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="883e0-119">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="883e0-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="883e0-120">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="883e0-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="883e0-121">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="883e0-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="883e0-122">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="883e0-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="883e0-123">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="883e0-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="883e0-124">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="883e0-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="883e0-125">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="883e0-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="883e0-126">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="883e0-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="883e0-127">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="883e0-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="883e0-128">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="883e0-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="883e0-129">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="883e0-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="883e0-130">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="883e0-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="883e0-131">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="883e0-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="883e0-132">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="883e0-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="883e0-133">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="883e0-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="883e0-134">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="883e0-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="883e0-135">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="883e0-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="883e0-136">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="883e0-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="883e0-137">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="883e0-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="883e0-138">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="883e0-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="883e0-139">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="883e0-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="883e0-140">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="883e0-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="883e0-141">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="883e0-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="883e0-142">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="883e0-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="883e0-143">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="883e0-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="883e0-144">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="883e0-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="883e0-145">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="883e0-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="883e0-146">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="883e0-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="883e0-147">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="883e0-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="883e0-148">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="883e0-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="883e0-149">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="883e0-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="883e0-150">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="883e0-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="883e0-151">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="883e0-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="883e0-152">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="883e0-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="883e0-153">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="883e0-154">Por padrão, o .NET Framework ativa um subconjunto de MDAs para todos os depuradores gerenciados.</span><span class="sxs-lookup"><span data-stu-id="883e0-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="883e0-155">Você pode exibir o conjunto padrão no Visual Studio escolhendo**configurações de exceção** do **Windows** > no menu **depurar** e, em seguida, expandindo a lista de **assistentes de depuração gerenciada** .</span><span class="sxs-lookup"><span data-stu-id="883e0-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Janela de configurações de exceção no Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="883e0-157">Habilitar e desabilitar MDAs</span><span class="sxs-lookup"><span data-stu-id="883e0-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="883e0-158">É possível habilitar e desabilitar MDAs usando uma chave do Registro, uma variável de ambiente e as definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="883e0-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="883e0-159">Você deve habilitar a chave do Registro ou a variável de ambiente para usar as definições de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="883e0-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="883e0-160">Em vez de desabilitar o MDAs, você pode impedir que o Visual Studio exiba a caixa de diálogo MDA sempre que uma notificação do MDA é recebida.</span><span class="sxs-lookup"><span data-stu-id="883e0-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="883e0-161">Para fazer isso, escolha**configurações de exceção** do **Windows** > no menu **depurar** , expanda a lista **assistentes de depuração gerenciada** e marque ou desmarque a caixa de seleção **interromper quando for gerada** para o MDA individual.</span><span class="sxs-lookup"><span data-stu-id="883e0-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="883e0-162">Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="883e0-162">Registry Key</span></span>

<span data-ttu-id="883e0-163">Para habilitar o MDAs, adicione **o\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.** Subchave NETFramework\MDA (tipo REG_SZ, valor 1) no registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="883e0-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="883e0-164">Copie o exemplo a seguir em um arquivo de texto chamado *MDAEnable. reg*. Abra o editor do registro do Windows (RegEdit. exe) e, no menu **arquivo** , escolha **importar**.</span><span class="sxs-lookup"><span data-stu-id="883e0-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="883e0-165">Selecione o arquivo *MDAEnable. reg* para habilitar o MDAs nesse computador.</span><span class="sxs-lookup"><span data-stu-id="883e0-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="883e0-166">A definição da subchave para o valor de cadeia de caracteres **1** (não o valor DWORD de **1**) permite a leitura das configurações de MDA do arquivo *ApplicationName. Suffix*. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="883e0-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="883e0-167">Por exemplo, o arquivo de configuração do MDA para o bloco de notas seria chamado de Notepad. exe. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="883e0-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="883e0-168">Se o computador estiver executando um aplicativo de 32 bits em um sistema operacional de 64 bits, a chave do MDA deverá ser definida da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="883e0-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="883e0-169">Consulte [definições de configuração específicas do aplicativo](#application-specific-configuration-settings) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="883e0-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="883e0-170">A configuração do Registro pode ser substituída pela variável de ambiente COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="883e0-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="883e0-171">Consulte [variável de ambiente](#environment-variable) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="883e0-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="883e0-172">Para desabilitar o MDAs, defina a subchave MDA como **0** (zero) usando o editor do registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="883e0-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="883e0-173">Por padrão, alguns MDAs são habilitados quando você executa um aplicativo anexado a um depurador, mesmo sem adicionar a chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="883e0-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="883e0-174">Você pode desabilitar esses assistentes executando o arquivo *MDADisable. reg* , conforme descrito anteriormente nesta seção.</span><span class="sxs-lookup"><span data-stu-id="883e0-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="883e0-175">Variável de ambiente</span><span class="sxs-lookup"><span data-stu-id="883e0-175">Environment Variable</span></span>

<span data-ttu-id="883e0-176">A ativação do MDA também pode ser controlada pela variável de ambiente COMPLUS_MDA, que substitui a chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="883e0-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="883e0-177">A cadeia de caracteres COMPLUS_MDA é uma lista delimitada por ponto-e-vírgula, que não diferencia maiúsculas de minúsculas, de nomes de MDA ou outras cadeias de caracteres de controle especiais.</span><span class="sxs-lookup"><span data-stu-id="883e0-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="883e0-178">A inicialização em um depurador gerenciado ou não gerenciado habilita um conjunto de MDAs por padrão.</span><span class="sxs-lookup"><span data-stu-id="883e0-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="883e0-179">Isso é feito implicitamente precedendo a lista separada por ponto-e-vírgula de MDAs habilitados por padrão nos depuradores ao valor da variável de ambiente ou da chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="883e0-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="883e0-180">As cadeias de caracteres de controle especiais são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="883e0-180">The special control strings are the following:</span></span>

- <span data-ttu-id="883e0-181">`0` – Desativa todos os MDAs.</span><span class="sxs-lookup"><span data-stu-id="883e0-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="883e0-182">`1` – Lê as configurações do MDA por meio de *ApplicationName*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="883e0-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="883e0-183">`managedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável gerenciado é iniciado em um depurador.</span><span class="sxs-lookup"><span data-stu-id="883e0-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="883e0-184">`unmanagedDebugger` – Ativa explicitamente todos os MDAs ativados implicitamente quando um executável não gerenciado é iniciado em um depurador.</span><span class="sxs-lookup"><span data-stu-id="883e0-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="883e0-185">Se houver configurações conflitantes, as mais recentes substituirão as anteriores:</span><span class="sxs-lookup"><span data-stu-id="883e0-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="883e0-186">`COMPLUS_MDA=0` desabilita todos os MDAs, incluindo aqueles habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="883e0-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="883e0-187">`COMPLUS_MDA=gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, além de todos os MDAs habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="883e0-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="883e0-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` habilita `gcUnmanagedToManaged`, mas desabilita os MDAs que seriam, de outro modo, habilitados implicitamente em um depurador.</span><span class="sxs-lookup"><span data-stu-id="883e0-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="883e0-189">Definições de configuração específicas do aplicativo</span><span class="sxs-lookup"><span data-stu-id="883e0-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="883e0-190">É possível habilitar, desabilitar e configurar alguns assistentes individualmente no arquivo de configuração do MDA para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="883e0-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="883e0-191">Para habilitar o uso de um arquivo de configuração de aplicativo para configurar MDAs, a chave do Registro do MDA ou a variável de ambiente COMPLUS_MDA deve estar definida.</span><span class="sxs-lookup"><span data-stu-id="883e0-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="883e0-192">O arquivo de configuração de aplicativo costuma ficar localizado no mesmo diretório do arquivo executável do aplicativo (.exe).</span><span class="sxs-lookup"><span data-stu-id="883e0-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="883e0-193">O nome de arquivo usa o formato *ApplicationName*.mda.config; por exemplo, notepad.exe.mda.config. Os assistentes habilitados no arquivo de configuração de aplicativo podem ter atributos ou elementos projetados especificamente para controlar esse comportamento do assistente.</span><span class="sxs-lookup"><span data-stu-id="883e0-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="883e0-194">O exemplo a seguir mostra como habilitar e configurar o [marshaling](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="883e0-194">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="883e0-195">O MDA `Marshaling` emite informações sobre o tipo gerenciado em que o marshaling está sendo realizado para um tipo não gerenciado para a transição gerenciado/não gerenciado no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="883e0-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="883e0-196">O `Marshaling` MDA também pode filtrar os nomes dos campos de método e estrutura fornecidos nos elementos filho **methodFilter** e **fieldFilter** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="883e0-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="883e0-197">O exemplo a seguir mostra como habilitar vários MDAs usando suas configurações padrão:</span><span class="sxs-lookup"><span data-stu-id="883e0-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="883e0-198">Ao especificar mais de um assistente em um arquivo de configuração, você deve listá-los em ordem alfabética.</span><span class="sxs-lookup"><span data-stu-id="883e0-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="883e0-199">Por exemplo, se quiser habilitar os MDAs `virtualCERCall` e `invalidCERCall`, você deverá adicionar a entrada `<invalidCERCall />` antes da entrada `<virtualCERCall />`.</span><span class="sxs-lookup"><span data-stu-id="883e0-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="883e0-200">Se as entradas não estiverem em ordem alfabética, será exibida uma mensagem de exceção do arquivo de configuração inválido sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="883e0-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="883e0-201">Exceções do MDA</span><span class="sxs-lookup"><span data-stu-id="883e0-201">MDA exceptions</span></span>

<span data-ttu-id="883e0-202">Quando um MDA é habilitado, ele fica ativo mesmo quando seu código não está em execução em um depurador.</span><span class="sxs-lookup"><span data-stu-id="883e0-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="883e0-203">Se um evento de MDA for acionado quando um depurador não estiver presente, a mensagem do evento será apresentada em uma caixa de diálogo de exceção sem tratamento, ainda que não seja uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="883e0-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="883e0-204">Para evitar a caixa de diálogo, remova as configurações de habilitação de MDA quando o código não estiver em execução em um ambiente de depuração.</span><span class="sxs-lookup"><span data-stu-id="883e0-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="883e0-205">Quando seu código é executado no IDE (ambiente de desenvolvimento integrado) do Visual Studio, você pode evitar a caixa de diálogo de exceção que aparece para eventos específicos do MDA.</span><span class="sxs-lookup"><span data-stu-id="883e0-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="883e0-206">Para fazer isso, no menu **depurar** , escolha**configurações de exceção**do **Windows** > .</span><span class="sxs-lookup"><span data-stu-id="883e0-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="883e0-207">Na janela **configurações de exceção** , expanda a lista **assistentes de depuração gerenciada** e desmarque a caixa de seleção **interromper quando lançado** para o MDA individual.</span><span class="sxs-lookup"><span data-stu-id="883e0-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="883e0-208">Você também pode usar essa caixa de diálogo para *habilitar* a exibição das caixas de diálogo de exceção do MDA.</span><span class="sxs-lookup"><span data-stu-id="883e0-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="883e0-209">Saída do MDA</span><span class="sxs-lookup"><span data-stu-id="883e0-209">MDA Output</span></span>

<span data-ttu-id="883e0-210">A saída do MDA é semelhante ao exemplo a seguir, que mostra a saída `PInvokeStackImbalance` do MDA:</span><span class="sxs-lookup"><span data-stu-id="883e0-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="883e0-211">**Uma chamada para a função PInvoke ' MDATest! ' MDATest. Program:: StdCall ' desbalanceou a pilha. Isso é provável porque a assinatura do PInvoke gerenciada não corresponde à assinatura de destino não gerenciada. Verifique se a Convenção de chamada e os parâmetros da assinatura PInvoke correspondem à assinatura não gerenciada de destino.**</span><span class="sxs-lookup"><span data-stu-id="883e0-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="883e0-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="883e0-212">See also</span></span>

- [<span data-ttu-id="883e0-213">Depuração, rastreamento e criação de perfil</span><span class="sxs-lookup"><span data-stu-id="883e0-213">Debugging, Tracing, and Profiling</span></span>](index.md)
