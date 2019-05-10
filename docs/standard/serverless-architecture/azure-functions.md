---
title: Funções do Azure – aplicativos sem servidor
description: O Azure functions fornece funcionalidades sem servidor em vários idiomas (c#, JavaScript, Java) e plataformas para fornecer controlada por evento instantâneas dimensionar o código.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754227"
---
# <a name="azure-functions"></a><span data-ttu-id="c8e3c-103">Verificação de</span><span class="sxs-lookup"><span data-stu-id="c8e3c-103">Azure Functions</span></span>

<span data-ttu-id="c8e3c-104">O Azure functions fornece uma experiência de computação sem servidor.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="c8e3c-105">Uma função é invocada por um *disparador* (como acesso a um ponto de extremidade HTTP ou um temporizador) e executa um bloco de código ou a lógica comercial.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="c8e3c-106">Funções também suporte especializado *associações* que se conectam a recursos como armazenamento e filas.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logotipo do Azure functions](./media/azure-functions-logo.png)

<span data-ttu-id="c8e3c-108">Há duas versões do framework do Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="c8e3c-109">A versão herdada dá suporte ao .NET Framework completo e o novo tempo de execução dá suporte a aplicativos do .NET Core de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="c8e3c-110">Idiomas adicionais além do C# , como JavaScript, F#, e Java são suportados.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="c8e3c-111">As funções criadas no portal do fornecem uma sintaxe de script avançada.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="c8e3c-112">Funções criadas como projetos autônomos podem ser implantadas com os recursos e suporte de plataforma completo.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="c8e3c-113">Para obter mais informações, consulte [documentação do Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="c8e3c-114">Funções v1 e v2</span><span class="sxs-lookup"><span data-stu-id="c8e3c-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="c8e3c-115">Há duas versões do tempo de execução do Azure Functions: 1.x e 2.x.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="c8e3c-116">Versão 1.x já está disponível (GA).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="c8e3c-117">Ele dá suporte ao desenvolvimento de .NET do portal ou as máquinas do Windows e usa o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="c8e3c-118">1.x dá suporte ao C#, JavaScript, e F#, com o suporte experimental para Python, PHP, TypeScript, Batch, Bash e PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="c8e3c-119">[Versão 2.x também está disponível agora](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="c8e3c-120">Ele aproveita o .NET Core e dá suporte ao desenvolvimento de plataforma cruzada em máquinas Linux, macOS e Windows.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="c8e3c-121">2.x adiciona suporte de primeira classe para Java, mas não ainda suporta diretamente qualquer uma das linguagens experimentais.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="c8e3c-122">Versão 2.x usa um novo modelo de extensibilidade de associação que permite que extensões de terceiros para a plataforma, o controle de versão independente de associações, e uma mais simples de ambiente de execução.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="c8e3c-123">**Há um problema conhecido no 1.x com [suporte de redirecionamento de associação](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="c8e3c-124">O problema é específico para o desenvolvimento de .NET.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="c8e3c-125">Projetos com dependências em bibliotecas que são uma versão diferente do que as bibliotecas incluídas no tempo de execução são afetados.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="c8e3c-126">A equipe de funções se comprometeu a progredindo concretas sobre o problema.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="c8e3c-127">A equipe abordará os redirecionamentos de associação no 2.x antes que ele fique em disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="c8e3c-128">A declaração oficial da equipe com correções sugeridas e soluções alternativas está disponível aqui: [Resolução de assembly no Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="c8e3c-129">Para obter mais informações, consulte [comparar 1.x e 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="c8e3c-130">Suporte de linguagem de programação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-130">Programming language support</span></span>

