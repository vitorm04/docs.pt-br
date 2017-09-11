---
title: Ngen.exe (Gerador de Imagens Nativas)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
caps.latest.revision: 57
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: c6e199800a86bc8b275fed4e3ba3ea6f77c7d2fa
ms.openlocfilehash: e7fd4049228d4361f4c0d4d61e15ca7f5ea0594f
ms.contentlocale: pt-br
ms.lasthandoff: 09/01/2017

---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="76e27-102">Ngen.exe (Gerador de Imagens Nativas)</span><span class="sxs-lookup"><span data-stu-id="76e27-102">Ngen.exe (Native Image Generator)</span></span>
<span data-ttu-id="76e27-103">O Gerador de Imagem Nativa (Ngen.exe) é uma ferramenta que melhora o desempenho de aplicativos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="76e27-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="76e27-104">Ngen.exe cria imagens nativas, que são arquivos que contém o código de máquina específico do processamento compilado e as instala no cache de imagem nativa do computador local.</span><span class="sxs-lookup"><span data-stu-id="76e27-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="76e27-105">O tempo de execução pode usar imagens nativas do cache em vez de usar o compilador JIT (Just-In-Time) para compilar o assembly original.</span><span class="sxs-lookup"><span data-stu-id="76e27-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>  
  
 <span data-ttu-id="76e27-106">Alterações feitas em Ngen.exe no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="76e27-106">Changes to Ngen.exe in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span></span>  
  
-   <span data-ttu-id="76e27-107">Ngen.exe agora compila assemblies com confiança total, e a política de segurança de acesso de código (CAS) deixa de ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="76e27-107">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
-   <span data-ttu-id="76e27-108">As imagens nativas geradas com Ngen.exe não podem mais ser carregadas em aplicativos em execução com confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="76e27-108">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>  
  
 <span data-ttu-id="76e27-109">Alterações feitas em Ngen.exe no .NET Framework versão 2.0:</span><span class="sxs-lookup"><span data-stu-id="76e27-109">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>  
  
-   <span data-ttu-id="76e27-110">A instalação de um assembly também instala suas dependências, o que simplifica a sintaxe de Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-110">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>  
  
-   <span data-ttu-id="76e27-111">As imagens nativas agora podem ser compartilhadas entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-111">Native images can now be shared across application domains.</span></span>  
  
-   <span data-ttu-id="76e27-112">Uma nova ação, `update`, recria imagens que foram invalidadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-112">A new action, `update`, re-creates images that have been invalidated.</span></span>  
  
-   <span data-ttu-id="76e27-113">As ações podem ser adiadas para execução por um serviço que usa o tempo ocioso no computador para gerar e instalar imagens.</span><span class="sxs-lookup"><span data-stu-id="76e27-113">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>  
  
