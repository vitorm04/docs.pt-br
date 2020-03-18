---
title: Funções do Azure - Aplicativos sem servidor
description: As funções do Azure fornecem recursos sem servidor em vários idiomas (C#, JavaScript, Java) e plataformas para fornecer código de escala instantânea orientado a eventos.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401609"
---
# <a name="azure-functions"></a><span data-ttu-id="2b5d2-103">Funções do Azure</span><span class="sxs-lookup"><span data-stu-id="2b5d2-103">Azure Functions</span></span>

<span data-ttu-id="2b5d2-104">As funções do Azure proporcionam uma experiência de computação sem servidor.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="2b5d2-105">Uma função é invocada por um *gatilho* (como acesso a um ponto final HTTP ou um temporizador) e executa um bloco de código ou lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="2b5d2-106">As funções também suportam *vinculações especializadas* que se conectam a recursos como armazenamento e filas.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logotipo de funções do Azure](./media/azure-functions-logo.png)

<span data-ttu-id="2b5d2-108">Existem duas versões da estrutura de Funções do Azure.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="2b5d2-109">A versão herdada suporta o Framework .NET completo e o novo tempo de execução suporta aplicativos .NET Core multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="2b5d2-110">Linguagens adicionais além de C# como JavaScript, F#e Java são suportadas.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="2b5d2-111">As funções criadas no portal fornecem uma rica sintaxe de scripts.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="2b5d2-112">Funções criadas como projetos autônomos podem ser implantadas com suporte e recursos completos da plataforma.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="2b5d2-113">Para obter mais informações, consulte [a documentação funções do Azure](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="2b5d2-114">Funções v1 vs. v2</span><span class="sxs-lookup"><span data-stu-id="2b5d2-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="2b5d2-115">Existem duas versões do tempo de execução das funções do Azure: 1.x e 2.x.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="2b5d2-116">A versão 1.x está geralmente disponível (GA).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="2b5d2-117">Ele suporta o desenvolvimento .NET a partir do portal ou máquinas Windows e usa o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="2b5d2-118">O 1.x suporta C#, JavaScript e F#, com suporte experimental para Python, PHP, TypeScript, Batch, Bash e PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="2b5d2-119">[A versão 2.x também está geralmente disponível agora](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="2b5d2-120">Ele aproveita o .NET Core e suporta o desenvolvimento entre plataformas em máquinas Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="2b5d2-121">2.x adiciona suporte de primeira classe para Java, mas ainda não suporta diretamente nenhuma das linguagens experimentais.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="2b5d2-122">A versão 2.x usa um novo modelo de extensibilidade de vinculação que permite extensões de terceiros à plataforma, versão independente de vinculações e um ambiente de execução mais simplificado.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="2b5d2-123">**Há um problema conhecido em 1.x com [suporte de redirecionamento de vinculação](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="2b5d2-124">O problema é específico para o desenvolvimento .NET.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="2b5d2-125">Projetos com dependências de bibliotecas que são uma versão diferente das bibliotecas incluídas no tempo de execução são impactados.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="2b5d2-126">A equipe de funções se comprometeu a fazer progressos concretos sobre o problema.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="2b5d2-127">A equipe abordará redirecionamentos de vinculação em 2.x antes de entrar em disponibilidade geral.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="2b5d2-128">A declaração oficial da equipe com correções e soluçãos sugeridas está disponível aqui: [Resolução da montagem em Funções Azure](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="2b5d2-129">Para obter mais informações, consulte [Compare 1.x e 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="2b5d2-130">Suporte à linguagem de programação</span><span class="sxs-lookup"><span data-stu-id="2b5d2-130">Programming language support</span></span>