<span data-ttu-id="c8e3c-131">Os idiomas a seguir têm suporte em geral GA (disponibilidade), visualizar, ou experimental.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="c8e3c-132">Idioma</span><span class="sxs-lookup"><span data-stu-id="c8e3c-132">Language</span></span>      |<span data-ttu-id="c8e3c-133">1.x</span><span class="sxs-lookup"><span data-stu-id="c8e3c-133">1.x</span></span>         |<span data-ttu-id="c8e3c-134">2.x</span><span class="sxs-lookup"><span data-stu-id="c8e3c-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="c8e3c-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-135">**C#**</span></span>        |<span data-ttu-id="c8e3c-136">GA</span><span class="sxs-lookup"><span data-stu-id="c8e3c-136">GA</span></span>          |<span data-ttu-id="c8e3c-137">Visualizar</span><span class="sxs-lookup"><span data-stu-id="c8e3c-137">Preview</span></span>  |
|<span data-ttu-id="c8e3c-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-138">**JavaScript**</span></span>|<span data-ttu-id="c8e3c-139">GA</span><span class="sxs-lookup"><span data-stu-id="c8e3c-139">GA</span></span>          |<span data-ttu-id="c8e3c-140">Visualizar</span><span class="sxs-lookup"><span data-stu-id="c8e3c-140">Preview</span></span>  |
|<span data-ttu-id="c8e3c-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-141">**F#**</span></span>        |<span data-ttu-id="c8e3c-142">GA</span><span class="sxs-lookup"><span data-stu-id="c8e3c-142">GA</span></span>          |         |
|<span data-ttu-id="c8e3c-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-143">**Java**</span></span>      |            |<span data-ttu-id="c8e3c-144">Visualizar</span><span class="sxs-lookup"><span data-stu-id="c8e3c-144">Preview</span></span>  |
|<span data-ttu-id="c8e3c-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-145">**Python**</span></span>    |<span data-ttu-id="c8e3c-146">Habilitação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-146">Experimental</span></span>|         |
|<span data-ttu-id="c8e3c-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-147">**PHP**</span></span>       |<span data-ttu-id="c8e3c-148">Habilitação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-148">Experimental</span></span>|         |
|<span data-ttu-id="c8e3c-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-149">**TypeScript**</span></span>|<span data-ttu-id="c8e3c-150">Habilitação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-150">Experimental</span></span>|         |
|<span data-ttu-id="c8e3c-151">**Lote**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-151">**Batch**</span></span>     |<span data-ttu-id="c8e3c-152">Habilitação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-152">Experimental</span></span>|         |
|<span data-ttu-id="c8e3c-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-153">**Bash**</span></span>      |<span data-ttu-id="c8e3c-154">Habilitação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-154">Experimental</span></span>|         |
|<span data-ttu-id="c8e3c-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="c8e3c-155">**PowerShell**</span></span>|<span data-ttu-id="c8e3c-156">Habilitação</span><span class="sxs-lookup"><span data-stu-id="c8e3c-156">Experimental</span></span>|         |