-   <span data-ttu-id="76e27-114">Algumas causas da invalidação de imagem são eliminadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-114">Some causes of image invalidation have been eliminated.</span></span>  
  
 <span data-ttu-id="76e27-115">No Windows 8, confira [Tarefa de Imagem Nativa](http://msdn.microsoft.com/en-us/9b1f7590-4e0d-4737-90ef-eaf696932afb).</span><span class="sxs-lookup"><span data-stu-id="76e27-115">On Windows 8, see [Native Image Task](http://msdn.microsoft.com/en-us/9b1f7590-4e0d-4737-90ef-eaf696932afb).</span></span>  
  
 <span data-ttu-id="76e27-116">Para saber mais sobre como usar o Ngen.exe e o serviço de imagem nativa, confira [Serviço de imagem nativa](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span><span class="sxs-lookup"><span data-stu-id="76e27-116">For additional information on using Ngen.exe and the native image service, see [Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-117">A sintaxe de Ngen.exe para as versões 1.0 e 1.1 do .NET Framework pode ser encontrada em [Sintaxe herdada do Gerador de Imagens Nativas (Ngen.exe)](http://msdn.microsoft.com/en-us/5a69fc7a-103f-4afc-8ab4-606adcb46324).</span><span class="sxs-lookup"><span data-stu-id="76e27-117">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](http://msdn.microsoft.com/en-us/5a69fc7a-103f-4afc-8ab4-606adcb46324).</span></span>  
  
 <span data-ttu-id="76e27-118">Essa ferramenta é instalada automaticamente com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="76e27-118">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="76e27-119">Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7).</span><span class="sxs-lookup"><span data-stu-id="76e27-119">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="76e27-120">Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="76e27-120">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="76e27-121">No prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="76e27-121">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e27-122">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76e27-122">Syntax</span></span>  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a><span data-ttu-id="76e27-123">Ações</span><span class="sxs-lookup"><span data-stu-id="76e27-123">Actions</span></span>  
 <span data-ttu-id="76e27-124">A tabela a seguir mostra a sintaxe de cada `action`.</span><span class="sxs-lookup"><span data-stu-id="76e27-124">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="76e27-125">Para obter descrições das partes individuais de um `action`, confira as tabelas [Argumentos](#ArgumentTable), [Níveis de Prioridade](#PriorityTable), [Cenários](#ScenarioTable) e [Configuração](#ConfigTable).</span><span class="sxs-lookup"><span data-stu-id="76e27-125">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="76e27-126">A tabela [Opções](#OptionTable) descreve o `options` e as opções da ajuda.</span><span class="sxs-lookup"><span data-stu-id="76e27-126">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>  
  
|<span data-ttu-id="76e27-127">Ação</span><span class="sxs-lookup"><span data-stu-id="76e27-127">Action</span></span>|<span data-ttu-id="76e27-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e27-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="76e27-129">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="76e27-129">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="76e27-130">Gere imagens nativas para um assembly e suas dependências e instale as imagens no cache de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-130">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="76e27-131">Se `/queue` for especificado, a ação será enfileirada para o serviço de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-131">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="76e27-132">A prioridade padrão é 3.</span><span class="sxs-lookup"><span data-stu-id="76e27-132">The default priority is 3.</span></span> <span data-ttu-id="76e27-133">Confira a tabela [Níveis de Prioridade](#PriorityTable).</span><span class="sxs-lookup"><span data-stu-id="76e27-133">See the [Priority Levels](#PriorityTable) table.</span></span>|  
|<span data-ttu-id="76e27-134">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="76e27-134">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="76e27-135">Exclua as imagens nativas de um assembly e suas dependências do cache de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-135">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="76e27-136">Para desinstalar uma única imagem e suas dependências, use os mesmos argumentos de linha de comando que foram usados para instalar a imagem.</span><span class="sxs-lookup"><span data-stu-id="76e27-136">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="76e27-137">**Observação:** a partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], a ação `uninstall` não tem mais suporte.</span><span class="sxs-lookup"><span data-stu-id="76e27-137">**Note:**  Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the action `uninstall` * is no longer supported.</span></span>|  
|<span data-ttu-id="76e27-138">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="76e27-138">`update` [`/queue`]</span></span>|<span data-ttu-id="76e27-139">Atualize imagens nativas que se tornaram inválidas.</span><span class="sxs-lookup"><span data-stu-id="76e27-139">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="76e27-140">Se `/queue` for especificado, as atualizações serão enfileiradas para o serviço de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-140">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="76e27-141">Como as atualizações estão sempre programadas na prioridade 3, elas são executadas quando o computador está ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-141">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|  
|<span data-ttu-id="76e27-142">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="76e27-142">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="76e27-143">Exiba o estado das imagens nativas para um assembly e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="76e27-143">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="76e27-144">Se nenhum argumento for fornecido, tudo no cache de imagem nativa será exibido.</span><span class="sxs-lookup"><span data-stu-id="76e27-144">If no argument is supplied, everything in the native image cache is displayed.</span></span>|  
|<span data-ttu-id="76e27-145">`executeQueuedItems` [`1``&#124;``2``&#124;``3`]</span><span class="sxs-lookup"><span data-stu-id="76e27-145">`executeQueuedItems` [`1``&#124;``2``&#124;``3`]</span></span><br /><br /> <span data-ttu-id="76e27-146">-ou-</span><span class="sxs-lookup"><span data-stu-id="76e27-146">-or-</span></span><br /><br /> <span data-ttu-id="76e27-147">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="76e27-147">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="76e27-148">Execute o trabalho de compilação enfileirado.</span><span class="sxs-lookup"><span data-stu-id="76e27-148">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="76e27-149">Se uma prioridade for especificada, trabalhos de compilação com prioridade maior ou igual serão executados.</span><span class="sxs-lookup"><span data-stu-id="76e27-149">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="76e27-150">Se nenhuma prioridade for especificada, todos os trabalhos de compilação enfileirados serão executados.</span><span class="sxs-lookup"><span data-stu-id="76e27-150">If no priority is specified, all queued compilation jobs are executed.</span></span>|  
|<span data-ttu-id="76e27-151">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="76e27-151">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="76e27-152">Pause o serviço de imagem nativa, deixe o serviço pausado continuar ou consulte o status do serviço.</span><span class="sxs-lookup"><span data-stu-id="76e27-152">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a><span data-ttu-id="76e27-153">Arguments</span><span class="sxs-lookup"><span data-stu-id="76e27-153">Arguments</span></span>  
  
|<span data-ttu-id="76e27-154">Argumento</span><span class="sxs-lookup"><span data-stu-id="76e27-154">Argument</span></span>|<span data-ttu-id="76e27-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e27-155">Description</span></span>|  
|--------------|-----------------|  
|`assemblyName`|<span data-ttu-id="76e27-156">O nome para exibição completo do assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-156">The full display name of the assembly.</span></span> <span data-ttu-id="76e27-157">Por exemplo, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="76e27-157">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="76e27-158">**Observação:** é possível fornecer um nome de assembly parcial, por exemplo, `myAssembly` para as ações `display` e `uninstall`.</span><span class="sxs-lookup"><span data-stu-id="76e27-158">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="76e27-159">Somente um assembly pode ser especificado por linha de comando de Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-159">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
|`assemblyPath`|<span data-ttu-id="76e27-160">O caminho explícito do assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-160">The explicit path of the assembly.</span></span> <span data-ttu-id="76e27-161">É possível especificar um caminho completo ou relativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-161">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="76e27-162">Se você especificar um nome de arquivo sem um caminho, o assembly deverá estar localizado no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="76e27-162">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="76e27-163">Somente um assembly pode ser especificado por linha de comando de Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a><span data-ttu-id="76e27-164">Níveis de Prioridade</span><span class="sxs-lookup"><span data-stu-id="76e27-164">Priority Levels</span></span>  
  
|<span data-ttu-id="76e27-165">Prioridade</span><span class="sxs-lookup"><span data-stu-id="76e27-165">Priority</span></span>|<span data-ttu-id="76e27-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e27-166">Description</span></span>|  
|--------------|-----------------|  
|`1`|<span data-ttu-id="76e27-167">As imagens nativas são geradas e instaladas imediatamente, sem aguardar o tempo ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-167">Native images are generated and installed immediately, without waiting for idle time.</span></span>|  
|`2`|<span data-ttu-id="76e27-168">As imagens nativas são geradas e instaladas sem aguardar o tempo ocioso, mas depois de todas as ações de prioridade 1 (e suas dependências) serem concluídas.</span><span class="sxs-lookup"><span data-stu-id="76e27-168">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|  
|`3`|<span data-ttu-id="76e27-169">As imagens nativas são instaladas quando o serviço de imagem nativa detecta que o computador está ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-169">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="76e27-170">Confira [Serviço de imagens nativas](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span><span class="sxs-lookup"><span data-stu-id="76e27-170">See [Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span></span>|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a><span data-ttu-id="76e27-171">Cenários</span><span class="sxs-lookup"><span data-stu-id="76e27-171">Scenarios</span></span>  
  
|<span data-ttu-id="76e27-172">Cenário</span><span class="sxs-lookup"><span data-stu-id="76e27-172">Scenario</span></span>|<span data-ttu-id="76e27-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e27-173">Description</span></span>|  
|--------------|-----------------|  
|`/Debug`|<span data-ttu-id="76e27-174">Gere imagens nativas que possam ser usadas em um depurador.</span><span class="sxs-lookup"><span data-stu-id="76e27-174">Generate native images that can be used under a debugger.</span></span>|  
|`/Profile`|<span data-ttu-id="76e27-175">Gere imagens nativas que possam ser usadas em um criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="76e27-175">Generate native images that can be used under a profiler.</span></span>|  
|`/NoDependencies`|<span data-ttu-id="76e27-176">Gere o número mínimo de imagens nativas exigidas pelas opções de cenário especificadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-176">Generate the minimum number of native images required by the specified scenario options.</span></span>|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a><span data-ttu-id="76e27-177">Config</span><span class="sxs-lookup"><span data-stu-id="76e27-177">Config</span></span>  
  
|<span data-ttu-id="76e27-178">Configuração</span><span class="sxs-lookup"><span data-stu-id="76e27-178">Configuration</span></span>|<span data-ttu-id="76e27-179">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e27-179">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="76e27-180">`/ExeConfig:` `exePath`</span><span class="sxs-lookup"><span data-stu-id="76e27-180">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="76e27-181">Use a configuração do assembly executável especificado.</span><span class="sxs-lookup"><span data-stu-id="76e27-181">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="76e27-182">Ngen.exe precisa tomar as mesmas decisões do carregador durante a associação a dependências.</span><span class="sxs-lookup"><span data-stu-id="76e27-182">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="76e27-183">Quando um componente compartilhado é carregado no tempo de execução, usando-se o método <xref:System.Reflection.Assembly.Load%2A>, o arquivo de configuração do aplicativo determina as dependências carregadas para o componente compartilhado — por exemplo, a versão de uma dependência carregada.</span><span class="sxs-lookup"><span data-stu-id="76e27-183">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="76e27-184">A opção `/ExeConfig` dá a Ngen.exe orientações sobre quais dependências seriam carregadas no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="76e27-184">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|  
|<span data-ttu-id="76e27-185">`/AppBase:` `directoryPath`</span><span class="sxs-lookup"><span data-stu-id="76e27-185">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="76e27-186">Para localizar dependências, use o diretório especificado como a base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-186">When locating dependencies, use the specified directory as the application base.</span></span>|  
  
<a name="OptionTable"></a>   
## <a name="options"></a><span data-ttu-id="76e27-187">Opções</span><span class="sxs-lookup"><span data-stu-id="76e27-187">Options</span></span>  
  
|<span data-ttu-id="76e27-188">Opção</span><span class="sxs-lookup"><span data-stu-id="76e27-188">Option</span></span>|<span data-ttu-id="76e27-189">Descrição</span><span class="sxs-lookup"><span data-stu-id="76e27-189">Description</span></span>|  
|------------|-----------------|  
|`/nologo`|<span data-ttu-id="76e27-190">Suprima a exibição do banner de inicialização da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="76e27-190">Suppress the Microsoft startup banner display.</span></span>|  
|`/silent`|<span data-ttu-id="76e27-191">Suprima a exibição das mensagens de êxito.</span><span class="sxs-lookup"><span data-stu-id="76e27-191">Suppress the display of success messages.</span></span>|  
|`/verbose`|<span data-ttu-id="76e27-192">Exiba informações detalhadas da depuração.</span><span class="sxs-lookup"><span data-stu-id="76e27-192">Display detailed information for debugging.</span></span> <span data-ttu-id="76e27-193">**Observação:** devido a limitações de sistema operacional, essa opção não exibe o máximo de informações adicionais sobre Windows 98 e Windows Millennium.</span><span class="sxs-lookup"><span data-stu-id="76e27-193">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|  
|<span data-ttu-id="76e27-194">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="76e27-194">`/help`, `/?`</span></span>|<span data-ttu-id="76e27-195">Exiba a sintaxe de comando e as opções da versão atual.</span><span class="sxs-lookup"><span data-stu-id="76e27-195">Display command syntax and options for the current release.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76e27-196">Comentários</span><span class="sxs-lookup"><span data-stu-id="76e27-196">Remarks</span></span>  
 <span data-ttu-id="76e27-197">Para executar Ngen.exe, você deve ter privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="76e27-197">To run Ngen.exe, you must have administrative privileges.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="76e27-198">Não execute Ngen.exe em assemblies que não sejam totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="76e27-198">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="76e27-199">Desde o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compila assemblies com confiança total, e a política de segurança de acesso de código (CAS) deixa de ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="76e27-199">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
 <span data-ttu-id="76e27-200">Desde o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], as imagens nativas geradas com Ngen.exe não podem mais ser carregadas em aplicativos em execução com confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="76e27-200">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="76e27-201">Em vez disso, o compilador JIT é invocado.</span><span class="sxs-lookup"><span data-stu-id="76e27-201">Instead, the just-in-time (JIT) compiler is invoked.</span></span>  
  
 <span data-ttu-id="76e27-202">O Ngen.exe gerencia imagens nativas para o assembly especificado pelo argumento `assemblyname` para a ação `install` e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="76e27-202">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="76e27-203">As dependências são determinadas com base nas referências do manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-203">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="76e27-204">O único cenário no qual você precisa instalar uma dependência separadamente é quando o aplicativo a carrega usando a reflexão, por exemplo, chamando o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="76e27-204">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76e27-205">Não use o método <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> com imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-205">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> method with native images.</span></span> <span data-ttu-id="76e27-206">Uma imagem carregada com esse método não pode ser usada por outros assemblies no contexto da execução.</span><span class="sxs-lookup"><span data-stu-id="76e27-206">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>  
  
 <span data-ttu-id="76e27-207">Ngen.exe mantém uma contagem das dependências.</span><span class="sxs-lookup"><span data-stu-id="76e27-207">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="76e27-208">Por exemplo, suponhamos que `MyAssembly.exe` e `YourAssembly.exe` estejam ambos instalados no cache de imagem nativa, e ambos tenham referências para `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="76e27-208">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="76e27-209">Se `MyAssembly.exe` for desinstalado, `OurDependency.dll` não será desinstalado.</span><span class="sxs-lookup"><span data-stu-id="76e27-209">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="76e27-210">Ele só é removido quando `YourAssembly.exe` também é desinstalado.</span><span class="sxs-lookup"><span data-stu-id="76e27-210">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>  
  
 <span data-ttu-id="76e27-211">Se você estiver gerando uma imagem nativa para um assembly no cache de assembly global, especifique seu nome para exibição.</span><span class="sxs-lookup"><span data-stu-id="76e27-211">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="76e27-212">Consulte <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="76e27-212">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="76e27-213">As imagens nativas geradas por Ngen.exe podem ser compartilhadas entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-213">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="76e27-214">Isso significa que é possível usar Ngen.exe em cenários de aplicativo que exijam que os assemblies sejam compartilhados entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-214">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="76e27-215">Para especificar a neutralidade do domínio:</span><span class="sxs-lookup"><span data-stu-id="76e27-215">To specify domain neutrality:</span></span>  
  
-   <span data-ttu-id="76e27-216">Aplique o atributo <xref:System.LoaderOptimizationAttribute> ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-216">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>  
  
-   <span data-ttu-id="76e27-217">Defina a propriedade <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=fullName> quando você cria informações de configuração para um novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-217">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=fullName> property when you create setup information for a new application domain.</span></span>  
  
 <span data-ttu-id="76e27-218">Sempre use o código neutro de domínio ao carregar o mesmo assembly em vários domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-218">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="76e27-219">Se uma imagem nativa for carregada em um domínio de aplicativo não compartilhado depois de ter sido carregada em um domínio compartilhado, ela não poderá ser usada.</span><span class="sxs-lookup"><span data-stu-id="76e27-219">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-220">O código neutro de domínio não pode ser descarregado, e o desempenho pode ser um pouco mais lento, especialmente durante o acesso a membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="76e27-220">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>  
  
 <span data-ttu-id="76e27-221">Nesta seção Observações:</span><span class="sxs-lookup"><span data-stu-id="76e27-221">In this Remarks section:</span></span>  
  
-   [<span data-ttu-id="76e27-222">Gerar imagens para cenários diferentes</span><span class="sxs-lookup"><span data-stu-id="76e27-222">Generating images for different scenarios</span></span>](#Scenarios)  
  
-   [<span data-ttu-id="76e27-223">Determinar quando usar imagens nativas</span><span class="sxs-lookup"><span data-stu-id="76e27-223">Determining when to Use native images</span></span>](#WhenToUse)  
  
    -   [<span data-ttu-id="76e27-224">Uso de memória aprimorado</span><span class="sxs-lookup"><span data-stu-id="76e27-224">Improved memory use</span></span>](#Memory)  
  
    -   [<span data-ttu-id="76e27-225">Inicialização mais rápida do aplicativo</span><span class="sxs-lookup"><span data-stu-id="76e27-225">Faster application startup</span></span>](#Startup)  
  
    -   [<span data-ttu-id="76e27-226">Resumo das considerações de uso</span><span class="sxs-lookup"><span data-stu-id="76e27-226">Summary of usage considerations</span></span>](#UsageSummary)  
  
-   [<span data-ttu-id="76e27-227">Importância de endereços de base do assembly</span><span class="sxs-lookup"><span data-stu-id="76e27-227">Importance of assembly base addresses</span></span>](#BaseAddresses)  
  
-   [<span data-ttu-id="76e27-228">Associação forçada</span><span class="sxs-lookup"><span data-stu-id="76e27-228">Hard binding</span></span>](#HardBinding)  
  
    -   [<span data-ttu-id="76e27-229">Especificar uma dica de associação para uma dependência</span><span class="sxs-lookup"><span data-stu-id="76e27-229">Specifying a binding hint for a dependency</span></span>](#DependencyHint)  
  
    -   [<span data-ttu-id="76e27-230">Especificar uma dica de associação padrão para um assembly</span><span class="sxs-lookup"><span data-stu-id="76e27-230">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)  
  
-   [<span data-ttu-id="76e27-231">Processamento adiado</span><span class="sxs-lookup"><span data-stu-id="76e27-231">Deferred processing</span></span>](#Deferred)  
  
-   [<span data-ttu-id="76e27-232">Imagens nativas e compilação JIT</span><span class="sxs-lookup"><span data-stu-id="76e27-232">Native images and JIT compilation</span></span>](#JITCompilation)  
  
    -   [<span data-ttu-id="76e27-233">Imagens inválidas</span><span class="sxs-lookup"><span data-stu-id="76e27-233">Invalid images</span></span>](#InvalidImages)  
  
-   [<span data-ttu-id="76e27-234">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="76e27-234">Troubleshooting</span></span>](#Troubleshooting)  
  
    -   [<span data-ttu-id="76e27-235">Visualizador de log da associação do assembly</span><span class="sxs-lookup"><span data-stu-id="76e27-235">Assembly Binding Log Viewer</span></span>](#Fusion)  
  
    -   [<span data-ttu-id="76e27-236">O assistente de depuração gerenciado JITCompilationStart</span><span class="sxs-lookup"><span data-stu-id="76e27-236">The JITCompilationStart managed debugging assistant</span></span>](#MDA)  
  
    -   [<span data-ttu-id="76e27-237">Recusa da geração automática de imagem nativa</span><span class="sxs-lookup"><span data-stu-id="76e27-237">Opting out of native image generation</span></span>](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="76e27-238">Gerar imagens para cenários diferentes</span><span class="sxs-lookup"><span data-stu-id="76e27-238">Generating images for     different scenarios</span></span>  
 <span data-ttu-id="76e27-239">Depois que você tiver gerado uma imagem nativa para um assembly, o tempo de execução tenta localizar e usar automaticamente essa imagem nativa sempre que executa o assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-239">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="76e27-240">Várias imagens podem ser geradas, dependendo dos cenários de uso.</span><span class="sxs-lookup"><span data-stu-id="76e27-240">Multiple images can be generated, depending on usage scenarios.</span></span>  
  
 <span data-ttu-id="76e27-241">Por exemplo, se você executar um assembly em um cenário de depuração ou de criação de perfil, o tempo de execução procurará uma imagem nativa gerada com as opções `/Debug` ou `/Profile`.</span><span class="sxs-lookup"><span data-stu-id="76e27-241">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="76e27-242">Caso ele não consiga encontrar uma imagem nativa correspondente, o tempo de execução é revertido para a compilação JIT padrão.</span><span class="sxs-lookup"><span data-stu-id="76e27-242">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="76e27-243">A única maneira de depurar imagens nativas é criando uma imagem nativa com a opção `/Debug`.</span><span class="sxs-lookup"><span data-stu-id="76e27-243">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>  
  
 <span data-ttu-id="76e27-244">Como a ação `uninstall` também reconhece cenários, é possível desinstalar todos os cenários ou apenas os cenários selecionados.</span><span class="sxs-lookup"><span data-stu-id="76e27-244">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="76e27-245">Determinar quando usar imagens nativas</span><span class="sxs-lookup"><span data-stu-id="76e27-245">Determining when to Use native images</span></span>  
 <span data-ttu-id="76e27-246">Imagens nativas podem oferecer melhorias de desempenho em duas áreas: melhor uso da memória e tempo de inicialização reduzido.</span><span class="sxs-lookup"><span data-stu-id="76e27-246">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-247">O desempenho de imagens nativas depende de vários fatores que dificultam a análise como, por exemplo, padrões de acesso ao código e aos dados, quantas chamadas são feitas entre os limites do módulo e quantas dependências já foram carregadas por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="76e27-247">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="76e27-248">A única maneira de determinar se as imagens nativas beneficiam o aplicativo é por meio de medidas de desempenho cuidadosas nos principais cenários de implantação.</span><span class="sxs-lookup"><span data-stu-id="76e27-248">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a><span data-ttu-id="76e27-249">Uso de memória aprimorado</span><span class="sxs-lookup"><span data-stu-id="76e27-249">Improved memory use</span></span>  
 <span data-ttu-id="76e27-250">Imagens nativas podem melhorar significativamente o uso da memória quando o código é compartilhado entre processos.</span><span class="sxs-lookup"><span data-stu-id="76e27-250">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="76e27-251">Como imagens nativas são arquivos do Windows PE, uma única cópia de um arquivo .dll pode ser compartilhada por vários processos; por outro lado, o código nativo produzido pelo compilador JIT é armazenado em memória privada e não pode ser compartilhada.</span><span class="sxs-lookup"><span data-stu-id="76e27-251">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>  
  
 <span data-ttu-id="76e27-252">Aplicativos executados em serviços de terminal também podem aproveitar páginas de código compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-252">Applications that are run under terminal services can also benefit from shared code pages.</span></span>  
  
 <span data-ttu-id="76e27-253">Além disso, o não carregamento do compilador JIT salva uma quantidade de memória fixa para cada instância do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-253">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a><span data-ttu-id="76e27-254">Inicialização mais rápida do aplicativo</span><span class="sxs-lookup"><span data-stu-id="76e27-254">Faster application startup</span></span>  
 <span data-ttu-id="76e27-255">A pré-compilação de assemblies com Ngen.exe pode melhorar o tempo de inicialização de alguns aplicativos.</span><span class="sxs-lookup"><span data-stu-id="76e27-255">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="76e27-256">Em geral, os ganhos podem acontecer quando aplicativos compartilham assemblies de componente, porque depois que o primeiro aplicativo foi iniciado os componentes compartilhados já estão carregados para aplicativos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="76e27-256">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="76e27-257">A inicialização fria, em que todos os assemblies em um aplicativo devem ser carregados do disco rígido, não beneficia tanto quanto imagens nativas porque o tempo de acesso ao disco rígido predomina.</span><span class="sxs-lookup"><span data-stu-id="76e27-257">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>  
  
 <span data-ttu-id="76e27-258">A associação forçada pode afetar o tempo de inicialização, pois todas as imagens solidamente associadas ao assembly do aplicativo principal devem ser carregadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="76e27-258">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-259">Antes do [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], você deve colocar componentes compartilhados, de nome forte, no cache de assembly global, porque o carregador realiza a validação extra em assemblies de nome forte que não estão no cache de assembly global, o que elimina efetivamente qualquer melhoria no tempo da inicialização obtido usando imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-259">Before the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="76e27-260">As otimizações que foram introduzidas no [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removeram a validação extra.</span><span class="sxs-lookup"><span data-stu-id="76e27-260">Optimizations that were introduced in the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removed the extra validation.</span></span>  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a><span data-ttu-id="76e27-261">Resumo das considerações de uso</span><span class="sxs-lookup"><span data-stu-id="76e27-261">Summary of usage considerations</span></span>  
 <span data-ttu-id="76e27-262">As seguintes considerações gerais e as considerações de aplicativo podem ajudá-lo na decisão de assumir o esforço de avaliação das imagens nativas para o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="76e27-262">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>  
  
-   <span data-ttu-id="76e27-263">Imagens nativas são carregadas mais rapidamente do que MSIL porque eliminam a necessidade de muitas atividades de inicialização, como a compilação JIT e a verificação da segurança de tipos.</span><span class="sxs-lookup"><span data-stu-id="76e27-263">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>  
  
-   <span data-ttu-id="76e27-264">As imagens nativas exigem um conjunto de trabalho inicial menor porque não há necessidade do compilador JIT.</span><span class="sxs-lookup"><span data-stu-id="76e27-264">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>  
  
-   <span data-ttu-id="76e27-265">As imagens nativas permitem o compartilhamento de código entre processos.</span><span class="sxs-lookup"><span data-stu-id="76e27-265">Native images enable code sharing between processes.</span></span>  
  
-   <span data-ttu-id="76e27-266">As imagens nativas exigem mais espaço em disco rígido do que assemblies MSIL e podem exigir um tempo considerável para geração.</span><span class="sxs-lookup"><span data-stu-id="76e27-266">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>  
  
-   <span data-ttu-id="76e27-267">As imagens nativas devem ser mantidas.</span><span class="sxs-lookup"><span data-stu-id="76e27-267">Native images must be maintained.</span></span>  
  
    -   <span data-ttu-id="76e27-268">As imagens precisam ser regeneradas quando o assembly original ou uma de suas dependências é atendida.</span><span class="sxs-lookup"><span data-stu-id="76e27-268">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>  
  
    -   <span data-ttu-id="76e27-269">Um único assembly pode precisar de várias imagens nativas que serão usadas em aplicativos diferentes ou em cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="76e27-269">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="76e27-270">Por exemplo, as informações de configuração em dois aplicativos podem resultar em decisões de associação diferentes para o mesmo assembly dependente.</span><span class="sxs-lookup"><span data-stu-id="76e27-270">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>  
  
    -   <span data-ttu-id="76e27-271">As imagens nativas devem ser geradas por um administrador; ou seja, com base em uma conta do Windows no grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="76e27-271">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>  
  
 <span data-ttu-id="76e27-272">Além dessas considerações gerais, a natureza do aplicativo deve ser levada em consideração durante a determinação da possibilidade das imagens nativas podem oferecer um benefício de desempenho:</span><span class="sxs-lookup"><span data-stu-id="76e27-272">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>  
  
-   <span data-ttu-id="76e27-273">Se o aplicativo for executado em um ambiente que usa vários componentes compartilhados, as imagens nativas permitirão que os componentes sejam compartilhados por vários processos.</span><span class="sxs-lookup"><span data-stu-id="76e27-273">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>  
  
-   <span data-ttu-id="76e27-274">Se o aplicativo usar vários domínios de aplicativo, as imagens nativas permitirão que as páginas de código sejam compartilhadas entre domínios.</span><span class="sxs-lookup"><span data-stu-id="76e27-274">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76e27-275">No .NET Framework versões 1.0 e 1.1, as imagens nativas não podem ser compartilhadas entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-275">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="76e27-276">Esse pode não ser o caso na versão 2.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="76e27-276">This is not the case in version 2.0 or later.</span></span>  
  
-   <span data-ttu-id="76e27-277">Se o aplicativo for executado no servidor Host da Sessão da Área de Trabalho Remota, as imagens nativas permitirão o compartilhamento das páginas de código.</span><span class="sxs-lookup"><span data-stu-id="76e27-277">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>  
  
-   <span data-ttu-id="76e27-278">Os aplicativos grandes normalmente se beneficiam da compilação para imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-278">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="76e27-279">Os aplicativos pequenos normalmente não beneficiam.</span><span class="sxs-lookup"><span data-stu-id="76e27-279">Small applications generally do not benefit.</span></span>  
  
-   <span data-ttu-id="76e27-280">Para aplicativos executados por muito tempo, a compilação JIT do tempo de execução é um pouco melhor do que a de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-280">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="76e27-281">(A associação forçada pode atenuar essa diferença de desempenho em algum grau.)</span><span class="sxs-lookup"><span data-stu-id="76e27-281">(Hard binding can mitigate this performance difference to some degree.)</span></span>  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="76e27-282">Importância de endereços de base do assembly</span><span class="sxs-lookup"><span data-stu-id="76e27-282">Importance of assembly base addresses</span></span>  
 <span data-ttu-id="76e27-283">Como são arquivos do Windows PE, as imagens nativas estão sujeitas aos mesmos problemas de rebase de outros arquivos executáveis.</span><span class="sxs-lookup"><span data-stu-id="76e27-283">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="76e27-284">O custo de desempenho da realocação ficará ainda mais evidente se a associação forçada não for utilizada.</span><span class="sxs-lookup"><span data-stu-id="76e27-284">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>  
  
 <span data-ttu-id="76e27-285">Para definir o endereço base para uma imagem nativa, use a opção apropriada do compilador para definir o endereço base do assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-285">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="76e27-286">Ngen.exe usa esse endereço base para a imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-286">Ngen.exe uses this base address for the native image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-287">As imagens nativas são maiores que os assemblies gerenciados a partir dos quais foram criadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-287">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="76e27-288">Os endereços de base devem ser calculados para possibilitar tamanhos maiores.</span><span class="sxs-lookup"><span data-stu-id="76e27-288">Base addresses must be calculated to allow for these larger sizes.</span></span>  
  
 <span data-ttu-id="76e27-289">É possível usar uma ferramenta como dumpbin.exe para exibir o endereço de base preferencial de uma imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-289">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a><span data-ttu-id="76e27-290">Associação forçada</span><span class="sxs-lookup"><span data-stu-id="76e27-290">Hard binding</span></span>  
 <span data-ttu-id="76e27-291">A associação forçada aumenta a taxa de transferência e reduz o tamanho do conjunto de trabalho de imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-291">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="76e27-292">A desvantagem da associação forçada é que todas as imagens associadas forçadamente a um assembly devem ser carregadas quando o assembly é carregado.</span><span class="sxs-lookup"><span data-stu-id="76e27-292">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="76e27-293">Isso pode aumentar significativamente o tempo de inicialização de um aplicativo grande.</span><span class="sxs-lookup"><span data-stu-id="76e27-293">This can significantly increase startup time for a large application.</span></span>  
  
 <span data-ttu-id="76e27-294">A associação forçada é apropriada para dependências carregadas em todos os cenários de desempenho crítico do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-294">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="76e27-295">Assim como acontece com qualquer aspecto do uso da imagem nativa, medidas de desempenho cuidadosas são a única maneira de determinar se a associação forçada melhora o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="76e27-295">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>  
  
 <span data-ttu-id="76e27-296">Os atributos <xref:System.Runtime.CompilerServices.DependencyAttribute> e <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> permitem que você dê dicas de associação forçada a Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-296">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-297">Esses atributos são dicas para Ngen.exe, e não comandos.</span><span class="sxs-lookup"><span data-stu-id="76e27-297">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="76e27-298">O uso deles não garante a associação forçada.</span><span class="sxs-lookup"><span data-stu-id="76e27-298">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="76e27-299">O significado desses atributos pode ser alterado em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="76e27-299">The meaning of these attributes may change in future releases.</span></span>  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="76e27-300">Especificar uma dica de associação para uma dependência</span><span class="sxs-lookup"><span data-stu-id="76e27-300">Specifying a binding hint for a dependency</span></span>  
 <span data-ttu-id="76e27-301">Aplique o <xref:System.Runtime.CompilerServices.DependencyAttribute> a um assembly para indicar a probabilidade de que uma dependência especificada será carregada.</span><span class="sxs-lookup"><span data-stu-id="76e27-301">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="76e27-302"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=fullName> indica que a associação forçada é apropriada, <xref:System.Runtime.CompilerServices.LoadHint.Default> indica que o padrão da dependência deve ser usado e <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indica que a associação forçada não é apropriada.</span><span class="sxs-lookup"><span data-stu-id="76e27-302"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=fullName> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>  
  
 <span data-ttu-id="76e27-303">O código a seguir mostra os atributos de um assembly que possui duas dependências.</span><span class="sxs-lookup"><span data-stu-id="76e27-303">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="76e27-304">A primeira dependência (Assembly1) é uma candidata apropriada à associação forçada, mas a segunda (Assembly2) não é.</span><span class="sxs-lookup"><span data-stu-id="76e27-304">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>  
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>  
```  
  
```csharp  
using System.Runtime.CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]  
```  
  
```cpp  
using namespace System::Runtime::CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];  
```  
  
 <span data-ttu-id="76e27-305">O nome do assembly não inclui a extensão do nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="76e27-305">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="76e27-306">Os nomes para exibição podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="76e27-306">Display names can be used.</span></span>  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="76e27-307">Especificar uma dica de associação padrão para um assembly</span><span class="sxs-lookup"><span data-stu-id="76e27-307">Specifying a default binding hint for an assembly</span></span>  
 <span data-ttu-id="76e27-308">As dicas de associação padrão só são necessárias para assemblies que serão usados imediata e frequentemente por qualquer aplicativo que tenha uma dependência neles.</span><span class="sxs-lookup"><span data-stu-id="76e27-308">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="76e27-309">Aplique o <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> com <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=fullName> a esses assemblies para especificar que a associação forçada deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="76e27-309">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=fullName> to such assemblies to specify that hard binding should be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-310">Não há motivo para aplicar <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> a assemblies .dll que não estejam nessa categoria, porque a aplicação do atributo com qualquer valor diferente de <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=fullName> tem o mesmo efeito de não aplicar o atributo.</span><span class="sxs-lookup"><span data-stu-id="76e27-310">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=fullName> has the same effect as not applying the attribute at all.</span></span>  
  
 <span data-ttu-id="76e27-311">A Microsoft usa o <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> para especificar que a associação forçada é o padrão para um número muito pequeno de assemblies no .NET Framework como, por exemplo, mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="76e27-311">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a><span data-ttu-id="76e27-312">Processamento adiado</span><span class="sxs-lookup"><span data-stu-id="76e27-312">Deferred processing</span></span>  
 <span data-ttu-id="76e27-313">A geração de imagens nativas para um aplicativo muito grande pode demorar um tempo considerável.</span><span class="sxs-lookup"><span data-stu-id="76e27-313">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="76e27-314">Da mesma forma, alterações feitas em um componente compartilhado ou alterações feitas em configurações do computador podem exigir a atualização de muitas imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-314">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="76e27-315">As ações `install` e `update` têm uma opção `/queue` que enfileira a operação para execução adiada pelo serviço de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-315">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="76e27-316">Além disso, Ngen.exe tem ações `queue` e `executeQueuedItems` que oferecem certo controle sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="76e27-316">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="76e27-317">Para saber mais, confira [Serviço de imagens nativas](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span><span class="sxs-lookup"><span data-stu-id="76e27-317">For more information, see [Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span></span>  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="76e27-318">Imagens nativas e compilação JIT</span><span class="sxs-lookup"><span data-stu-id="76e27-318">Native images and JIT compilation</span></span>  
 <span data-ttu-id="76e27-319">Se encontrar algum método em um assembly que não puder gerar, Ngen.exe os excluirá da imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-319">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="76e27-320">Ao executar esse assembly, o tempo de execução o reverte para compilação JIT dos métodos que não foram incluídos na imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-320">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>  
  
 <span data-ttu-id="76e27-321">Além disso, as imagens nativas não serão usadas se o assembly tiver sido atualizado, ou se a imagem tiver sido invalidada por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="76e27-321">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a><span data-ttu-id="76e27-322">Imagens inválidas</span><span class="sxs-lookup"><span data-stu-id="76e27-322">Invalid images</span></span>  
 <span data-ttu-id="76e27-323">Quando você usa Ngen.exe para criar uma imagem nativa de um assembly, a saída depende das opções de linha de comando especificadas e de determinadas configurações do computador.</span><span class="sxs-lookup"><span data-stu-id="76e27-323">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="76e27-324">Entre essas configurações estão as seguintes:</span><span class="sxs-lookup"><span data-stu-id="76e27-324">These settings include the following:</span></span>  
  
-   <span data-ttu-id="76e27-325">A versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76e27-325">The version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="76e27-326">A versão do sistema operacional, se a alteração for da família Windows 9x para a família Windows NT.</span><span class="sxs-lookup"><span data-stu-id="76e27-326">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
-   <span data-ttu-id="76e27-327">A identidade exata do assembly (recompilação altera a identidade).</span><span class="sxs-lookup"><span data-stu-id="76e27-327">The exact identity of the assembly (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="76e27-328">A identidade exata de todos os assemblies aos quais o assembly faz referência (recompilação altera a identidade).</span><span class="sxs-lookup"><span data-stu-id="76e27-328">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="76e27-329">Fatores de segurança.</span><span class="sxs-lookup"><span data-stu-id="76e27-329">Security factors.</span></span>  
  
 <span data-ttu-id="76e27-330">Ngen.exe registra essas informações ao gerar uma imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-330">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="76e27-331">Quando você executa um assembly, o tempo de execução procura a imagem nativa gerada com opções e configurações correspondentes ao ambiente atual do computador.</span><span class="sxs-lookup"><span data-stu-id="76e27-331">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="76e27-332">O tempo de execução será revertido para a compilação JIT de um assembly se não conseguir encontrar uma imagem nativa correspondente.</span><span class="sxs-lookup"><span data-stu-id="76e27-332">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="76e27-333">As seguintes alterações feitas nas configurações e no ambiente de um computador invalidam imagens nativas:</span><span class="sxs-lookup"><span data-stu-id="76e27-333">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>  
  
-   <span data-ttu-id="76e27-334">A versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76e27-334">The version of the .NET Framework.</span></span>  
  
     <span data-ttu-id="76e27-335">Se você aplicar uma atualização ao .NET Framework, todas as imagens nativas criadas usando-se Ngen.exe serão invalidadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-335">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="76e27-336">Por esse motivo, todas as atualizações do .NET Framework executam o comando `Ngen Update`, para garantir que todas as imagens nativas sejam regeneradas.</span><span class="sxs-lookup"><span data-stu-id="76e27-336">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="76e27-337">O .NET Framework cria automaticamente novas imagens nativas para as bibliotecas do .NET Framework instaladas.</span><span class="sxs-lookup"><span data-stu-id="76e27-337">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>  
  
-   <span data-ttu-id="76e27-338">A versão do sistema operacional, se a alteração for da família Windows 9x para a família Windows NT.</span><span class="sxs-lookup"><span data-stu-id="76e27-338">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
     <span data-ttu-id="76e27-339">Por exemplo, se a versão do sistema operacional em execução em um computador mudar do Windows 98 para o Windows XP, todas as imagens nativas armazenadas no cache de imagem nativa serão invalidadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-339">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="76e27-340">No entanto, se o sistema operacional mudar do Windows 2000 para o Windows XP, as imagens não serão invalidadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-340">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>  
  
-   <span data-ttu-id="76e27-341">A identidade exata do assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-341">The exact identity of the assembly.</span></span>  
  
     <span data-ttu-id="76e27-342">Se você recompilar um assembly, a imagem nativa correspondente do assembly será invalidada.</span><span class="sxs-lookup"><span data-stu-id="76e27-342">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>  
  
-   <span data-ttu-id="76e27-343">A identidade exata de todos os assemblies aos quais o assembly faz referência.</span><span class="sxs-lookup"><span data-stu-id="76e27-343">The exact identity of any assemblies the assembly references.</span></span>  
  
     <span data-ttu-id="76e27-344">Se você atualizar um assembly gerenciado, todas as imagens nativas que dependam direta ou indiretamente desse assembly serão invalidadas e precisarão ser regeneradas.</span><span class="sxs-lookup"><span data-stu-id="76e27-344">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="76e27-345">Isso inclui as referências comuns e as dependências associadas forçadamente.</span><span class="sxs-lookup"><span data-stu-id="76e27-345">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="76e27-346">Sempre que uma atualização de software for aplicada, o programa de instalação deverá executar um comando `Ngen Update` para garantir que as todas as imagens nativas dependentes sejam regeneradas.</span><span class="sxs-lookup"><span data-stu-id="76e27-346">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>  
  
-   <span data-ttu-id="76e27-347">Fatores de segurança.</span><span class="sxs-lookup"><span data-stu-id="76e27-347">Security factors.</span></span>  
  
     <span data-ttu-id="76e27-348">A alteração da política de segurança do computador para restringir permissões concedidas anteriormente a um assembly pode invalidar uma imagem nativa compilada anteriormente para esse assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-348">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>  
  
     <span data-ttu-id="76e27-349">Para obter informações detalhadas sobre como o Common Language Runtime administra a segurança de acesso do código e como usar permissões, confira [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="76e27-349">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../../../docs/framework/misc/code-access-security.md).</span></span>  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="76e27-350">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="76e27-350">Troubleshooting</span></span>  
 <span data-ttu-id="76e27-351">Os tópicos de solução de problemas a seguir permitem que você veja quais imagens nativas estão sendo usadas e quais não podem ser usadas por seu aplicativo, para determinar quando o compilador JIT começa a compilar um método, e mostra como recusar a compilação de imagem nativa dos métodos especificados.</span><span class="sxs-lookup"><span data-stu-id="76e27-351">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="76e27-352">Visualizador de Log de Associação do Assembly</span><span class="sxs-lookup"><span data-stu-id="76e27-352">Assembly Binding Log Viewer</span></span>  
 <span data-ttu-id="76e27-353">Para confirmar que as imagens nativas estão sendo usadas pelo aplicativo, é possível usar [Fuslogvw.exe (Visualizador do Log de Associações de Assembly)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="76e27-353">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="76e27-354">Selecione **Imagens Nativas** na caixa **Categorias de Log** na janela do visualizador de log da associação.</span><span class="sxs-lookup"><span data-stu-id="76e27-354">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="76e27-355">O Fuslogvw.exe fornece informações sobre por que uma imagem nativa foi rejeitada.</span><span class="sxs-lookup"><span data-stu-id="76e27-355">Fuslogvw.exe provides information about why a native image was rejected.</span></span>  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="76e27-356">O assistente de depuração gerenciado JITCompilationStart</span><span class="sxs-lookup"><span data-stu-id="76e27-356">The JITCompilationStart managed debugging assistant</span></span>  
 <span data-ttu-id="76e27-357">É possível usar o MDA (Assistente para depuração gerenciada) [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) para determinar quando o compilador JIT começa a compilar uma função.</span><span class="sxs-lookup"><span data-stu-id="76e27-357">You can use the [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="76e27-358">Recusa da geração automática de imagem nativa</span><span class="sxs-lookup"><span data-stu-id="76e27-358">Opting out of native image generation</span></span>  
 <span data-ttu-id="76e27-359">Em alguns casos, o NGen.exe pode ter dificuldade para gerar uma imagem nativa para um método específico, ou talvez você prefira que o método seja compilado pelo JIT, em vez de ser compilado para uma imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-359">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="76e27-360">Nesse caso, você pode usar o atributo `System.Runtime.BypassNGenAttribute` para impedir que o NGen.exe gere uma imagem nativa para um método específico.</span><span class="sxs-lookup"><span data-stu-id="76e27-360">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="76e27-361">O atributo deve ser aplicado individualmente a cada método cujo código você não quer incluir na imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-361">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="76e27-362">O NGen.exe reconhece o atributo e não gera um código na imagem nativa para o método correspondente.</span><span class="sxs-lookup"><span data-stu-id="76e27-362">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>  
  
 <span data-ttu-id="76e27-363">No entanto, observe que `BypassNGenAttribute` não está definido como um tipo na biblioteca de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76e27-363">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class library.</span></span> <span data-ttu-id="76e27-364">Para consumir o atributo em seu código, primeiro definia-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="76e27-364">In order to consume the attribute in your code, you must first define it as follows:</span></span>  
  
 <span data-ttu-id="76e27-365">[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)] [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="76e27-365">[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)] [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]</span></span>  
  
 <span data-ttu-id="76e27-366">Depois, você pode aplicar o atributo de acordo com o método.</span><span class="sxs-lookup"><span data-stu-id="76e27-366">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="76e27-367">O exemplo a seguir instrui o Gerador de imagem nativa que ele não deve gerar uma imagem nativa para o método `ExampleClass.ToJITCompile`.</span><span class="sxs-lookup"><span data-stu-id="76e27-367">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>  
  
 <span data-ttu-id="76e27-368">[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)] [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="76e27-368">[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)] [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]</span></span>  
  
## <a name="examples"></a><span data-ttu-id="76e27-369">Exemplos</span><span class="sxs-lookup"><span data-stu-id="76e27-369">Examples</span></span>  
 <span data-ttu-id="76e27-370">O comando a seguir gera uma imagem nativa para `ClientApp.exe`, localizado no diretório atual, e instala a imagem no cache de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-370">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="76e27-371">Se existir um arquivo de configuração para o assembly, Ngen.exe o usará.</span><span class="sxs-lookup"><span data-stu-id="76e27-371">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="76e27-372">Além de isso, imagens nativas são geradas para todos os arquivos .dll a que `ClientApp.exe` faz referência.</span><span class="sxs-lookup"><span data-stu-id="76e27-372">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>  
  
```  
ngen install ClientApp.exe  
```  
  
 <span data-ttu-id="76e27-373">Uma imagem instalada com Ngen.exe também é chamada de raiz.</span><span class="sxs-lookup"><span data-stu-id="76e27-373">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="76e27-374">Uma raiz pode ser um aplicativo ou um componente compartilhado.</span><span class="sxs-lookup"><span data-stu-id="76e27-374">A root can be an application or a shared component.</span></span>  
  
 <span data-ttu-id="76e27-375">O comando a seguir gera uma imagem nativa para `MyAssembly.exe` com o caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="76e27-375">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 <span data-ttu-id="76e27-376">Para localizar assemblies e as suas dependências, Ngen.exe usa a mesma lógica de investigação usada pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="76e27-376">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="76e27-377">Por padrão, o diretório que contém `ClientApp.exe` é usado como diretório base do aplicativo, e toda investigação de assembly começa nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="76e27-377">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="76e27-378">É possível substituir esse comportamento usando-se a opção `/AppBase`.</span><span class="sxs-lookup"><span data-stu-id="76e27-378">You can override this behavior by using the `/AppBase` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-379">Essa é uma alteração no comportamento de Ngen.exe no .NET Framework versões 1.0 e 1.1, em que a base do aplicativo é definida como o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="76e27-379">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>  
  
 <span data-ttu-id="76e27-380">Um assembly pode ter uma dependência sem uma referência, por exemplo, se carregar um arquivo .dll usando o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="76e27-380">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="76e27-381">É possível criar uma imagem nativa para esse arquivo .dll usando-se as informações de configuração do assembly do aplicativo, com a opção `/ExeConfig`.</span><span class="sxs-lookup"><span data-stu-id="76e27-381">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="76e27-382">O comando a seguir gera uma imagem nativa para `MyLib.dll,` usando as informações de configuração de `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="76e27-382">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="76e27-383">Os assemblies instalados dessa forma não são removidos quando o aplicativo é removido.</span><span class="sxs-lookup"><span data-stu-id="76e27-383">Assemblies installed in this way are not removed when the application is removed.</span></span>  
  
 <span data-ttu-id="76e27-384">Para desinstalar uma dependência, use as mesmas opções de linha de comando que foram usadas para instalá-la.</span><span class="sxs-lookup"><span data-stu-id="76e27-384">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="76e27-385">O comando a seguir desinstala o `MyLib.dll` do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="76e27-385">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="76e27-386">Para criar uma imagem nativa para um assembly no cache de assembly global, use o nome para exibição do assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-386">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="76e27-387">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="76e27-387">For example:</span></span>  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 <span data-ttu-id="76e27-388">NGen.exe gera um conjunto separado de imagens para cada cenário instalado.</span><span class="sxs-lookup"><span data-stu-id="76e27-388">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="76e27-389">Por exemplo, os seguintes comandos instalam um conjunto completo de imagens nativas para operação normal, outro conjunto completo para depuração e um terceiro para criação de perfil:</span><span class="sxs-lookup"><span data-stu-id="76e27-389">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="76e27-390">Exibindo o Cache de Imagem Nativa</span><span class="sxs-lookup"><span data-stu-id="76e27-390">Displaying the Native Image Cache</span></span>  
 <span data-ttu-id="76e27-391">Depois de serem instaladas no cache, as imagens nativas poderão ser exibidas usando-se Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-391">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="76e27-392">O comando a seguir exibe todas as imagens nativas no cache de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-392">The following command displays all native images in the native image cache.</span></span>  
  
```  
ngen display  
```  
  
 <span data-ttu-id="76e27-393">A ação `display` lista todos os assemblies raiz primeiro, seguido de uma lista de todas as imagens nativas no computador.</span><span class="sxs-lookup"><span data-stu-id="76e27-393">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>  
  
 <span data-ttu-id="76e27-394">Use o nome simples de um assembly para exibir informações somente desse assembly.</span><span class="sxs-lookup"><span data-stu-id="76e27-394">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="76e27-395">O seguinte comando exibe todas as imagens nativas no cache de imagem nativa que correspondem ao nome parcial `MyAssembly`, suas dependências e todas as raízes que tenham uma dependência em `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="76e27-395">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>  
  
```  
ngen display MyAssembly  
```  
  
 <span data-ttu-id="76e27-396">Saber quais raízes dependem de um assembly de componente compartilhado é útil na avaliação do impacto de uma ação `update` depois que o componente compartilhado é atualizado.</span><span class="sxs-lookup"><span data-stu-id="76e27-396">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>  
  
 <span data-ttu-id="76e27-397">Se especificar a extensão de arquivo de um assembly, você deverá especificar o caminho ou executar Ngen.exe no diretório que contém o assembly:</span><span class="sxs-lookup"><span data-stu-id="76e27-397">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 <span data-ttu-id="76e27-398">O comando a seguir exibe todas as imagens nativas no cache de imagem nativa com o nome `MyAssembly`e a versão 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="76e27-398">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a><span data-ttu-id="76e27-399">Atualizando Imagens</span><span class="sxs-lookup"><span data-stu-id="76e27-399">Updating Images</span></span>  
 <span data-ttu-id="76e27-400">As imagens normalmente são atualizadas depois que um componente compartilhado é atualizado.</span><span class="sxs-lookup"><span data-stu-id="76e27-400">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="76e27-401">Para atualizar todas as imagens nativas alteradas, ou cujas dependências foram alteradas, use a ação `update` sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="76e27-401">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>  
  
```  
ngen update  
```  
  
 <span data-ttu-id="76e27-402">A atualização de todas as imagens pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="76e27-402">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="76e27-403">É possível enfileirar as atualizações para execução pelo serviço de imagem nativa usando-se a opção `/queue`.</span><span class="sxs-lookup"><span data-stu-id="76e27-403">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="76e27-404">Para saber mais sobre a opção `/queue` e as prioridades de instalação, confira [Serviço de imagem nativa](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span><span class="sxs-lookup"><span data-stu-id="76e27-404">For more information on the `/queue` option and installation priorities, see [Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span></span>  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a><span data-ttu-id="76e27-405">Desinstalando Imagens</span><span class="sxs-lookup"><span data-stu-id="76e27-405">Uninstalling Images</span></span>  
 <span data-ttu-id="76e27-406">Como Ngen.exe mantém uma lista de dependências, os componentes compartilhados só são removidos quando todos os assemblies que dependam dele forem removidos.</span><span class="sxs-lookup"><span data-stu-id="76e27-406">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="76e27-407">Além de isso, um componente compartilhado não será removido se tiver sido instalado como raiz.</span><span class="sxs-lookup"><span data-stu-id="76e27-407">In addition, a shared component is not removed if it has been installed as a root.</span></span>  
  
 <span data-ttu-id="76e27-408">O seguinte comando desinstala todos os cenários da raiz `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="76e27-408">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp  
```  
  
 <span data-ttu-id="76e27-409">A ação `uninstall` pode ser usada para remover cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="76e27-409">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="76e27-410">O seguinte comando desinstala todos os cenários de depuração de `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="76e27-410">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  <span data-ttu-id="76e27-411">A desinstalação de cenários `/debug` não desinstalará um cenário que inclua `/profile` e `/debug.`</span><span class="sxs-lookup"><span data-stu-id="76e27-411">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>  
  
 <span data-ttu-id="76e27-412">O seguinte comando desinstala todos os cenários de uma versão específica de `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="76e27-412">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 <span data-ttu-id="76e27-413">Os seguintes comandos desinstalam todos os cenários de `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` ou apenas o cenário de depuração desse assembly:</span><span class="sxs-lookup"><span data-stu-id="76e27-413">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 <span data-ttu-id="76e27-414">Assim como acontece com a ação `install`, o fornecimento de uma extensão exige a execução de Ngen.exe no diretório que contém o assembly ou a especificação de um caminho completo.</span><span class="sxs-lookup"><span data-stu-id="76e27-414">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>  
  
 <span data-ttu-id="76e27-415">Para obter exemplos relacionados ao serviço de imagem nativa, confira [Serviço de imagem nativa](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span><span class="sxs-lookup"><span data-stu-id="76e27-415">For examples relating to the native image service, see [Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span></span>  
  
## <a name="native-image-task"></a><span data-ttu-id="76e27-416">Tarefa de imagem nativa</span><span class="sxs-lookup"><span data-stu-id="76e27-416">Native Image Task</span></span>  
 <span data-ttu-id="76e27-417">A tarefa de imagem nativa é uma tarefa do Windows que gera e mantém as imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-417">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="76e27-418">A tarefa de imagem nativa gera e recupera automaticamente as imagens nativas para cenários com suporte.</span><span class="sxs-lookup"><span data-stu-id="76e27-418">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="76e27-419">(Confira [Criar imagens nativas](http://msdn.microsoft.com/en-us/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Também permite que os instaladores usem o [Ngen.exe (Gerador de imagens nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) para criar e atualizar as imagens nativas em um tempo adiado.</span><span class="sxs-lookup"><span data-stu-id="76e27-419">(See [Creating Native Images](http://msdn.microsoft.com/en-us/2bc8b678-dd8d-4742-ad82-319e9bf52418).) It also enables installers to use [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>  
  
 <span data-ttu-id="76e27-420">A tarefa de imagem nativa é registrada uma vez para cada arquitetura de CPU com suporte em um computador, a fim de permitir a compilação para aplicativos direcionados a cada arquitetura:</span><span class="sxs-lookup"><span data-stu-id="76e27-420">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>  
  
|<span data-ttu-id="76e27-421">Nome da tarefa</span><span class="sxs-lookup"><span data-stu-id="76e27-421">Task name</span></span>|<span data-ttu-id="76e27-422">Computadores de 32 bits</span><span class="sxs-lookup"><span data-stu-id="76e27-422">32-bit computer</span></span>|<span data-ttu-id="76e27-423">Computadores de 64 bits</span><span class="sxs-lookup"><span data-stu-id="76e27-423">64-bit computer</span></span>|  
|---------------|----------------------|----------------------|  
|<span data-ttu-id="76e27-424">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="76e27-424">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="76e27-425">Sim</span><span class="sxs-lookup"><span data-stu-id="76e27-425">Yes</span></span>|<span data-ttu-id="76e27-426">Sim</span><span class="sxs-lookup"><span data-stu-id="76e27-426">Yes</span></span>|  
|<span data-ttu-id="76e27-427">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="76e27-427">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="76e27-428">Não</span><span class="sxs-lookup"><span data-stu-id="76e27-428">No</span></span>|<span data-ttu-id="76e27-429">Sim</span><span class="sxs-lookup"><span data-stu-id="76e27-429">Yes</span></span>|  
  
 <span data-ttu-id="76e27-430">A tarefa de imagem nativa está disponível no .NET Framework 4.5 e em versões posteriores ao ser executado no Windows 8 ou versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="76e27-430">The native image task is is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="76e27-431">Em versões anteriores do Windows, o .NET Framework usava o [Serviço de imagem nativa](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span><span class="sxs-lookup"><span data-stu-id="76e27-431">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309).</span></span>  
  
### <a name="task-lifetime"></a><span data-ttu-id="76e27-432">Tempo de vida da tarefa</span><span class="sxs-lookup"><span data-stu-id="76e27-432">Task Lifetime</span></span>  
 <span data-ttu-id="76e27-433">Em geral, o Agendador de Tarefas do Windows inicia a tarefa de imagem nativa toda noite, quando o computador está ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-433">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="76e27-434">A tarefa procura qualquer trabalho adiado que foi enfileirado pelos instaladores de aplicativo, quaisquer solicitações de atualização de imagem nativa adiadas e qualquer criação automática de imagem.</span><span class="sxs-lookup"><span data-stu-id="76e27-434">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="76e27-435">A tarefa conclui itens de trabalho pendentes e depois desliga.</span><span class="sxs-lookup"><span data-stu-id="76e27-435">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="76e27-436">Se o computador deixar o estado ocioso durante a execução da tarefa, a tarefa será interrompida.</span><span class="sxs-lookup"><span data-stu-id="76e27-436">If the computer stops being idle while the task is running, the task stops.</span></span>  
  
 <span data-ttu-id="76e27-437">Você também pode iniciar manualmente a tarefa de imagem nativa por meio da interface de usuário do Agendador de Tarefas ou por chamadas manuais ao NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-437">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="76e27-438">Se a tarefa for iniciada por um desses métodos, ele continuará em execução quando o computador não estiver mais ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-438">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="76e27-439">As imagens criadas manualmente com o NGen.exe recebem prioridade para permitir o comportamento previsível para os instaladores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="76e27-439">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>  
  
## <a name="native-image-service"></a><span data-ttu-id="76e27-440">Serviço de imagens nativas</span><span class="sxs-lookup"><span data-stu-id="76e27-440">Native Image Service</span></span>  
 <span data-ttu-id="76e27-441">O serviço de imagem nativa é um serviço do Windows que gera e mantém as imagens nativas.</span><span class="sxs-lookup"><span data-stu-id="76e27-441">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="76e27-442">Com o serviço de imagem nativa, o desenvolvedor pode adiar a instalação e a atualização de imagens nativas para quando o computador estiver ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-442">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>  
  
 <span data-ttu-id="76e27-443">Normalmente, o serviço de imagem nativa é iniciado pelo programa de instalação (instalador) para um aplicativo ou atualização.</span><span class="sxs-lookup"><span data-stu-id="76e27-443">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="76e27-444">Para ações de prioridade 3, o serviço é executado durante o período ocioso do computador.</span><span class="sxs-lookup"><span data-stu-id="76e27-444">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="76e27-445">O serviço salva seu estado e é capaz de continuar através de várias reinicializações, se for necessário.</span><span class="sxs-lookup"><span data-stu-id="76e27-445">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="76e27-446">É possível enfileirar várias compilações de imagem.</span><span class="sxs-lookup"><span data-stu-id="76e27-446">Multiple image compilations can be queued.</span></span>  
  
 <span data-ttu-id="76e27-447">O serviço também interage com o comando manual Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-447">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="76e27-448">Comandos manuais têm precedência sobre a atividade em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="76e27-448">Manual commands take precedence over background activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76e27-449">No Windows Vista, o nome exibido para o serviço de imagem nativa é "Microsoft.NET Framework NGEN v2.0.50727_X86" ou "Microsoft.NET Framework NGEN v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="76e27-449">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="76e27-450">Em todas as versões anteriores do Microsoft Windows, o nome é ".NET Runtime Optimization Service v2.0.50727_X86" ou ".NET Runtime Optimization Service v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="76e27-450">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>  
  
### <a name="launching-deferred-operations"></a><span data-ttu-id="76e27-451">Iniciar operações adiadas</span><span class="sxs-lookup"><span data-stu-id="76e27-451">Launching Deferred Operations</span></span>  
 <span data-ttu-id="76e27-452">Antes de iniciar uma instalação ou atualização, recomendamos pausar o serviço.</span><span class="sxs-lookup"><span data-stu-id="76e27-452">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="76e27-453">Isso garante que o serviço não seja executado enquanto o instalador está copiando os arquivos ou colocando os assemblies no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="76e27-453">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="76e27-454">Esta linha de comando do Ngen.exe pausa o serviço:</span><span class="sxs-lookup"><span data-stu-id="76e27-454">The following Ngen.exe command line pauses the service:</span></span>  
  
```  
ngen queue pause  
```  
  
 <span data-ttu-id="76e27-455">Quando todas as operações adiadas tiverem sido enfileiradas, o comando a seguir permitirá que o serviço continue:</span><span class="sxs-lookup"><span data-stu-id="76e27-455">When all deferred operations have been queued, the following command allows the service to resume:</span></span>  
  
```  
ngen queue continue  
```  
  
 <span data-ttu-id="76e27-456">Para adiar a geração de imagem nativa ao instalar um novo aplicativo ou ao atualizar um componente compartilhado, use a opção `/queue` com as ações `install` ou `update`.</span><span class="sxs-lookup"><span data-stu-id="76e27-456">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="76e27-457">Estas linhas de comando do Ngen.exe instalam uma imagem nativa para um componente compartilhado e executam uma atualização de todas as raízes que foram afetadas:</span><span class="sxs-lookup"><span data-stu-id="76e27-457">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 <span data-ttu-id="76e27-458">A ação `update` gera novamente todas as imagens nativas que foram invalidadas, não apenas as que usam `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="76e27-458">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>  
  
 <span data-ttu-id="76e27-459">Se o seu aplicativo for composto por várias raízes, você poderá controlar a prioridade das ações adiadas.</span><span class="sxs-lookup"><span data-stu-id="76e27-459">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="76e27-460">Os comandos a seguir enfileiram a instalação de três raízes.</span><span class="sxs-lookup"><span data-stu-id="76e27-460">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="76e27-461">O `Assembly1` é instalado primeiro, sem aguardar o tempo ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-461">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="76e27-462">O `Assembly2` também é instalado sem esperar o tempo ocioso, mas somente após a conclusão de todas as ações de prioridade 1.</span><span class="sxs-lookup"><span data-stu-id="76e27-462">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="76e27-463">O `Assembly3` é instalado quando o serviço detecta que o computador está ocioso.</span><span class="sxs-lookup"><span data-stu-id="76e27-463">`Assembly3` is installed when the service detects that the computer is idle.</span></span>  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 <span data-ttu-id="76e27-464">Você pode forçar a ocorrência assíncrona de ações enfileiradas usando a ação `executeQueuedItems`.</span><span class="sxs-lookup"><span data-stu-id="76e27-464">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="76e27-465">Se você fornecer a prioridade opcional, essa ação afetará somente as ações enfileiradas que têm prioridade igual ou menor.</span><span class="sxs-lookup"><span data-stu-id="76e27-465">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="76e27-466">A prioridade padrão é a 3, portanto, o seguinte comando Ngen.exe processa todas as ações em fila imediatamente e não retorna até que todas sejam concluídas:</span><span class="sxs-lookup"><span data-stu-id="76e27-466">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>  
  
```  
ngen executeQueuedItems  
```  
  
 <span data-ttu-id="76e27-467">Os comandos síncronos são executados pelo Ngen.exe e não usam o serviço de imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="76e27-467">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="76e27-468">Você pode executar ações usando Ngen.exe enquanto o serviço de imagem nativa estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="76e27-468">You can execute actions using Ngen.exe while the native image service is running.</span></span>  
  
### <a name="service-shutdown"></a><span data-ttu-id="76e27-469">Desligamento do serviço</span><span class="sxs-lookup"><span data-stu-id="76e27-469">Service Shutdown</span></span>  
 <span data-ttu-id="76e27-470">Depois de iniciado pela execução de um comando Ngen.exe que inclui a opção `/queue`, o serviço é executado em segundo plano até que todas as ações sejam concluídas.</span><span class="sxs-lookup"><span data-stu-id="76e27-470">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="76e27-471">O serviço salva seu estado para que ele possa continuar por várias reinicializações, se for necessário.</span><span class="sxs-lookup"><span data-stu-id="76e27-471">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="76e27-472">Quando o serviço detecta que há não mais ações na fila, ele redefine seu status para que não reinicie na próxima vez que o computador for inicializado e, depois, ele se desliga.</span><span class="sxs-lookup"><span data-stu-id="76e27-472">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>  
  
### <a name="service-interaction-with-clients"></a><span data-ttu-id="76e27-473">Interação do serviço com clientes</span><span class="sxs-lookup"><span data-stu-id="76e27-473">Service Interaction with Clients</span></span>  
 <span data-ttu-id="76e27-474">No .NET Framework versão 2.0, a única interação com o serviço de imagem nativa ocorre por meio da ferramenta de linha de comando Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="76e27-474">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="76e27-475">Use a ferramenta de linha de comando em scripts de instalação para enfileirar ações para o serviço de imagem nativa e para interagir com o serviço.</span><span class="sxs-lookup"><span data-stu-id="76e27-475">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e27-476">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76e27-476">See Also</span></span>  
 <span data-ttu-id="76e27-477">[Serviço de imagens nativas](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309) </span><span class="sxs-lookup"><span data-stu-id="76e27-477">[Native Image Service](http://msdn.microsoft.com/en-us/b15e0e32-59cb-4ae4-967c-6c9527781309) </span></span>  
 <span data-ttu-id="76e27-478">[Tarefa de imagem nativa](http://msdn.microsoft.com/en-us/9b1f7590-4e0d-4737-90ef-eaf696932afb) </span><span class="sxs-lookup"><span data-stu-id="76e27-478">[Native Image Task](http://msdn.microsoft.com/en-us/9b1f7590-4e0d-4737-90ef-eaf696932afb) </span></span>  
 <span data-ttu-id="76e27-479">[Ferramentas](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="76e27-479">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 <span data-ttu-id="76e27-480">[Processo de execução gerenciada](../../../docs/standard/managed-execution-process.md) </span><span class="sxs-lookup"><span data-stu-id="76e27-480">[Managed Execution Process](../../../docs/standard/managed-execution-process.md) </span></span>  
 <span data-ttu-id="76e27-481">[Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="76e27-481">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="76e27-482">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="76e27-482">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