<span data-ttu-id="2b5d2-131">Os idiomas a seguir são suportados em disponibilidade geral (GA), visualização ou experimental.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="2b5d2-132">Linguagem</span><span class="sxs-lookup"><span data-stu-id="2b5d2-132">Language</span></span>      |<span data-ttu-id="2b5d2-133">1.x</span><span class="sxs-lookup"><span data-stu-id="2b5d2-133">1.x</span></span>         |<span data-ttu-id="2b5d2-134">2. x</span><span class="sxs-lookup"><span data-stu-id="2b5d2-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="2b5d2-135">**C #**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-135">**C#**</span></span>        |<span data-ttu-id="2b5d2-136">GA</span><span class="sxs-lookup"><span data-stu-id="2b5d2-136">GA</span></span>          |<span data-ttu-id="2b5d2-137">Visualização</span><span class="sxs-lookup"><span data-stu-id="2b5d2-137">Preview</span></span>  |
|<span data-ttu-id="2b5d2-138">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-138">**JavaScript**</span></span>|<span data-ttu-id="2b5d2-139">GA</span><span class="sxs-lookup"><span data-stu-id="2b5d2-139">GA</span></span>          |<span data-ttu-id="2b5d2-140">Visualização</span><span class="sxs-lookup"><span data-stu-id="2b5d2-140">Preview</span></span>  |
|<span data-ttu-id="2b5d2-141">**F #**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-141">**F#**</span></span>        |<span data-ttu-id="2b5d2-142">GA</span><span class="sxs-lookup"><span data-stu-id="2b5d2-142">GA</span></span>          |         |
|<span data-ttu-id="2b5d2-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-143">**Java**</span></span>      |            |<span data-ttu-id="2b5d2-144">Visualização</span><span class="sxs-lookup"><span data-stu-id="2b5d2-144">Preview</span></span>  |
|<span data-ttu-id="2b5d2-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-145">**Python**</span></span>    |<span data-ttu-id="2b5d2-146">Experimental</span><span class="sxs-lookup"><span data-stu-id="2b5d2-146">Experimental</span></span>|         |
|<span data-ttu-id="2b5d2-147">**Php**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-147">**PHP**</span></span>       |<span data-ttu-id="2b5d2-148">Experimental</span><span class="sxs-lookup"><span data-stu-id="2b5d2-148">Experimental</span></span>|         |
|<span data-ttu-id="2b5d2-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-149">**TypeScript**</span></span>|<span data-ttu-id="2b5d2-150">Experimental</span><span class="sxs-lookup"><span data-stu-id="2b5d2-150">Experimental</span></span>|         |
|<span data-ttu-id="2b5d2-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-151">**Batch**</span></span>     |<span data-ttu-id="2b5d2-152">Experimental</span><span class="sxs-lookup"><span data-stu-id="2b5d2-152">Experimental</span></span>|         |
|<span data-ttu-id="2b5d2-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-153">**Bash**</span></span>      |<span data-ttu-id="2b5d2-154">Experimental</span><span class="sxs-lookup"><span data-stu-id="2b5d2-154">Experimental</span></span>|         |
|<span data-ttu-id="2b5d2-155">**Powershell**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-155">**PowerShell**</span></span>|<span data-ttu-id="2b5d2-156">Experimental</span><span class="sxs-lookup"><span data-stu-id="2b5d2-156">Experimental</span></span>|         |