<span data-ttu-id="c8e3c-157">Para obter mais informações, consulte [idiomas com suporte](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="c8e3c-158">Planos de serviço de aplicativo</span><span class="sxs-lookup"><span data-stu-id="c8e3c-158">App service plans</span></span>

<span data-ttu-id="c8e3c-159">Funções são apoiadas por um *plano do serviço de aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="c8e3c-160">O plano define os recursos usados pelo aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="c8e3c-161">Você pode atribuir os planos para uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um tipo de preço.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="c8e3c-162">Para uma verdadeira abordagem sem servidor, aplicativos de funções podem usar o **consumo** plano.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="c8e3c-163">O plano de consumo escala automaticamente com base na carga de back-end.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="c8e3c-164">Para obter mais informações, consulte [planos de serviço de aplicativo](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="c8e3c-165">Criar sua primeira função</span><span class="sxs-lookup"><span data-stu-id="c8e3c-165">Create your first function</span></span>

<span data-ttu-id="c8e3c-166">Há três maneiras comuns que você pode criar aplicativos de funções.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-166">There are three common ways you can create function apps.</span></span>

* <span data-ttu-id="c8e3c-167">Funções de script no portal.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-167">Script functions in the portal.</span></span>
* <span data-ttu-id="c8e3c-168">Crie os recursos necessários usando a Interface de linha de comando (CLI) do Azure.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-168">Create the necessary resources using the Azure Command Line Interface (CLI).</span></span>
* <span data-ttu-id="c8e3c-169">Crie funções localmente usando seu IDE favorito e publicá-los para o Azure.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="c8e3c-170">Para obter mais informações sobre como criar uma função de script no portal, consulte [criar sua primeira função no portal do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="c8e3c-171">Para compilar a partir da CLI do Azure, consulte [criar sua primeira função usando a CLI do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="c8e3c-172">Para criar uma função do Visual Studio, consulte [criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="c8e3c-173">Entender os gatilhos e associações</span><span class="sxs-lookup"><span data-stu-id="c8e3c-173">Understand triggers and bindings</span></span>

<span data-ttu-id="c8e3c-174">As funções são chamadas por um *disparador* e pode ter exatamente um.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="c8e3c-175">Além de chamar a função, determinados disparadores também servem como associações.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="c8e3c-176">Você também pode definir várias associações, além de gatilho.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="c8e3c-177">*Associações* fornecem uma maneira declarativa para se conectar a dados ao seu código.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="c8e3c-178">Eles podem ser passados em (entrada) ou recebem dados (saída).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="c8e3c-179">Gatilhos e associações tornam fácil trabalhar com funções.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="c8e3c-180">Associações de remover a sobrecarga de criar manualmente banco de dados ou arquivo de conexões de sistema.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="c8e3c-181">Todas as informações necessárias para as ligações estão contidas em um especial *Functions* de arquivos para scripts ou declarados com atributos no código.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="c8e3c-182">Alguns gatilhos comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-182">Some common triggers include:</span></span>

* <span data-ttu-id="c8e3c-183">Armazenamento de BLOBs: chama sua função quando um arquivo ou pasta for carregada ou alterada no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
* <span data-ttu-id="c8e3c-184">HTTP: chama sua função como uma API REST.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-184">HTTP: invoke your function like a REST API.</span></span>
* <span data-ttu-id="c8e3c-185">Fila: chama sua função quando existem itens em uma fila.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-185">Queue: invoke your function when items exist in a queue.</span></span>
* <span data-ttu-id="c8e3c-186">Temporizador: chama sua função em um ritmo regular.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="c8e3c-187">Exemplos de associações:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-187">Examples of bindings include:</span></span>

* <span data-ttu-id="c8e3c-188">CosmosDB: facilmente se conecte ao banco de dados para carregar ou salvar arquivos.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-188">CosmosDB: easily connect to the database to load or save files.</span></span>
* <span data-ttu-id="c8e3c-189">O armazenamento de tabela: trabalhar com o armazenamento de chave/valor de seu aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-189">Table Storage: work with key/value storage from your function app.</span></span>
* <span data-ttu-id="c8e3c-190">O armazenamento de filas: facilmente recuperar itens de uma fila ou colocar novos itens na fila.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="c8e3c-191">O exemplo a seguir *Functions* arquivo define um gatilho e uma associação:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="c8e3c-192">Neste exemplo, a função é disparada por uma alteração no armazenamento de BLOBs no `images` contêiner.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="c8e3c-193">As informações para o arquivo são passadas, portanto, o gatilho também atua como uma associação.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="c8e3c-194">Outra associação existe para colocar as informações em uma fila denominada `images`.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="c8e3c-195">Aqui está o script do c# para a função:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="c8e3c-196">O exemplo é uma função simples que usa o nome do arquivo que foi modificada ou carregados no armazenamento de BLOBs e coloca-o em uma fila para processamento posterior.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="c8e3c-197">Para obter uma lista completa dos gatilhos e associações, consulte [conceitos de associações e gatilhos do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="c8e3c-198">Proxies</span><span class="sxs-lookup"><span data-stu-id="c8e3c-198">Proxies</span></span>

<span data-ttu-id="c8e3c-199">Proxies fornecem a funcionalidade de redirecionamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="c8e3c-200">Proxies expõem um ponto de extremidade e mapeiam esse ponto de extremidade para outro recurso.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="c8e3c-201">Com proxies, você pode:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-201">With proxies, you can:</span></span>

* <span data-ttu-id="c8e3c-202">Redirecionar uma solicitação de entrada para outro ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-202">Reroute an incoming request to another endpoint.</span></span>
* <span data-ttu-id="c8e3c-203">Modificar a solicitação de entrada antes de ser passado ao longo.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-203">Modify the incoming request before it's passed along.</span></span>
* <span data-ttu-id="c8e3c-204">Modificar ou fornecer uma resposta.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-204">Modify or provide a response.</span></span>

<span data-ttu-id="c8e3c-205">Os proxies são usados para cenários como:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-205">Proxies are used for scenarios such as:</span></span>

* <span data-ttu-id="c8e3c-206">Simplificando, encurtando ou alterar a URL.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-206">Simplifying, shortening, or changing the URL.</span></span>
* <span data-ttu-id="c8e3c-207">Fornecendo um prefixo de API consistente para vários serviços de back-end.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-207">Providing a consistent API prefix to multiple back-end services.</span></span>
* <span data-ttu-id="c8e3c-208">Simulação de uma resposta a um ponto de extremidade que está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-208">Mocking a response to an endpoint being developed.</span></span>
* <span data-ttu-id="c8e3c-209">Fornecendo uma resposta de estática para um ponto de extremidade conhecido.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-209">Providing a static response to a well-known endpoint.</span></span>
* <span data-ttu-id="c8e3c-210">Mantendo um ponto de extremidade de API consistente enquanto o back-end é movido ou migrado.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="c8e3c-211">Os proxies são armazenados como definições de JSON.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="c8e3c-212">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="c8e3c-213">O `Domain Redirect` proxy usa uma rota reduzida e mapeia-os para o recurso de função mais tempo.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="c8e3c-214">A transformação é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="c8e3c-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="c8e3c-215">O `Root` proxy usa qualquer coisa enviadas para a URL da raiz (`https://--shorturl--/`) e o redireciona para o site de documentação.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="c8e3c-216">Um exemplo do uso de proxies é mostrado no vídeo [Azure: Traga o seu aplicativo para a nuvem com o Azure Functions sem servidor](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="c8e3c-217">Em tempo real, um aplicativo ASP.NET Core em execução no SQL Server local é migrado para a nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="c8e3c-218">Os proxies são usados para ajudar a refatorar um projeto de API da Web tradicional para usar funções.</span><span class="sxs-lookup"><span data-stu-id="c8e3c-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="c8e3c-219">Para obter mais informações sobre Proxies, consulte [trabalhar com Proxies do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="c8e3c-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c8e3c-220">[Anterior](azure-serverless-platform.md)
>[Próximo](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="c8e3c-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
