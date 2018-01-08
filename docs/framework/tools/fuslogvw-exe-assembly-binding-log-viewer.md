---
title: "Fuslogvw.exe (Visualizador do Log de Associações de Assembly)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 170e9ca4ed2b9ad17ec9120321612c37da32e453
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="f61a8-102">Fuslogvw.exe (Visualizador do Log de Associações de Assembly)</span><span class="sxs-lookup"><span data-stu-id="f61a8-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>
<span data-ttu-id="f61a8-103">O Visualizador de Log de Associação do Assembly exibe detalhes das associações de assembly.</span><span class="sxs-lookup"><span data-stu-id="f61a8-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="f61a8-104">Essas informações ajudam a diagnosticar por que o .NET Framework não pode localizar um assembly no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f61a8-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="f61a8-105">Essas falhas normalmente são o resultado de um assembly implantado no local incorreto, de uma imagem nativa que não é mais válida ou de uma incompatibilidade em números de versão ou culturas.</span><span class="sxs-lookup"><span data-stu-id="f61a8-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="f61a8-106">A falha no Common Language Runtime em localizar um assembly costuma aparecer como um <xref:System.TypeLoadException> em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f61a8-107">Você deve executar fuslogvw.exe com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="f61a8-107">You must run fuslogvw.exe with administrator privileges.</span></span>  
  
 <span data-ttu-id="f61a8-108">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f61a8-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f61a8-109">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7) com credenciais de administrador.</span><span class="sxs-lookup"><span data-stu-id="f61a8-109">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="f61a8-110">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f61a8-110">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="f61a8-111">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f61a8-111">At the command prompt, type the following:</span></span>  
  
```  
fuslogvw  
```  
  
 <span data-ttu-id="f61a8-112">O visualizador exibe uma entrada para cada associação do assembly com falha.</span><span class="sxs-lookup"><span data-stu-id="f61a8-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="f61a8-113">Para cada falha, o visualizador descreve o aplicativo que iniciou a associação; o assembly de associação, incluindo nome, versão, cultura e chave pública; e a data e a hora da falha.</span><span class="sxs-lookup"><span data-stu-id="f61a8-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>  
  
### <a name="to-change-the-log-location-view"></a><span data-ttu-id="f61a8-114">Para alterar a exibição do local do log</span><span class="sxs-lookup"><span data-stu-id="f61a8-114">To change the log location view</span></span>  
  
1.  <span data-ttu-id="f61a8-115">Selecione o botão de opção **Padrão** para exibir falhas de associação de todos os tipos de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="f61a8-116">Por padrão, as entradas de log são armazenadas em diretórios por usuário em disco no cache de wininet.</span><span class="sxs-lookup"><span data-stu-id="f61a8-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>  
  
2.  <span data-ttu-id="f61a8-117">Selecione o botão de opção **Personalizar** para exibir falhas de associação em um diretório personalizado especificado.</span><span class="sxs-lookup"><span data-stu-id="f61a8-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="f61a8-118">Você deve especificar o local personalizado no qual deseja que o tempo de execução armazene os logs definindo o local de log personalizado na caixa de diálogo **Configurações de Log** como um nome de diretório válido.</span><span class="sxs-lookup"><span data-stu-id="f61a8-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="f61a8-119">Esse diretório deve estar limpo e conter apenas arquivos gerados pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f61a8-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="f61a8-120">Se ele contiver um executável que gere uma falha a ser registrada em log, a falha não será registrada em log porque a ferramenta tenta criar um diretório com o mesmo nome do executável.</span><span class="sxs-lookup"><span data-stu-id="f61a8-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="f61a8-121">Além disso, haverá falha em uma tentativa de executar um executável com base no local do log.</span><span class="sxs-lookup"><span data-stu-id="f61a8-121">In addition, an attempt to run an executable from the log location will fail.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f61a8-122">O local de associação padrão é preferível ao local de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="f61a8-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="f61a8-123">O tempo de execução armazena o local de associação padrão no cache de wininet e, assim, o limpa automaticamente. Se especificar um local de associação personalizado, você será responsável por limpá-lo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>  
  
### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="f61a8-124">Para exibir detalhes sobre uma falha específica</span><span class="sxs-lookup"><span data-stu-id="f61a8-124">To view details about a specific failure</span></span>  
  
1.  <span data-ttu-id="f61a8-125">Selecione o nome do aplicativo da entrada desejada no visualizador.</span><span class="sxs-lookup"><span data-stu-id="f61a8-125">Select the application name of the desired entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="f61a8-126">Clique no botão **Exibir Log**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-126">Click the **View Log** button.</span></span> <span data-ttu-id="f61a8-127">Também é possível clicar duas vezes na entrada selecionada.</span><span class="sxs-lookup"><span data-stu-id="f61a8-127">Alternately, you can double-click the selected entry.</span></span>  
  
     <span data-ttu-id="f61a8-128">A ferramenta exibe os seguintes detalhes sobre a falha de associação selecionada:</span><span class="sxs-lookup"><span data-stu-id="f61a8-128">The tool displays the following details about the selected bind failure:</span></span>  
  
    -   <span data-ttu-id="f61a8-129">Um motivo específico para a falha na associação como, por exemplo, "arquivo não encontrado" ou "incompatibilidade versão".</span><span class="sxs-lookup"><span data-stu-id="f61a8-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>  
  
    -   <span data-ttu-id="f61a8-130">Informações sobre o aplicativo que iniciou a associação, incluindo seu nome, o diretório raiz do aplicativo (AppBase) e uma descrição do caminho de pesquisa privado, se houver uma.</span><span class="sxs-lookup"><span data-stu-id="f61a8-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>  
  
    -   <span data-ttu-id="f61a8-131">A identidade do assembly que a ferramenta está procurando.</span><span class="sxs-lookup"><span data-stu-id="f61a8-131">The identity of the assembly the tool is looking for.</span></span>  
  
    -   <span data-ttu-id="f61a8-132">Uma descrição de qualquer política da versão Aplicativo, Editor ou Administrador aplicada.</span><span class="sxs-lookup"><span data-stu-id="f61a8-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>  
  
    -   <span data-ttu-id="f61a8-133">Se o assembly estava ou não no [cache de assembly global](../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="f61a8-133">Whether the assembly was found in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span>  
  
    -   <span data-ttu-id="f61a8-134">Uma lista de todas as URLs de sondagem.</span><span class="sxs-lookup"><span data-stu-id="f61a8-134">A list of all probing URLs.</span></span>  
  
 <span data-ttu-id="f61a8-135">A entrada do log de exemplo a seguir mostra informações detalhadas sobre uma associação do assembly com falha.</span><span class="sxs-lookup"><span data-stu-id="f61a8-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>  
  
```  
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll  
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe  
--- A detailed error log follows.   
  
=== Pre-bind state information ===  
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
 (Fully-specified)  
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\  
LOG: Initial PrivatePath = NULL  
LOG: Dynamic Base = NULL  
LOG: Cache Base = NULL  
LOG: AppName = NULL  
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
===  
  
LOG: Processing DEVPATH.  
LOG: DEVPATH is not set. Falling through to regular bind.  
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).  
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.  
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.  
LOG: All probing URLs attempted and failed.  
```  
  
### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="f61a8-136">Para excluir uma única entrada do log</span><span class="sxs-lookup"><span data-stu-id="f61a8-136">To delete a single entry from the log</span></span>  
  
1.  <span data-ttu-id="f61a8-137">Selecione uma entrada no visualizador.</span><span class="sxs-lookup"><span data-stu-id="f61a8-137">Select an entry in the viewer.</span></span>  
  
2.  <span data-ttu-id="f61a8-138">Clique no botão **Excluir Entrada**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-138">Click the **Delete Entry** button.</span></span>  
  
### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="f61a8-139">Para excluir todas as entradas do log</span><span class="sxs-lookup"><span data-stu-id="f61a8-139">To delete all entries from the log</span></span>  
  
-   <span data-ttu-id="f61a8-140">Clique no botão **Excluir Tudo**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-140">Click the **Delete All** button.</span></span>  
  
### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="f61a8-141">Para atualizar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="f61a8-141">To refresh the user interface</span></span>  
  
-   <span data-ttu-id="f61a8-142">Clique no botão **Atualizar**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-142">Click the **Refresh** button.</span></span> <span data-ttu-id="f61a8-143">O visualizador não detecta automaticamente novas entradas de log durante a execução.</span><span class="sxs-lookup"><span data-stu-id="f61a8-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="f61a8-144">Você deve usar o botão **Atualizar** para exibi-las.</span><span class="sxs-lookup"><span data-stu-id="f61a8-144">You must use the **Refresh** button to display them.</span></span>  
  
### <a name="to-change-the-log-settings"></a><span data-ttu-id="f61a8-145">Para alterar as configurações de log.</span><span class="sxs-lookup"><span data-stu-id="f61a8-145">To change the log settings</span></span>  
  
-   <span data-ttu-id="f61a8-146">Clique no botão **Configurações** para abrir a caixa de diálogo **Configurações de Log**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>  
  
### <a name="to-view-the-about-dialog"></a><span data-ttu-id="f61a8-147">Para exibir a caixa de diálogo Sobre</span><span class="sxs-lookup"><span data-stu-id="f61a8-147">To view the About dialog</span></span>  
  
-   <span data-ttu-id="f61a8-148">Clique no botão **Sobre**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-148">Click the **About** button.</span></span>  
  
## <a name="binding-logs-for-native-images"></a><span data-ttu-id="f61a8-149">Associando Logs para Imagens Nativas</span><span class="sxs-lookup"><span data-stu-id="f61a8-149">Binding Logs for Native Images</span></span>  
 <span data-ttu-id="f61a8-150">Por padrão, Fuslogvw.exe registra em log solicitações de associação normais.</span><span class="sxs-lookup"><span data-stu-id="f61a8-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="f61a8-151">Também é possível registrar em log associações de assembly para imagens nativas criadas usando o [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="f61a8-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="f61a8-152">Para registrar em log associações de assembly para imagens nativas</span><span class="sxs-lookup"><span data-stu-id="f61a8-152">To log assembly binds for native images</span></span>  
  
-   <span data-ttu-id="f61a8-153">No grupo **Categorias de Log**, selecione o botão de opção **Imagens Nativas**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>  
  
 <span data-ttu-id="f61a8-154">O log a seguir mostra uma falha causada por uma dependência que não existia quando a imagem nativa foi criada para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="f61a8-155">Se as dependências no tempo de execução forem diferentes das dependências durante a execução de Ngen.exe, a associação a uma imagem nativa não será permitida.</span><span class="sxs-lookup"><span data-stu-id="f61a8-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80070002. The system cannot find the file specified.  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\App.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\App.exe.  
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.  
WRN: No matching native image found.  
LOG: Bind to native image assembly did not succeed. Use IL image.  
```  
  
 <span data-ttu-id="f61a8-156">O log seguir mostra uma associação de imagem nativa com falha ocorrida porque as configurações de segurança no computador quando o aplicativo foi executado eram diferentes das configurações de segurança no momento em que a imagem nativa foi criada.</span><span class="sxs-lookup"><span data-stu-id="f61a8-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>  
  
```  
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***  
  
The operation failed.  
Bind result: hr = 0x80004005. Unspecified error  
  
Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll  
Running under executable  E:\test\Application101622.exe  
--- A detailed error log follows.   
  
LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: IL assembly loaded from E:\test\Application101622.exe.  
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Start validating all the dependencies.  
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
LOG: Dependency evaluation succeeded.  
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.  
LOG: Dependency evaluation succeeded.  
LOG: Validation of dependencies succeeded.  
LOG: Start loading all the dependencies into load context.  
LOG: Loading of dependencies succeeded.  
LOG: Bind to native image succeeded.  
Native image has correct version information.  
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.  
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.  
Discarding native image.  
```  
  
## <a name="the-log-settings-dialog"></a><span data-ttu-id="f61a8-157">A caixa de diálogo Configurações de Log</span><span class="sxs-lookup"><span data-stu-id="f61a8-157">The Log Settings Dialog</span></span>  
 <span data-ttu-id="f61a8-158">É possível usar a caixa de diálogo **Configurações de Log** para executar as ações a seguir.</span><span class="sxs-lookup"><span data-stu-id="f61a8-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>  
  
#### <a name="to-disable-logging"></a><span data-ttu-id="f61a8-159">Para desabilitar o registro em log</span><span class="sxs-lookup"><span data-stu-id="f61a8-159">To disable logging</span></span>  
  
-   <span data-ttu-id="f61a8-160">Selecione o botão de opção **Log desabilitado**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="f61a8-161">Essa opção não permanece selecionada por padrão.</span><span class="sxs-lookup"><span data-stu-id="f61a8-161">Note that this option is selected by default.</span></span>  
  
#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="f61a8-162">Para registrar em log associações de assembly em exceções</span><span class="sxs-lookup"><span data-stu-id="f61a8-162">To log assembly binds in exceptions</span></span>  
  
-   <span data-ttu-id="f61a8-163">Selecione o botão de opção **Registrar em log o texto de exceção**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="f61a8-164">Apenas as informações de log da fusão menos detalhadas são registradas em log em texto de exceção.</span><span class="sxs-lookup"><span data-stu-id="f61a8-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="f61a8-165">Para exibir informações completas, use uma das outras configurações.</span><span class="sxs-lookup"><span data-stu-id="f61a8-165">To view full information, use one of the other settings.</span></span>  
  
     <span data-ttu-id="f61a8-166">Consulte a observação Importante a respeito de assemblies carregados como tendo domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="f61a8-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="f61a8-167">Para registrar em log falhas na associação do assembly</span><span class="sxs-lookup"><span data-stu-id="f61a8-167">To log assembly bind failures</span></span>  
  
-   <span data-ttu-id="f61a8-168">Selecione o botão de opção **Registrar falhas na associação em disco**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-168">Select the **Log bind failures to disk** option button.</span></span>  
  
     <span data-ttu-id="f61a8-169">Consulte a observação Importante a respeito de assemblies carregados como tendo domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="f61a8-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="f61a8-170">Para registrar em log todas as associações de assembly</span><span class="sxs-lookup"><span data-stu-id="f61a8-170">To log all assembly binds</span></span>  
  
-   <span data-ttu-id="f61a8-171">Selecione o botão de opção **Registrar todas as associações em disco**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-171">Select the **Log all binds to disk** option button.</span></span>  
  
     <span data-ttu-id="f61a8-172">Consulte a observação Importante a respeito de assemblies carregados como tendo domínio neutro.</span><span class="sxs-lookup"><span data-stu-id="f61a8-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f61a8-173">Quando um assembly é carregado como tendo domínio neutro, por exemplo, definindo-se a propriedade <xref:System.AppDomainSetup.LoaderOptimization%2A> como <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> ou a <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, a ativação do registro em log pode causar perda de memória em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="f61a8-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="f61a8-174">Isso poderá acontecer se uma entrada de log for feita quando um módulo de domínio neutro for carregado em um domínio do aplicativo e, posteriormente, o domínio do aplicativo for descarregado.</span><span class="sxs-lookup"><span data-stu-id="f61a8-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="f61a8-175">A entrada de log talvez não seja liberada até o término do processo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="f61a8-176">Alguns depuradores ativam o registro em log automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f61a8-176">Some debuggers automatically turn on logging.</span></span>  
  
#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="f61a8-177">Para habilitar um caminho de log personalizado</span><span class="sxs-lookup"><span data-stu-id="f61a8-177">To enable a custom log path</span></span>  
  
1.  <span data-ttu-id="f61a8-178">Selecione o botão de opção **Habilitar caminho de log personalizado**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-178">Select the **Enable custom log path** option button.</span></span>  
  
2.  <span data-ttu-id="f61a8-179">Digite o caminho na caixa de texto **Caminho de log personalizado**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-179">Enter the path into the **Custom log path** text box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f61a8-180">O [Visualizador de Log de Associação de Assembly (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) usa o cache do IE (Internet Explorer) para armazenar seu log de associação.</span><span class="sxs-lookup"><span data-stu-id="f61a8-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="f61a8-181">Devido a um dano ocasional no cache do IE, o [Visualizador de Log de Associação de Assembly (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) às vezes pode parar de mostrar os novos logs de associação na janela de exibição.</span><span class="sxs-lookup"><span data-stu-id="f61a8-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="f61a8-182">Por conta desse dano, a infraestrutura de associação do .NET (fusão) não pode gravar no ou ler do log de associação.</span><span class="sxs-lookup"><span data-stu-id="f61a8-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="f61a8-183">(Esse problema não será encontrado se você usar um caminho de log personalizado.)  Para corrigir o dano e permitir que a fusão mostre logs de associação novamente, limpe o cache do IE excluindo arquivos de Internet temporários na caixa de diálogo Opções da Internet do IE.</span><span class="sxs-lookup"><span data-stu-id="f61a8-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>  
>   
>  <span data-ttu-id="f61a8-184">Se o aplicativo não gerenciado hospedar o Common Language Runtime implementando as interfaces `IHostAssemblyManager` e `IHostAssemblyStore`, as entradas de log não poderão ser armazenadas no cache de wininet.</span><span class="sxs-lookup"><span data-stu-id="f61a8-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="f61a8-185">Para exibir entradas de log para hosts personalizadas que implementam essas interfaces, você deve especificar um caminho de log alternativo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>  
  
#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="f61a8-186">Para habilitar o registro em log para aplicativos em execução no contêiner do aplicativo do Windows</span><span class="sxs-lookup"><span data-stu-id="f61a8-186">To enable logging for apps running in the Windows app container</span></span>  
  
1.  <span data-ttu-id="f61a8-187">Habilite um caminho de log personalizado, conforme descrito no procedimento anterior.</span><span class="sxs-lookup"><span data-stu-id="f61a8-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="f61a8-188">Por padrão, os aplicativos em execução no contêiner do aplicativo do Windows têm acesso limitado no disco rígido.</span><span class="sxs-lookup"><span data-stu-id="f61a8-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="f61a8-189">O diretório especificado terá acesso de leitura/gravação em todos os aplicativos no contêiner do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f61a8-189">The directory you specify will have read/write access for all apps in the app container.</span></span>  
  
2.  <span data-ttu-id="f61a8-190">Marque a caixa de seleção **Habilitar registro em log imersivo**.</span><span class="sxs-lookup"><span data-stu-id="f61a8-190">Select the **Enable immersive logging** check box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f61a8-191">Essa caixa só está habilitada no Windows 8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="f61a8-191">This box is enabled only on Windows 8 or later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61a8-192">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f61a8-192">See Also</span></span>  
 <xref:System.TypeLoadException>  
 [<span data-ttu-id="f61a8-193">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="f61a8-193">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="f61a8-194">Cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="f61a8-194">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="f61a8-195">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="f61a8-195">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="f61a8-196">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="f61a8-196">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
