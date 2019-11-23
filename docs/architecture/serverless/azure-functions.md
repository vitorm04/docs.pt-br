---
title: Aplicativos Azure Functions-sem servidor
description: O Azure Functions fornece recursos sem servidor em váriosC#idiomas (, JavaScript, Java) e plataformas para fornecer código de escala instantânea controlado por eventos.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5e8187b3752a0f0d0bcf8e15f2ce440dc5a64e45
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522874"
---
# <a name="azure-functions"></a><span data-ttu-id="ba308-103">Verificação de</span><span class="sxs-lookup"><span data-stu-id="ba308-103">Azure Functions</span></span>

<span data-ttu-id="ba308-104">O Azure Functions fornece uma experiência de computação sem servidor.</span><span class="sxs-lookup"><span data-stu-id="ba308-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="ba308-105">Uma função é invocada por um *gatilho* (como o acesso a um ponto de extremidade http ou um temporizador) e executa um bloco de código ou lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="ba308-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="ba308-106">As funções também dão suporte a *associações* especializadas que se conectam a recursos como armazenamento e filas.</span><span class="sxs-lookup"><span data-stu-id="ba308-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logotipo do Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="ba308-108">Há duas versões do Azure Functions Framework.</span><span class="sxs-lookup"><span data-stu-id="ba308-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="ba308-109">A versão herdada dá suporte ao .NET Framework completo e o novo tempo de execução dá suporte a aplicativos .NET Core de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="ba308-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="ba308-110">Há suporte para C# idiomas adicionais, além F#de JavaScript, e Java.</span><span class="sxs-lookup"><span data-stu-id="ba308-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="ba308-111">As funções criadas no portal fornecem uma sintaxe de script avançada.</span><span class="sxs-lookup"><span data-stu-id="ba308-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="ba308-112">As funções criadas como projetos autônomos podem ser implantadas com recursos e suporte completos à plataforma.</span><span class="sxs-lookup"><span data-stu-id="ba308-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="ba308-113">Para obter mais informações, consulte a [documentação do Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="ba308-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="ba308-114">Funções V1 versus V2</span><span class="sxs-lookup"><span data-stu-id="ba308-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="ba308-115">Há duas versões do tempo de execução de Azure Functions: 1. x e 2. x.</span><span class="sxs-lookup"><span data-stu-id="ba308-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="ba308-116">A versão 1. x está disponível para o público geral (GA).</span><span class="sxs-lookup"><span data-stu-id="ba308-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="ba308-117">Ele dá suporte ao desenvolvimento .NET do portal ou de máquinas Windows e usa o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba308-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="ba308-118">1. x dá C#suporte a, JavaScript F#e, com suporte experimental para Python, PHP, TypeScript, lote, bash e PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ba308-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="ba308-119">A [versão 2. x também está geralmente disponível agora](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="ba308-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="ba308-120">Ele aproveita o .NET Core e dá suporte ao desenvolvimento de plataforma cruzada em computadores Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="ba308-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="ba308-121">2. x adiciona o suporte de primeira classe para Java, mas ainda não dá suporte diretamente a qualquer uma das linguagens experimentais.</span><span class="sxs-lookup"><span data-stu-id="ba308-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="ba308-122">A versão 2. x usa um novo modelo de extensibilidade de associação que permite extensões de terceiros para a plataforma, controle de versão independente de associações e um ambiente de execução mais simplificado.</span><span class="sxs-lookup"><span data-stu-id="ba308-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="ba308-123">**Há um problema conhecido em 1. x com [suporte para redirecionamento de associação](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="ba308-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="ba308-124">O problema é específico do desenvolvimento do .NET.</span><span class="sxs-lookup"><span data-stu-id="ba308-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="ba308-125">Os projetos com dependências em bibliotecas que são uma versão diferente das bibliotecas incluídas no tempo de execução são afetados.</span><span class="sxs-lookup"><span data-stu-id="ba308-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="ba308-126">A equipe de funções se comprometeu a fazer o progresso concreto do problema.</span><span class="sxs-lookup"><span data-stu-id="ba308-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="ba308-127">A equipe abordará redirecionamentos de associação em 2. x antes de entrar em disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="ba308-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="ba308-128">A declaração de equipe oficial com correções e soluções alternativas sugeridas está disponível aqui: [resolução de assembly em Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="ba308-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="ba308-129">Para obter mais informações, consulte [comparar 1. x e 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="ba308-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="ba308-130">Suporte à linguagem de programação</span><span class="sxs-lookup"><span data-stu-id="ba308-130">Programming language support</span></span>

<span data-ttu-id="ba308-131">Os idiomas a seguir têm suporte em disponibilidade geral (GA), visualização ou experimental.</span><span class="sxs-lookup"><span data-stu-id="ba308-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="ba308-132">Linguagem</span><span class="sxs-lookup"><span data-stu-id="ba308-132">Language</span></span>      |<span data-ttu-id="ba308-133">1.x</span><span class="sxs-lookup"><span data-stu-id="ba308-133">1.x</span></span>         |<span data-ttu-id="ba308-134">2.x</span><span class="sxs-lookup"><span data-stu-id="ba308-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="ba308-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="ba308-135">**C#**</span></span>        |<span data-ttu-id="ba308-136">3º</span><span class="sxs-lookup"><span data-stu-id="ba308-136">GA</span></span>          |<span data-ttu-id="ba308-137">{1&gt;Preview&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ba308-137">Preview</span></span>  |
|<span data-ttu-id="ba308-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="ba308-138">**JavaScript**</span></span>|<span data-ttu-id="ba308-139">3º</span><span class="sxs-lookup"><span data-stu-id="ba308-139">GA</span></span>          |<span data-ttu-id="ba308-140">{1&gt;Preview&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ba308-140">Preview</span></span>  |
|<span data-ttu-id="ba308-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="ba308-141">**F#**</span></span>        |<span data-ttu-id="ba308-142">3º</span><span class="sxs-lookup"><span data-stu-id="ba308-142">GA</span></span>          |         |
|<span data-ttu-id="ba308-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="ba308-143">**Java**</span></span>      |            |<span data-ttu-id="ba308-144">{1&gt;Preview&lt;1}</span><span class="sxs-lookup"><span data-stu-id="ba308-144">Preview</span></span>  |
|<span data-ttu-id="ba308-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="ba308-145">**Python**</span></span>    |<span data-ttu-id="ba308-146">Habilitação</span><span class="sxs-lookup"><span data-stu-id="ba308-146">Experimental</span></span>|         |
|<span data-ttu-id="ba308-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="ba308-147">**PHP**</span></span>       |<span data-ttu-id="ba308-148">Habilitação</span><span class="sxs-lookup"><span data-stu-id="ba308-148">Experimental</span></span>|         |
|<span data-ttu-id="ba308-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="ba308-149">**TypeScript**</span></span>|<span data-ttu-id="ba308-150">Habilitação</span><span class="sxs-lookup"><span data-stu-id="ba308-150">Experimental</span></span>|         |
|<span data-ttu-id="ba308-151">**Lote**</span><span class="sxs-lookup"><span data-stu-id="ba308-151">**Batch**</span></span>     |<span data-ttu-id="ba308-152">Habilitação</span><span class="sxs-lookup"><span data-stu-id="ba308-152">Experimental</span></span>|         |
|<span data-ttu-id="ba308-153">**Raso**</span><span class="sxs-lookup"><span data-stu-id="ba308-153">**Bash**</span></span>      |<span data-ttu-id="ba308-154">Habilitação</span><span class="sxs-lookup"><span data-stu-id="ba308-154">Experimental</span></span>|         |
|<span data-ttu-id="ba308-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="ba308-155">**PowerShell**</span></span>|<span data-ttu-id="ba308-156">Habilitação</span><span class="sxs-lookup"><span data-stu-id="ba308-156">Experimental</span></span>|         |

<span data-ttu-id="ba308-157">Para obter mais informações, consulte [idiomas com suporte](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="ba308-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="ba308-158">Planos do serviço de aplicativo</span><span class="sxs-lookup"><span data-stu-id="ba308-158">App service plans</span></span>

<span data-ttu-id="ba308-159">As funções são apoiadas por um *plano do serviço de aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="ba308-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="ba308-160">O plano define os recursos usados pelo aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="ba308-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="ba308-161">Você pode atribuir planos a uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um tipo de preço.</span><span class="sxs-lookup"><span data-stu-id="ba308-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="ba308-162">Para uma abordagem verdadeira sem servidor, os aplicativos de função podem usar o plano de **consumo** .</span><span class="sxs-lookup"><span data-stu-id="ba308-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="ba308-163">O plano de consumo dimensionará o back-end automaticamente com base na carga.</span><span class="sxs-lookup"><span data-stu-id="ba308-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="ba308-164">Para obter mais informações, consulte [planos do serviço de aplicativo](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="ba308-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="ba308-165">Criar sua primeira função</span><span class="sxs-lookup"><span data-stu-id="ba308-165">Create your first function</span></span>

<span data-ttu-id="ba308-166">Há três maneiras comuns de criar aplicativos de funções.</span><span class="sxs-lookup"><span data-stu-id="ba308-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="ba308-167">Funções de script no Portal.</span><span class="sxs-lookup"><span data-stu-id="ba308-167">Script functions in the portal.</span></span>
- <span data-ttu-id="ba308-168">Crie os recursos necessários usando a CLI (interface de linha de comando) do Azure.</span><span class="sxs-lookup"><span data-stu-id="ba308-168">Create the necessary resources using the Azure Command Line Interface (CLI).</span></span>
- <span data-ttu-id="ba308-169">Crie funções localmente usando seu IDE favorito e publique-as no Azure.</span><span class="sxs-lookup"><span data-stu-id="ba308-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="ba308-170">Para obter mais informações sobre como criar uma função com script no portal, consulte [criar sua primeira função no portal do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="ba308-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="ba308-171">Para criar a partir do CLI do Azure, consulte [criar sua primeira função usando o CLI do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="ba308-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="ba308-172">Para criar uma função do Visual Studio, consulte [criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ba308-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="ba308-173">Entender gatilhos e associações</span><span class="sxs-lookup"><span data-stu-id="ba308-173">Understand triggers and bindings</span></span>

<span data-ttu-id="ba308-174">As funções são invocadas por um *gatilho* e podem ter exatamente uma.</span><span class="sxs-lookup"><span data-stu-id="ba308-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="ba308-175">Além de invocar a função, determinados gatilhos também servem como associações.</span><span class="sxs-lookup"><span data-stu-id="ba308-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="ba308-176">Você também pode definir várias associações além do gatilho.</span><span class="sxs-lookup"><span data-stu-id="ba308-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="ba308-177">As *associações* fornecem uma maneira declarativa de conectar dados ao seu código.</span><span class="sxs-lookup"><span data-stu-id="ba308-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="ba308-178">Eles podem ser passados (entrada) ou receber dados (saída).</span><span class="sxs-lookup"><span data-stu-id="ba308-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="ba308-179">Os gatilhos e as associações facilitam o trabalho com as funções.</span><span class="sxs-lookup"><span data-stu-id="ba308-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="ba308-180">As associações removem a sobrecarga de criar manualmente as conexões do banco de dados ou do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ba308-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="ba308-181">Todas as informações necessárias para as associações estão contidas em um arquivo *functions. JSON* especial para scripts ou declarados com atributos no código.</span><span class="sxs-lookup"><span data-stu-id="ba308-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="ba308-182">Alguns gatilhos comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="ba308-182">Some common triggers include:</span></span>

- <span data-ttu-id="ba308-183">Armazenamento de BLOBs: invoque sua função quando um arquivo ou pasta for carregado ou alterado no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="ba308-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="ba308-184">HTTP: invoque sua função como uma API REST.</span><span class="sxs-lookup"><span data-stu-id="ba308-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="ba308-185">Fila: invoque sua função quando houver itens em uma fila.</span><span class="sxs-lookup"><span data-stu-id="ba308-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="ba308-186">Temporizador: invocar sua função em uma cadência regular.</span><span class="sxs-lookup"><span data-stu-id="ba308-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="ba308-187">Exemplos de associações incluem:</span><span class="sxs-lookup"><span data-stu-id="ba308-187">Examples of bindings include:</span></span>

- <span data-ttu-id="ba308-188">CosmosDB: Conecte-se facilmente ao banco de dados para carregar ou salvar arquivos.</span><span class="sxs-lookup"><span data-stu-id="ba308-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="ba308-189">Armazenamento de tabelas: trabalhe com o armazenamento de chave/valor do seu aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="ba308-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="ba308-190">Armazenamento de filas: recuperar facilmente itens de uma fila ou colocar novos itens na fila.</span><span class="sxs-lookup"><span data-stu-id="ba308-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="ba308-191">O arquivo *functions. JSON* de exemplo a seguir define um gatilho e uma associação:</span><span class="sxs-lookup"><span data-stu-id="ba308-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="ba308-192">Neste exemplo, a função é disparada por uma alteração no armazenamento de BLOBs no contêiner de `images`.</span><span class="sxs-lookup"><span data-stu-id="ba308-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="ba308-193">As informações para o arquivo são passadas para que o gatilho também atue como uma associação.</span><span class="sxs-lookup"><span data-stu-id="ba308-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="ba308-194">Existe outra associação para colocar informações em uma fila chamada `images`.</span><span class="sxs-lookup"><span data-stu-id="ba308-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="ba308-195">Este é o C# script para a função:</span><span class="sxs-lookup"><span data-stu-id="ba308-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="ba308-196">O exemplo é uma função simples que usa o nome do arquivo que foi modificado ou carregado no armazenamento de BLOBs e o coloca em uma fila para processamento posterior.</span><span class="sxs-lookup"><span data-stu-id="ba308-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="ba308-197">Para obter uma lista completa de gatilhos e associações, consulte [Azure Functions os conceitos de gatilhos e associações](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="ba308-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="ba308-198">Proxies</span><span class="sxs-lookup"><span data-stu-id="ba308-198">Proxies</span></span>

<span data-ttu-id="ba308-199">Os proxies fornecem funcionalidade de redirecionamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ba308-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="ba308-200">Os proxies expõem um ponto de extremidade e mapeiam esse ponto de extremidade para outro recurso.</span><span class="sxs-lookup"><span data-stu-id="ba308-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="ba308-201">Com proxies, você pode:</span><span class="sxs-lookup"><span data-stu-id="ba308-201">With proxies, you can:</span></span>

- <span data-ttu-id="ba308-202">Redirecionar uma solicitação de entrada para outro ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="ba308-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="ba308-203">Modifique a solicitação de entrada antes de ela ser passada.</span><span class="sxs-lookup"><span data-stu-id="ba308-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="ba308-204">Modifique ou forneça uma resposta.</span><span class="sxs-lookup"><span data-stu-id="ba308-204">Modify or provide a response.</span></span>

<span data-ttu-id="ba308-205">Os proxies são usados para cenários como:</span><span class="sxs-lookup"><span data-stu-id="ba308-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="ba308-206">Simplificando, reduzindo ou alterando a URL.</span><span class="sxs-lookup"><span data-stu-id="ba308-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="ba308-207">Fornecer um prefixo de API consistente para vários serviços de back-end.</span><span class="sxs-lookup"><span data-stu-id="ba308-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="ba308-208">Simulação de uma resposta a um ponto de extremidade que está sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="ba308-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="ba308-209">Fornecer uma resposta estática para um ponto de extremidade bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="ba308-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="ba308-210">Manter um ponto de extremidade de API consistente enquanto o back-end é movido ou migrado.</span><span class="sxs-lookup"><span data-stu-id="ba308-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="ba308-211">Os proxies são armazenados como definições de JSON.</span><span class="sxs-lookup"><span data-stu-id="ba308-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="ba308-212">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="ba308-212">Here is an example:</span></span>

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

<span data-ttu-id="ba308-213">O proxy de `Domain Redirect` usa uma rota reduzida e a mapeia para o recurso de função mais longo.</span><span class="sxs-lookup"><span data-stu-id="ba308-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="ba308-214">A transformação é semelhante a:</span><span class="sxs-lookup"><span data-stu-id="ba308-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="ba308-215">O proxy de `Root` faz algo enviado para a URL raiz (`https://--shorturl--/`) e o redireciona para o site de documentação.</span><span class="sxs-lookup"><span data-stu-id="ba308-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="ba308-216">Um exemplo de uso de proxies é mostrado no vídeo [Azure: Traga seu aplicativo para a nuvem com Azure Functions sem servidor](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="ba308-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="ba308-217">Em tempo real, um aplicativo ASP.NET Core em execução no SQL Server local é migrado para a nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="ba308-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="ba308-218">Os proxies são usados para ajudar a refatorar um projeto de API Web tradicional para usar funções.</span><span class="sxs-lookup"><span data-stu-id="ba308-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="ba308-219">Para obter mais informações sobre proxies, consulte [trabalhar com proxies do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="ba308-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ba308-220">[Anterior](azure-serverless-platform.md)
>[Próximo](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="ba308-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
