---
title: Cenários de negócios de exemplo e casos de uso para aplicativos sem servidor
description: Aprenda sem servidor com uma abordagem prática acessando exemplos que variam desde o processamento de imagens até o suporte móvel e pipelines de ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 3cb3b73325fccc327ccf17f7298048f2eeb3577a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158444"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="43232-103">Casos de uso e cenários de negócios sem servidor</span><span class="sxs-lookup"><span data-stu-id="43232-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="43232-104">Há muitos casos de uso e cenários para aplicativos sem servidor.</span><span class="sxs-lookup"><span data-stu-id="43232-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="43232-105">Este capítulo inclui exemplos que ilustram os diferentes cenários.</span><span class="sxs-lookup"><span data-stu-id="43232-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="43232-106">Os cenários incluem links para documentação relacionada e repositórios de código-fonte público.</span><span class="sxs-lookup"><span data-stu-id="43232-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="43232-107">Os exemplos neste capítulo permitem que você comece a usar sua própria compilação e implementação de soluções sem servidor.</span><span class="sxs-lookup"><span data-stu-id="43232-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="43232-108">Processamento de big data</span><span class="sxs-lookup"><span data-stu-id="43232-108">Big data processing</span></span>

![Mapear/reduzir diagrama](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="43232-110">Este exemplo usa sem servidor para fazer uma operação de mapeamento/redução em um conjunto de Big Data.</span><span class="sxs-lookup"><span data-stu-id="43232-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="43232-111">Ele determina a velocidade média de viagens de táxi amarelo de Nova York por dia em 2017.</span><span class="sxs-lookup"><span data-stu-id="43232-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="43232-112">Processamento de Big Data: MapReduce sem servidor no Azure</span><span class="sxs-lookup"><span data-stu-id="43232-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="43232-113">Criar aplicativos sem servidor: laboratório prático</span><span class="sxs-lookup"><span data-stu-id="43232-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="43232-114">Saiba como usar funções para executar a lógica do lado do servidor e criar arquiteturas sem servidor.</span><span class="sxs-lookup"><span data-stu-id="43232-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="43232-115">Escolhendo o melhor serviço do Azure para sua empresa</span><span class="sxs-lookup"><span data-stu-id="43232-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="43232-116">Criando Azure Functions</span><span class="sxs-lookup"><span data-stu-id="43232-116">Creating Azure Functions</span></span>
- <span data-ttu-id="43232-117">Usando gatilhos</span><span class="sxs-lookup"><span data-stu-id="43232-117">Using triggers</span></span>
- <span data-ttu-id="43232-118">Funções de encadeamento</span><span class="sxs-lookup"><span data-stu-id="43232-118">Chaining functions</span></span>
- <span data-ttu-id="43232-119">Fluxos de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="43232-119">Long-running workflows</span></span>
- <span data-ttu-id="43232-120">Monitoramento</span><span class="sxs-lookup"><span data-stu-id="43232-120">Monitoring</span></span>
- <span data-ttu-id="43232-121">Desenvolvimento, teste e implantação</span><span class="sxs-lookup"><span data-stu-id="43232-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="43232-122">Criar aplicativos sem servidor</span><span class="sxs-lookup"><span data-stu-id="43232-122">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="43232-123">Revisões do cliente</span><span class="sxs-lookup"><span data-stu-id="43232-123">Customer reviews</span></span>

<span data-ttu-id="43232-124">Este exemplo demonstra as novas ferramentas de Azure Functions para bibliotecas de classes C# no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43232-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="43232-125">Crie um site da Web em que os clientes enviem análises de produtos que são armazenados em blobs de armazenamento do Azure e CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="43232-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="43232-126">Adicione um Azure function para executar a moderação automatizada das revisões do cliente usando os serviços cognitivas do Azure.</span><span class="sxs-lookup"><span data-stu-id="43232-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="43232-127">Use uma fila de armazenamento do Azure para desacoplar o site da função.</span><span class="sxs-lookup"><span data-stu-id="43232-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="43232-128">Aplicativo de revisões de clientes com serviços cognitivas</span><span class="sxs-lookup"><span data-stu-id="43232-128">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="43232-129">Suporte a imagens do Docker para Linux</span><span class="sxs-lookup"><span data-stu-id="43232-129">Docker Linux image support</span></span>

<span data-ttu-id="43232-130">Este exemplo demonstra como criar um `Dockerfile` para compilar e executar Azure Functions em um contêiner do Docker do Linux.</span><span class="sxs-lookup"><span data-stu-id="43232-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="43232-131">Azure Functions no Linux</span><span class="sxs-lookup"><span data-stu-id="43232-131">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="43232-132">Processamento e validação de arquivo</span><span class="sxs-lookup"><span data-stu-id="43232-132">File processing and validation</span></span>

<span data-ttu-id="43232-133">Este exemplo analisa um conjunto de arquivos CSV de clientes hipotéticos.</span><span class="sxs-lookup"><span data-stu-id="43232-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="43232-134">Ele garante que todos os arquivos necessários para um cliente "lote" estejam prontos e, em seguida, valida a estrutura de cada arquivo.</span><span class="sxs-lookup"><span data-stu-id="43232-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="43232-135">Soluções diferentes são apresentadas usando Azure Functions, aplicativos lógicos e Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="43232-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="43232-136">Processamento e validação de arquivos usando Azure Functions, aplicativos lógicos e Durable Functions</span><span class="sxs-lookup"><span data-stu-id="43232-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="43232-137">Visualização de dados do jogo</span><span class="sxs-lookup"><span data-stu-id="43232-137">Game data visualization</span></span>

![Telemetria do jogo](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="43232-139">Um exemplo de como um desenvolvedor poderia implementar uma solução de visualização de dados no editor para seus jogos.</span><span class="sxs-lookup"><span data-stu-id="43232-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="43232-140">Na verdade, um plug-in do motor 4 e um plug-in do Unity inreais foram desenvolvidos usando esse exemplo como seu back-end.</span><span class="sxs-lookup"><span data-stu-id="43232-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="43232-141">O componente de serviço é independente do mecanismo de jogo.</span><span class="sxs-lookup"><span data-stu-id="43232-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="43232-142">Visualização de telemetria do jogo no editor</span><span class="sxs-lookup"><span data-stu-id="43232-142">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="43232-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="43232-143">GraphQL</span></span>

<span data-ttu-id="43232-144">Crie uma função sem servidor que expõe uma API GraphQL.</span><span class="sxs-lookup"><span data-stu-id="43232-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="43232-145">Funções sem servidor para GraphQL</span><span class="sxs-lookup"><span data-stu-id="43232-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="43232-146">Retransmissão de borda confiável de Internet das Coisas (IoT)</span><span class="sxs-lookup"><span data-stu-id="43232-146">Internet of Things (IoT) reliable edge relay</span></span>

![Arquitetura de IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="43232-148">Este exemplo implementa um novo protocolo de comunicação para habilitar a comunicação de upstream confiável de dispositivos IoT.</span><span class="sxs-lookup"><span data-stu-id="43232-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="43232-149">Ele automatiza a detecção de lacunas de dados e o aterramento.</span><span class="sxs-lookup"><span data-stu-id="43232-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="43232-150">Retransmissão de borda confiável de IoT</span><span class="sxs-lookup"><span data-stu-id="43232-150">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="43232-151">Arquitetura de referência de microserviços</span><span class="sxs-lookup"><span data-stu-id="43232-151">Microservices reference architecture</span></span>

![Arquitetura de referência](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="43232-153">Uma arquitetura de referência que orienta o processo de tomada de decisão envolvido na criação, no desenvolvimento e na entrega do aplicativo Rideshare by Relecloud (uma empresa fictícia).</span><span class="sxs-lookup"><span data-stu-id="43232-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="43232-154">Ele inclui instruções práticas para configurar e implantar todos os componentes da arquitetura.</span><span class="sxs-lookup"><span data-stu-id="43232-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="43232-155">Arquitetura de referência de microserviço sem servidor</span><span class="sxs-lookup"><span data-stu-id="43232-155">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="43232-156">Migrar aplicativos de console para servidor</span><span class="sxs-lookup"><span data-stu-id="43232-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="43232-157">Este exemplo é uma função genérica (`.csx` arquivo) que pode ser usada para converter qualquer aplicativo de console em um serviço Web HTTP no Azure functions.</span><span class="sxs-lookup"><span data-stu-id="43232-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="43232-158">Tudo o que você precisa fazer é editar um arquivo de configuração e especificar quais parâmetros de entrada serão passados como argumentos `.exe`para o.</span><span class="sxs-lookup"><span data-stu-id="43232-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="43232-159">Executar aplicativos de console no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="43232-159">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="43232-160">Sem servidor para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="43232-160">Serverless for mobile</span></span>

<span data-ttu-id="43232-161">Azure Functions são fáceis de implementar e manter e podem ser acessadas por meio de HTTP.</span><span class="sxs-lookup"><span data-stu-id="43232-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="43232-162">Eles são uma ótima maneira de implementar uma API para um aplicativo móvel.</span><span class="sxs-lookup"><span data-stu-id="43232-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="43232-163">A Microsoft oferece excelentes ferramentas de plataforma cruzada para iOS, Android e Windows com o Xamarin.</span><span class="sxs-lookup"><span data-stu-id="43232-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="43232-164">Como tal, o Xamarin e o Azure Functions estão trabalhando muito juntos.</span><span class="sxs-lookup"><span data-stu-id="43232-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="43232-165">Este artigo mostra como implementar uma função do Azure no portal do Azure ou no Visual Studio primeiro e criar um cliente de plataforma cruzada com Xamarin. Forms em execução no Android, iOS e Windows.</span><span class="sxs-lookup"><span data-stu-id="43232-165">This article shows how to implement an Azure Function in the Azure portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="43232-166">Implementando uma função simples do Azure com um cliente Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="43232-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="43232-167">Mensagens sem servidor</span><span class="sxs-lookup"><span data-stu-id="43232-167">Serverless messaging</span></span>

<span data-ttu-id="43232-168">Este exemplo mostra como utilizar Durable Functions padrão de Fan-out para carregar um número arbitrário de mensagens em qualquer número de sessões/partições.</span><span class="sxs-lookup"><span data-stu-id="43232-168">This sample shows how to utilize Durable Functions' fan-out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="43232-169">Ele visa o barramento de serviço, hubs de eventos ou filas de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="43232-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="43232-170">O exemplo também adiciona a capacidade de consumir essas mensagens com outra função do Azure e carregar os dados de tempo resultantes em outro hub de eventos.</span><span class="sxs-lookup"><span data-stu-id="43232-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="43232-171">Os dados são então ingeridos em serviços de análise, como o Azure Data Explorer.</span><span class="sxs-lookup"><span data-stu-id="43232-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="43232-172">Produzir e consumir mensagens por meio do barramento de serviço, dos hubs de eventos e das filas de armazenamento com Azure Functions</span><span class="sxs-lookup"><span data-stu-id="43232-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="43232-173">Recursos recomendados</span><span class="sxs-lookup"><span data-stu-id="43232-173">Recommended resources</span></span>

- [<span data-ttu-id="43232-174">Azure Functions no Linux</span><span class="sxs-lookup"><span data-stu-id="43232-174">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="43232-175">Processamento de Big Data: MapReduce sem servidor no Azure</span><span class="sxs-lookup"><span data-stu-id="43232-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="43232-176">Criar aplicativos sem servidor</span><span class="sxs-lookup"><span data-stu-id="43232-176">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="43232-177">Aplicativo de revisões de clientes com serviços cognitivas</span><span class="sxs-lookup"><span data-stu-id="43232-177">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="43232-178">Processamento e validação de arquivos usando Azure Functions, aplicativos lógicos e Durable Functions</span><span class="sxs-lookup"><span data-stu-id="43232-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="43232-179">Implementando uma função simples do Azure com um cliente Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="43232-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="43232-180">Visualização de telemetria do jogo no editor</span><span class="sxs-lookup"><span data-stu-id="43232-180">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="43232-181">Retransmissão de borda confiável de IoT</span><span class="sxs-lookup"><span data-stu-id="43232-181">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="43232-182">Produzir e consumir mensagens por meio do barramento de serviço, dos hubs de eventos e das filas de armazenamento com Azure Functions</span><span class="sxs-lookup"><span data-stu-id="43232-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="43232-183">Executar aplicativos de console no Azure Functions</span><span class="sxs-lookup"><span data-stu-id="43232-183">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="43232-184">Funções sem servidor para GraphQL</span><span class="sxs-lookup"><span data-stu-id="43232-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="43232-185">Arquitetura de referência de microserviço sem servidor</span><span class="sxs-lookup"><span data-stu-id="43232-185">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="43232-186">[Anterior](orchestration-patterns.md)
>[próximo](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="43232-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
