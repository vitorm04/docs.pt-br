---
title: Aplicativos Azure Functions-sem servidor
description: O Azure Functions fornece recursos sem servidor em vários idiomas (C#, JavaScript, Java) e plataformas para fornecer código de escala instantânea controlado por eventos.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 7625b2a0dafb90dc1bf2fb7fe680d53b20764c09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171800"
---
# <a name="azure-functions"></a><span data-ttu-id="d91d8-103">Verificação de</span><span class="sxs-lookup"><span data-stu-id="d91d8-103">Azure Functions</span></span>

<span data-ttu-id="d91d8-104">O Azure Functions fornece uma experiência de computação sem servidor.</span><span class="sxs-lookup"><span data-stu-id="d91d8-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="d91d8-105">Uma função é invocada por um *gatilho* (como o acesso a um ponto de extremidade http ou um temporizador) e executa um bloco de código ou lógica de negócios.</span><span class="sxs-lookup"><span data-stu-id="d91d8-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="d91d8-106">As funções também dão suporte a *associações* especializadas que se conectam a recursos como armazenamento e filas.</span><span class="sxs-lookup"><span data-stu-id="d91d8-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logotipo do Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="d91d8-108">A versão de tempo de execução atual 3,0 dá suporte a aplicativos .NET Core 3,1 de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="d91d8-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="d91d8-109">Há suporte para idiomas adicionais além do C#, como JavaScript, F # e Java.</span><span class="sxs-lookup"><span data-stu-id="d91d8-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="d91d8-110">As funções criadas no portal fornecem uma sintaxe de script avançada.</span><span class="sxs-lookup"><span data-stu-id="d91d8-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="d91d8-111">As funções criadas como projetos autônomos podem ser implantadas com recursos e suporte completos à plataforma.</span><span class="sxs-lookup"><span data-stu-id="d91d8-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="d91d8-112">Para obter mais informações, consulte a [documentação do Azure Functions](/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="d91d8-112">For more information, see [Azure Functions documentation](/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="d91d8-113">Suporte à linguagem de programação</span><span class="sxs-lookup"><span data-stu-id="d91d8-113">Programming language support</span></span>

<span data-ttu-id="d91d8-114">Todos os idiomas a seguir têm suporte na disponibilidade geral (GA).</span><span class="sxs-lookup"><span data-stu-id="d91d8-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="d91d8-115">Idioma</span><span class="sxs-lookup"><span data-stu-id="d91d8-115">Language</span></span>      |<span data-ttu-id="d91d8-116">Tempos de execução com suporte</span><span class="sxs-lookup"><span data-stu-id="d91d8-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="d91d8-117">**C#**</span><span class="sxs-lookup"><span data-stu-id="d91d8-117">**C#**</span></span>        |<span data-ttu-id="d91d8-118">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d91d8-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="d91d8-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="d91d8-119">**JavaScript**</span></span>|<span data-ttu-id="d91d8-120">Nó 10 & 12</span><span class="sxs-lookup"><span data-stu-id="d91d8-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="d91d8-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="d91d8-121">**F#**</span></span>        |<span data-ttu-id="d91d8-122">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d91d8-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="d91d8-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="d91d8-123">**Java**</span></span>      |<span data-ttu-id="d91d8-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="d91d8-124">Java 8</span></span>            |
|<span data-ttu-id="d91d8-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="d91d8-125">**Python**</span></span>    |<span data-ttu-id="d91d8-126">Python 3,6, 3,7, & 3,8</span><span class="sxs-lookup"><span data-stu-id="d91d8-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="d91d8-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="d91d8-127">**TypeScript**</span></span>|<span data-ttu-id="d91d8-128">Nó 10 & 12 (via JavaScript)</span><span class="sxs-lookup"><span data-stu-id="d91d8-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="d91d8-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="d91d8-129">**PowerShell**</span></span>|<span data-ttu-id="d91d8-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="d91d8-130">PowerShell Core 6</span></span>|

<span data-ttu-id="d91d8-131">Para obter mais informações, consulte [Linguagens com suporte](/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="d91d8-131">For more information, see [Supported languages](/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="d91d8-132">Planos do serviço de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d91d8-132">App service plans</span></span>

<span data-ttu-id="d91d8-133">As funções são apoiadas por um *plano do serviço de aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="d91d8-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="d91d8-134">O plano define os recursos usados pelo aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="d91d8-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="d91d8-135">Você pode atribuir planos a uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um tipo de preço.</span><span class="sxs-lookup"><span data-stu-id="d91d8-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="d91d8-136">Para uma abordagem verdadeira sem servidor, os aplicativos de função podem usar o plano de **consumo** .</span><span class="sxs-lookup"><span data-stu-id="d91d8-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="d91d8-137">O plano de consumo dimensionará o back-end automaticamente com base na carga.</span><span class="sxs-lookup"><span data-stu-id="d91d8-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="d91d8-138">Outra opção de hospedagem para aplicativos de funções é o [plano Premium](/azure/azure-functions/functions-premium-plan).</span><span class="sxs-lookup"><span data-stu-id="d91d8-138">Another hosting option for function apps is the [Premium plan](/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="d91d8-139">Esse plano fornece uma instância "Always on" para evitar o início frio, dá suporte a recursos avançados como conectividade VNet e é executado em hardware Premium.</span><span class="sxs-lookup"><span data-stu-id="d91d8-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="d91d8-140">Para obter mais informações, consulte [planos do serviço de aplicativo](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="d91d8-140">For more information, see [App service plans](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="d91d8-141">Criar sua primeira função</span><span class="sxs-lookup"><span data-stu-id="d91d8-141">Create your first function</span></span>

<span data-ttu-id="d91d8-142">Há três maneiras comuns de criar aplicativos de funções.</span><span class="sxs-lookup"><span data-stu-id="d91d8-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="d91d8-143">Funções de script no Portal.</span><span class="sxs-lookup"><span data-stu-id="d91d8-143">Script functions in the portal.</span></span>
- <span data-ttu-id="d91d8-144">Crie os recursos necessários usando o CLI do Azure.</span><span class="sxs-lookup"><span data-stu-id="d91d8-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="d91d8-145">Crie funções localmente usando seu IDE favorito e publique-as no Azure.</span><span class="sxs-lookup"><span data-stu-id="d91d8-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="d91d8-146">Para obter mais informações sobre como criar uma função com script no portal, consulte [criar sua primeira função no portal do Azure](/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="d91d8-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="d91d8-147">Para criar a partir do CLI do Azure, consulte [criar sua primeira função usando o CLI do Azure](/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="d91d8-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="d91d8-148">Para criar uma função do Visual Studio, consulte [criar sua primeira função usando o Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d91d8-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="d91d8-149">Entender gatilhos e associações</span><span class="sxs-lookup"><span data-stu-id="d91d8-149">Understand triggers and bindings</span></span>

<span data-ttu-id="d91d8-150">As funções são invocadas por um *gatilho* e podem ter exatamente uma.</span><span class="sxs-lookup"><span data-stu-id="d91d8-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="d91d8-151">Além de invocar a função, determinados gatilhos também servem como associações.</span><span class="sxs-lookup"><span data-stu-id="d91d8-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="d91d8-152">Você também pode definir várias associações além do gatilho.</span><span class="sxs-lookup"><span data-stu-id="d91d8-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="d91d8-153">As *associações* fornecem uma maneira declarativa de conectar dados ao seu código.</span><span class="sxs-lookup"><span data-stu-id="d91d8-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="d91d8-154">Eles podem ser passados (entrada) ou receber dados (saída).</span><span class="sxs-lookup"><span data-stu-id="d91d8-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="d91d8-155">Os gatilhos e as associações facilitam o trabalho com as funções.</span><span class="sxs-lookup"><span data-stu-id="d91d8-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="d91d8-156">As associações removem a sobrecarga de criar manualmente as conexões do banco de dados ou do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="d91d8-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="d91d8-157">Todas as informações necessárias para as associações estão contidas em umfunctions.jsespecial \* no\* arquivo para scripts ou declaradas com atributos no código.</span><span class="sxs-lookup"><span data-stu-id="d91d8-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="d91d8-158">Alguns gatilhos comuns incluem:</span><span class="sxs-lookup"><span data-stu-id="d91d8-158">Some common triggers include:</span></span>

- <span data-ttu-id="d91d8-159">Armazenamento de BLOBs: invoque sua função quando um arquivo ou pasta for carregado ou alterado no armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d91d8-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="d91d8-160">HTTP: invoque sua função como uma API REST.</span><span class="sxs-lookup"><span data-stu-id="d91d8-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="d91d8-161">Fila: invoque sua função quando houver itens em uma fila.</span><span class="sxs-lookup"><span data-stu-id="d91d8-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="d91d8-162">Temporizador: invocar sua função em uma cadência regular.</span><span class="sxs-lookup"><span data-stu-id="d91d8-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="d91d8-163">Exemplos de associações incluem:</span><span class="sxs-lookup"><span data-stu-id="d91d8-163">Examples of bindings include:</span></span>

- <span data-ttu-id="d91d8-164">CosmosDB: Conecte-se facilmente ao banco de dados para carregar ou salvar arquivos.</span><span class="sxs-lookup"><span data-stu-id="d91d8-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="d91d8-165">Armazenamento de tabelas: trabalhe com o armazenamento de chave/valor do seu aplicativo de funções.</span><span class="sxs-lookup"><span data-stu-id="d91d8-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="d91d8-166">Armazenamento de filas: recuperar facilmente itens de uma fila ou colocar novos itens na fila.</span><span class="sxs-lookup"><span data-stu-id="d91d8-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="d91d8-167">O exemplo a seguir *functions.jsno* arquivo define um gatilho e uma associação:</span><span class="sxs-lookup"><span data-stu-id="d91d8-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="d91d8-168">Neste exemplo, a função é disparada por uma alteração no armazenamento de BLOBs no `images` contêiner.</span><span class="sxs-lookup"><span data-stu-id="d91d8-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="d91d8-169">As informações para o arquivo são passadas para que o gatilho também atue como uma associação.</span><span class="sxs-lookup"><span data-stu-id="d91d8-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="d91d8-170">Existe outra associação para colocar informações em uma fila chamada `images` .</span><span class="sxs-lookup"><span data-stu-id="d91d8-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="d91d8-171">Este é o script C# para a função:</span><span class="sxs-lookup"><span data-stu-id="d91d8-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="d91d8-172">O exemplo é uma função simples que usa o nome do arquivo que foi modificado ou carregado no armazenamento de BLOBs e o coloca em uma fila para processamento posterior.</span><span class="sxs-lookup"><span data-stu-id="d91d8-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="d91d8-173">Para obter uma lista completa de gatilhos e associações, consulte [Azure Functions os conceitos de gatilhos e associações](/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="d91d8-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d91d8-174">[Anterior](azure-serverless-platform.md) 
> [Avançar](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="d91d8-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