<span data-ttu-id="2b5d2-157">Para obter mais informações, consulte [idiomas suportados](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="2b5d2-158">Planos de serviço de aplicativos</span><span class="sxs-lookup"><span data-stu-id="2b5d2-158">App service plans</span></span>

<span data-ttu-id="2b5d2-159">As funções são apoiadas por um *plano de serviço de aplicativo.*</span><span class="sxs-lookup"><span data-stu-id="2b5d2-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="2b5d2-160">O plano define os recursos utilizados pelo aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="2b5d2-161">Você pode atribuir planos a uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um nível de preço.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="2b5d2-162">Para uma abordagem sem servidor, os aplicativos de função podem usar o plano **de consumo.**</span><span class="sxs-lookup"><span data-stu-id="2b5d2-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="2b5d2-163">O plano de consumo irá dimensionar o back-end automaticamente com base na carga.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="2b5d2-164">Para obter mais informações, consulte [os planos de serviço do App](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="2b5d2-165">Criar sua primeira função</span><span class="sxs-lookup"><span data-stu-id="2b5d2-165">Create your first function</span></span>

<span data-ttu-id="2b5d2-166">Existem três maneiras comuns de criar aplicativos de função.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="2b5d2-167">O script funciona no portal.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-167">Script functions in the portal.</span></span>
- <span data-ttu-id="2b5d2-168">Crie os recursos necessários usando o Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="2b5d2-169">Crie funções localmente usando seu IDE favorito e publique-as no Azure.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="2b5d2-170">Para obter mais informações sobre a criação de uma função de script no portal, consulte [Criar sua primeira função no portal Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="2b5d2-171">Para construir a partir do Cli azure, consulte [Criar sua primeira função usando o Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="2b5d2-172">Para criar uma função no Visual Studio, consulte [Criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="2b5d2-173">Entenda os gatilhos e ligações</span><span class="sxs-lookup"><span data-stu-id="2b5d2-173">Understand triggers and bindings</span></span>

<span data-ttu-id="2b5d2-174">As funções são invocadas por um *gatilho* e podem ter exatamente uma.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="2b5d2-175">Além de invocar a função, certos gatilhos também servem como ligações.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="2b5d2-176">Você também pode definir várias ligações além do gatilho.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="2b5d2-177">*As vinculações* fornecem uma maneira declarativa de conectar dados ao seu código.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="2b5d2-178">Eles podem ser passados (entrada) ou receber dados (saída).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="2b5d2-179">Gatilhos e amarras facilitam o trabalho.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="2b5d2-180">As vinculações removem a sobrecarga da criação manual de conexões de banco de dados ou sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="2b5d2-181">Todas as informações necessárias para as vinculações estão contidas em um arquivo *special functions.json* para scripts ou declaradas com atributos em código.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="2b5d2-182">Alguns gatilhos comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-182">Some common triggers include:</span></span>

- <span data-ttu-id="2b5d2-183">Blob Storage: invoque sua função quando um arquivo ou pasta for carregado ou alterado no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="2b5d2-184">HTTP: invoque sua função como uma API REST.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="2b5d2-185">Fila: invoque sua função quando os itens existirem em uma fila.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="2b5d2-186">Temporizador: invoque sua função em uma cadência regular.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="2b5d2-187">Exemplos de vinculações incluem:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-187">Examples of bindings include:</span></span>

- <span data-ttu-id="2b5d2-188">CosmosDB: conecte-se facilmente ao banco de dados para carregar ou salvar arquivos.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="2b5d2-189">Armazenamento de tabela: trabalhe com armazenamento de chave/valor do seu aplicativo de função.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="2b5d2-190">Armazenamento na fila: recupere facilmente itens de uma fila ou coloque novos itens na fila.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="2b5d2-191">O exemplo a seguir *funções.json* arquivo define um gatilho e uma vinculação:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="2b5d2-192">Neste exemplo, a função é acionada por uma alteração `images` para o armazenamento de bolhas no recipiente.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="2b5d2-193">As informações para o arquivo são passadas, então o gatilho também age como uma vinculação.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="2b5d2-194">Existe outra vinculação para colocar informações `images`em uma fila chamada .</span><span class="sxs-lookup"><span data-stu-id="2b5d2-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="2b5d2-195">Aqui está o script C# para a função:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="2b5d2-196">O exemplo é uma função simples que leva o nome do arquivo que foi modificado ou carregado para armazenamento blob, e coloca-o em uma fila para processamento posterior.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="2b5d2-197">Para obter uma lista completa de gatilhos e vinculações, consulte [Os gatilhos e conceitos de vinculações do Azure](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="2b5d2-198">Proxies</span><span class="sxs-lookup"><span data-stu-id="2b5d2-198">Proxies</span></span>

<span data-ttu-id="2b5d2-199">Os proxies fornecem funcionalidade de redirecionamento para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="2b5d2-200">Proxies expõem um ponto final e mapeiam esse ponto final para outro recurso.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="2b5d2-201">Com proxies, você pode:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-201">With proxies, you can:</span></span>

- <span data-ttu-id="2b5d2-202">Redirecione uma solicitação recebida para outro ponto final.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="2b5d2-203">Modifique a solicitação de entrada antes de ser transmitida.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="2b5d2-204">Modifique ou forneça uma resposta.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-204">Modify or provide a response.</span></span>

<span data-ttu-id="2b5d2-205">Proxies são usados para cenários como:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="2b5d2-206">Simplificando, encurtando ou alterando a URL.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="2b5d2-207">Fornecendo um prefixo de API consistente para vários serviços back-end.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="2b5d2-208">Zombando de uma resposta a um ponto final sendo desenvolvido.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="2b5d2-209">Fornecendo uma resposta estática a um ponto final bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="2b5d2-210">Manter um ponto final de API consistente enquanto a parte traseira é movida ou migrada.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="2b5d2-211">Os proxies são armazenados como definições JSON.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="2b5d2-212">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-212">Here is an example:</span></span>

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

<span data-ttu-id="2b5d2-213">O `Domain Redirect` proxy pega uma rota encurtada e mapeia-a para o recurso de função mais longa.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="2b5d2-214">A transformação parece:</span><span class="sxs-lookup"><span data-stu-id="2b5d2-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="2b5d2-215">O `Root` proxy pega qualquer coisa`https://--shorturl--/`enviada para a URL raiz ( ) e redireciona-a para o site de documentação.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="2b5d2-216">Um exemplo de uso de proxies é mostrado no vídeo [Azure: Traga seu aplicativo para a nuvem com funções azure sem servidor](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="2b5d2-217">Em tempo real, um aplicativo ASP.NET Core em execução no SQL Server local é migrado para a Nuvem Azure.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="2b5d2-218">Os proxies são usados para ajudar a refatorar um projeto de API web tradicional para usar funções.</span><span class="sxs-lookup"><span data-stu-id="2b5d2-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="2b5d2-219">Para obter mais informações sobre proxies, consulte [Trabalhe com Proxies de Funções Azure](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="2b5d2-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b5d2-220">[Próximo](azure-serverless-platform.md)
>[anterior](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="2b5d2-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
