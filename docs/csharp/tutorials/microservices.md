---
title: Microsserviços hospedados no Docker - C#
description: Aprenda a criar serviços asp.net core que são executados em contêineres do Docker
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 1f4b38243beb1210b1374bd701fac66b2fa72cc5
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106344"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="ea382-103">Microsserviços hospedados no Docker</span><span class="sxs-lookup"><span data-stu-id="ea382-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="ea382-104">Este tutorial detalha as tarefas necessárias para compilar e implantar um microsserviço ASP.NET Core em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="ea382-105">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="ea382-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="ea382-106">Como gerar um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="ea382-107">Como criar um ambiente de desenvolvimento do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="ea382-108">Como compilar uma imagem do Docker com base em uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="ea382-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="ea382-109">Como implantar seu serviço em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="ea382-110">Ao longo do caminho, você também verá alguns recursos da linguagem C#:</span><span class="sxs-lookup"><span data-stu-id="ea382-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="ea382-111">Como converter objetos C# em cargas JSON.</span><span class="sxs-lookup"><span data-stu-id="ea382-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="ea382-112">Como compilar Objetos de Transferência de Dados imutáveis.</span><span class="sxs-lookup"><span data-stu-id="ea382-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="ea382-113">Como processar Solicitações HTTP de entrada e gerar a Resposta HTTP.</span><span class="sxs-lookup"><span data-stu-id="ea382-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="ea382-114">Como trabalhar com tipos de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="ea382-114">How to work with nullable value types.</span></span>

<span data-ttu-id="ea382-115">Você pode [exibir ou baixar o aplicativo de exemplo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) deste tópico.</span><span class="sxs-lookup"><span data-stu-id="ea382-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="ea382-116">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ea382-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="ea382-117">Por que o Docker?</span><span class="sxs-lookup"><span data-stu-id="ea382-117">Why Docker?</span></span>

<span data-ttu-id="ea382-118">O Docker facilita a criação de imagens de máquina padrão para hospedar seus serviços em um data center ou na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="ea382-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="ea382-119">O Docker permite que você configure a imagem e replique-a conforme o necessário para dimensionar a instalação de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="ea382-120">Todo o código neste tutorial funcionará em qualquer ambiente .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="ea382-121">As tarefas adicionais para uma instalação do Docker funcionarão para um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="ea382-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ea382-122">Prerequisites</span></span>

<span data-ttu-id="ea382-123">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="ea382-124">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="ea382-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="ea382-125">Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="ea382-126">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="ea382-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="ea382-127">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="ea382-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="ea382-128">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="ea382-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="ea382-129">Também precisará instalar o mecanismo Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="ea382-130">Consulte a [página Instalação de Docker](http://www.docker.com/products/docker) para obter instruções para sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="ea382-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="ea382-131">O Docker pode ser instalado em muitas distribuições do Linux, macOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="ea382-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="ea382-132">A página mencionada acima contém seções para cada uma das instalações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ea382-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="ea382-133">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="ea382-133">Create the Application</span></span>

<span data-ttu-id="ea382-134">Agora que você instalou todas as ferramentas, crie um novo aplicativo do ASP.NET Core em um diretório chamado "WeatherMicroservice" executando o seguinte comando no seu shell favorito:</span><span class="sxs-lookup"><span data-stu-id="ea382-134">Now that you've installed all the tools, create a new ASP.NET Core application in a directory called "WeatherMicroservice" by executing the following command in your favorite shell:</span></span>

```console
dotnet new web -o WeatherMicroservice
```

<span data-ttu-id="ea382-135">O comando `dotnet` executa as ferramentas necessárias para desenvolvimento em .NET.</span><span class="sxs-lookup"><span data-stu-id="ea382-135">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="ea382-136">Cada verbo executa um comando diferente.</span><span class="sxs-lookup"><span data-stu-id="ea382-136">Each verb executes a different command.</span></span>

<span data-ttu-id="ea382-137">O comando `dotnet new` é usado para criar projetos do .Net Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-137">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="ea382-138">A opção `-o WeatherMicroservice` após o comando `dotnet new` é usada para fornecer o local para criar o aplicativo do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-138">The `-o WeatherMicroservice` option after the `dotnet new` command is used to give the location to create the ASP.NET Core application.</span></span>

<span data-ttu-id="ea382-139">Para esse microsserviço, queremos o aplicativo Web mais simples e leve possível, portanto, usamos o modelo "ASP.NET Core Vazio", especificando seu nome curto, `web`.</span><span class="sxs-lookup"><span data-stu-id="ea382-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="ea382-140">O modelo cria quatro arquivos para você:</span><span class="sxs-lookup"><span data-stu-id="ea382-140">The template creates four files for you:</span></span>

* <span data-ttu-id="ea382-141">Um arquivo Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="ea382-141">A Startup.cs file.</span></span> <span data-ttu-id="ea382-142">Contém a base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="ea382-143">Um arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="ea382-143">A Program.cs file.</span></span> <span data-ttu-id="ea382-144">Contém o ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="ea382-145">Um arquivo WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="ea382-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="ea382-146">Esse é o arquivo de compilação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-146">This is the build file for the application.</span></span>
* <span data-ttu-id="ea382-147">Um arquivo Properties/launchSettings.json.</span><span class="sxs-lookup"><span data-stu-id="ea382-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="ea382-148">Contém as configurações de depuração usadas pelos IDEs.</span><span class="sxs-lookup"><span data-stu-id="ea382-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="ea382-149">Agora você pode executar o aplicativo gerado pelo modelo:</span><span class="sxs-lookup"><span data-stu-id="ea382-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="ea382-150">Esse comando restaurará primeiro as dependências necessárias para compilar o aplicativo e, em seguida, compilará o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="ea382-151">A configuração padrão escuta `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="ea382-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="ea382-152">Abra um navegador, navegue até a página e veja uma mensagem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ea382-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="ea382-153">.</span><span class="sxs-lookup"><span data-stu-id="ea382-153">message.</span></span>

<span data-ttu-id="ea382-154">Quando estiver pronto, você poderá desligar o aplicativo pressionando <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ea382-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="ea382-155">Anatomia de um aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea382-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="ea382-156">Agora que você criou o aplicativo, vamos analisar como essa funcionalidade é implementada.</span><span class="sxs-lookup"><span data-stu-id="ea382-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="ea382-157">Há dois dos arquivos gerados que são particularmente interessantes neste ponto: WeatherMicroservice.csproj e Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="ea382-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="ea382-158">O arquivo .csproj contém informações sobre o projeto.</span><span class="sxs-lookup"><span data-stu-id="ea382-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="ea382-159">Os dois nós mais interessantes são `<TargetFramework>` e `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="ea382-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="ea382-160">O nó `<TargetFramework>` especifica a versão do .NET que executará esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="ea382-161">Cada nó `<PackageReference>` é usado para especificar um pacote necessário para esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="ea382-162">O aplicativo é implementado em Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="ea382-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="ea382-163">Esse arquivo contém a classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ea382-163">This file contains the startup class.</span></span>

<span data-ttu-id="ea382-164">Os dois métodos são chamados pela infraestrutura do ASP.NET Core para configurar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="ea382-165">O método `ConfigureServices` descreve os serviços que são necessários para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="ea382-166">Você está compilando um microsserviço enxuto, portanto, não precisa configurar dependências.</span><span class="sxs-lookup"><span data-stu-id="ea382-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="ea382-167">O método `Configure` configura os manipuladores para solicitações HTTP de entrada.</span><span class="sxs-lookup"><span data-stu-id="ea382-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="ea382-168">O modelo gera um manipulador simples que responde a qualquer solicitação com o texto "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="ea382-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="ea382-169">Criar um microsserviço</span><span class="sxs-lookup"><span data-stu-id="ea382-169">Build a microservice</span></span>

<span data-ttu-id="ea382-170">O serviço criado fornecerá relatórios meteorológicos de qualquer lugar do mundo.</span><span class="sxs-lookup"><span data-stu-id="ea382-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="ea382-171">Em um aplicativo de produção, você chamaria algum serviço para obter os dados meteorológicos.</span><span class="sxs-lookup"><span data-stu-id="ea382-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="ea382-172">Em nosso exemplo, geraremos uma previsão do tempo aleatória.</span><span class="sxs-lookup"><span data-stu-id="ea382-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="ea382-173">Há várias tarefas que você precisará executar para implementar nosso serviço meteorológico aleatório:</span><span class="sxs-lookup"><span data-stu-id="ea382-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="ea382-174">Analise a solicitação de entrada para ler a latitude e a longitude.</span><span class="sxs-lookup"><span data-stu-id="ea382-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="ea382-175">Gere alguns dados de previsão aleatórios.</span><span class="sxs-lookup"><span data-stu-id="ea382-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="ea382-176">Converta esses dados de previsão aleatórios de objetos C# para pacotes JSON.</span><span class="sxs-lookup"><span data-stu-id="ea382-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="ea382-177">Defina o cabeçalho de resposta para indicar que o serviço retorna JSON.</span><span class="sxs-lookup"><span data-stu-id="ea382-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="ea382-178">Escreva a resposta.</span><span class="sxs-lookup"><span data-stu-id="ea382-178">Write the response.</span></span>

<span data-ttu-id="ea382-179">As próximas seções orientarão você por cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="ea382-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="ea382-180">Análise da cadeia de caracteres de consulta</span><span class="sxs-lookup"><span data-stu-id="ea382-180">Parsing the Query String</span></span>

<span data-ttu-id="ea382-181">Você começará pela análise de cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="ea382-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="ea382-182">O serviço aceitará os argumentos 'lat' e 'long' na cadeia de consulta nesta forma:</span><span class="sxs-lookup"><span data-stu-id="ea382-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="ea382-183">Todas as alterações que você precisa fazer estão na expressão lambda definida como o argumento `app.Run` em sua classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ea382-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="ea382-184">O argumento na expressão lambda é o `HttpContext` para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="ea382-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="ea382-185">Uma de suas propriedades é o objeto `Request`.</span><span class="sxs-lookup"><span data-stu-id="ea382-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="ea382-186">O objeto `Request` tem uma propriedade `Query` que contém um dicionário com todos os valores na cadeia de consulta da solicitação.</span><span class="sxs-lookup"><span data-stu-id="ea382-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="ea382-187">A primeira adição serve para encontrar os valores de latitude e longitude:</span><span class="sxs-lookup"><span data-stu-id="ea382-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="ea382-188">Os valores do dicionário `Query` são do tipo `StringValue`.</span><span class="sxs-lookup"><span data-stu-id="ea382-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="ea382-189">Esse tipo pode conter uma coleção de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea382-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="ea382-190">Para o serviço meteorológico, cada valor é uma cadeia de caracteres única.</span><span class="sxs-lookup"><span data-stu-id="ea382-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="ea382-191">É por isso que há a chamada para `FirstOrDefault()` no código acima.</span><span class="sxs-lookup"><span data-stu-id="ea382-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="ea382-192">Em seguida, você precisa converter as cadeias de caracteres em doubles.</span><span class="sxs-lookup"><span data-stu-id="ea382-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="ea382-193">O método que você usará para converter a cadeia de caracteres em um double é `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="ea382-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="ea382-194">Esse método utiliza parâmetros C# para indicar se a cadeia de caracteres de entrada pode ser convertida em um double.</span><span class="sxs-lookup"><span data-stu-id="ea382-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="ea382-195">Se a cadeia de caracteres for uma representação válida de um double, o método retornará true, e o argumento `result` conterá o valor.</span><span class="sxs-lookup"><span data-stu-id="ea382-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="ea382-196">Se a cadeia de caracteres não representar um double válida, o método retornará false.</span><span class="sxs-lookup"><span data-stu-id="ea382-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="ea382-197">Adapte essa API com o uso de um *método de extensão* que retorna um *double anulável*.</span><span class="sxs-lookup"><span data-stu-id="ea382-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="ea382-198">O *tipo de valor anulável* é um tipo que representa algum tipo de valor e também pode apresentar um valor ausente ou nulo.</span><span class="sxs-lookup"><span data-stu-id="ea382-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="ea382-199">Um tipo que permite valor nulo é representado por meio do acréscimo do caractere `?` à declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="ea382-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="ea382-200">Métodos de extensão são métodos definidos como estáticos, mas ao adicionar o modificador `this` no primeiro parâmetro é possível chamá-los como se fossem membros dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ea382-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="ea382-201">Os métodos de extensão só podem ser definidos em classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="ea382-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="ea382-202">Confira aqui a definição da classe que contém o método de extensão para análise:</span><span class="sxs-lookup"><span data-stu-id="ea382-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="ea382-203">Antes de chamar o método de extensão, altere a cultura atual para invariável:</span><span class="sxs-lookup"><span data-stu-id="ea382-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="ea382-204">Isso garante que seu aplicativo analise os mesmos números em qualquer servidor, independentemente de sua cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="ea382-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="ea382-205">Agora você pode usar o método de extensão para converter os argumentos da cadeia de caracteres de consulta no tipo duplo:</span><span class="sxs-lookup"><span data-stu-id="ea382-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="ea382-206">Para testar o código de análise com facilidade, atualize a resposta para incluir os valores dos argumentos:</span><span class="sxs-lookup"><span data-stu-id="ea382-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="ea382-207">Neste ponto, você pode executar o aplicativo Web e verificar se o código de análise está funcionando.</span><span class="sxs-lookup"><span data-stu-id="ea382-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="ea382-208">Adicione valores à solicitação da Web em um navegador e você verá os resultados atualizados.</span><span class="sxs-lookup"><span data-stu-id="ea382-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="ea382-209">Compilar uma previsão do tempo aleatória</span><span class="sxs-lookup"><span data-stu-id="ea382-209">Build a random weather forecast</span></span>

<span data-ttu-id="ea382-210">A próxima tarefa é compilar uma previsão do tempo aleatória.</span><span class="sxs-lookup"><span data-stu-id="ea382-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="ea382-211">Vamos começar com um contêiner de dados com os valores que você gostaria para uma previsão do tempo:</span><span class="sxs-lookup"><span data-stu-id="ea382-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

<span data-ttu-id="ea382-212">Em seguida, compile um construtor que define aleatoriamente os valores.</span><span class="sxs-lookup"><span data-stu-id="ea382-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="ea382-213">Este construtor usa os valores de latitude e longitude para propagar o gerador de número `Random`.</span><span class="sxs-lookup"><span data-stu-id="ea382-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="ea382-214">Isso significa que a previsão para o mesmo local é a mesma.</span><span class="sxs-lookup"><span data-stu-id="ea382-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="ea382-215">Se você alterar os argumentos para latitude e longitude, obterá uma previsão diferente (porque começou com uma semente diferente).</span><span class="sxs-lookup"><span data-stu-id="ea382-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="ea382-216">Agora você pode gerar a previsão de cinco dias em seu método de resposta:</span><span class="sxs-lookup"><span data-stu-id="ea382-216">You can now generate the 5-day forecast in your response method:</span></span>

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a><span data-ttu-id="ea382-217">Compile a resposta JSON</span><span class="sxs-lookup"><span data-stu-id="ea382-217">Build the JSON response</span></span>

<span data-ttu-id="ea382-218">A tarefa de código final no servidor é converter a lista `WeatherReport` no documento JSON e enviar isso de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ea382-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="ea382-219">Vamos começar criando o documento JSON.</span><span class="sxs-lookup"><span data-stu-id="ea382-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="ea382-220">Você adicionará o serializador JSON da NewtonSoft à lista de dependências.</span><span class="sxs-lookup"><span data-stu-id="ea382-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="ea382-221">Você pode fazer isso usando o seguinte comando `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="ea382-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="ea382-222">Em seguida, use a classe `JsonConvert` para gravar o objeto em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="ea382-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="ea382-223">O código acima converte o objeto de previsão (uma lista de `WeatherForecast` objetos) em um documento JSON.</span><span class="sxs-lookup"><span data-stu-id="ea382-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="ea382-224">Depois de ter construído o documento de resposta, defina o tipo de conteúdo como `application/json` e grave a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea382-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="ea382-225">Agora, o aplicativo é executado e retorna previsões aleatórias.</span><span class="sxs-lookup"><span data-stu-id="ea382-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="ea382-226">Criar uma imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="ea382-226">Build a Docker image</span></span>

<span data-ttu-id="ea382-227">Nossa tarefa final é executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="ea382-228">Vamos criar um contêiner do Docker que executa uma imagem do Docker que representa nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="ea382-229">Uma ***imagem do Docker*** é um arquivo que define o ambiente para execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="ea382-230">Um ***Contêiner do Docker*** representa uma instância em execução de uma Imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="ea382-231">Por analogia, você pode considerar a *imagem do Docker* como uma *classe* e o *Contêiner do Docker* como um objeto ou uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="ea382-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="ea382-232">O Dockerfile a seguir atenderá aos nossos propósitos:</span><span class="sxs-lookup"><span data-stu-id="ea382-232">The following Dockerfile will serve for our purposes:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="ea382-233">Vamos analisar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ea382-233">Let's go over its contents.</span></span>

<span data-ttu-id="ea382-234">A primeira linha especifica a imagem de origem usada para compilar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ea382-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="ea382-235">O Docker permite que você configure uma imagem de máquina com base em um modelo de origem.</span><span class="sxs-lookup"><span data-stu-id="ea382-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="ea382-236">Isso significa que não é necessário fornecer todos os parâmetros da máquina ao iniciar, você só precisa fornecer as alterações.</span><span class="sxs-lookup"><span data-stu-id="ea382-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="ea382-237">As alterações feitas aqui servem para incluir nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="ea382-238">Neste exemplo, usaremos a versão `2.1-sdk` da imagem `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="ea382-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="ea382-239">Essa é a maneira mais fácil de criar um ambiente funcional do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="ea382-240">Esta imagem inclui o tempo de execução do .NET Core e o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="ea382-241">Isso torna mais fácil começar a usar e compilar, mas cria uma imagem maior, assim, vamos usar essa imagem para compilar o aplicativo e uma imagem diferente para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="ea382-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="ea382-242">As próximas linhas configuram e compilam seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ea382-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="ea382-243">Isso copiará o arquivo de projeto do diretório atual para a VM do Docker e restaurará todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="ea382-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="ea382-244">Usar a CLI do dotnet significa que a imagem do Docker deve incluir o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="ea382-245">Depois disso, o restante do seu aplicativo será copiado e o comando `dotnet
publish` compilará e empacotará seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ea382-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="ea382-246">Por fim, criamos uma segunda imagem do Docker que executa o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ea382-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="ea382-247">Esta imagem usa a versão `2.1-aspnetcore-runtime` da imagem `dotnet`, que contém tudo o que é necessário para executar os aplicativos do ASP.NET Core, mas não inclui o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea382-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="ea382-248">Isso significa que essa imagem não pode ser usada para compilar aplicativos do .NET Core, mas também torna a imagem final menor.</span><span class="sxs-lookup"><span data-stu-id="ea382-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="ea382-249">Para fazer isso funcionar, copiamos o aplicativo de compilado da primeira imagem para a segunda.</span><span class="sxs-lookup"><span data-stu-id="ea382-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="ea382-250">O comando `ENTRYPOINT` informa o Docker sobre qual comando inicia o serviço.</span><span class="sxs-lookup"><span data-stu-id="ea382-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="ea382-251">Compilando e executando a imagem em um contêiner</span><span class="sxs-lookup"><span data-stu-id="ea382-251">Building and running the image in a container</span></span>

<span data-ttu-id="ea382-252">Vamos compilar uma imagem e executar o serviço dentro de um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="ea382-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="ea382-253">Você não quer que todos os arquivos de seu diretório local sejam copiados na imagem.</span><span class="sxs-lookup"><span data-stu-id="ea382-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="ea382-254">Em vez disso, compile o aplicativo no contêiner.</span><span class="sxs-lookup"><span data-stu-id="ea382-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="ea382-255">Você criará um arquivo `.dockerignore` para especificar os diretórios que não são copiados na imagem.</span><span class="sxs-lookup"><span data-stu-id="ea382-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="ea382-256">Você não que copiar nenhum ativo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ea382-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="ea382-257">Especifique os diretórios de compilação e publicação no arquivo `.dockerignore`:</span><span class="sxs-lookup"><span data-stu-id="ea382-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="ea382-258">Crie a imagem usando o comando `docker build`.</span><span class="sxs-lookup"><span data-stu-id="ea382-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="ea382-259">Execute o seguinte comando no diretório que contém seu código.</span><span class="sxs-lookup"><span data-stu-id="ea382-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="ea382-260">Esse comando compila a imagem do contêiner com base em todas as informações de seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="ea382-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="ea382-261">O argumento `-t` fornece uma marca, ou nome, para essa imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="ea382-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="ea382-262">Na linha de comando acima, a marca usada para o contêiner do Docker é `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="ea382-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="ea382-263">Quando esse comando for concluído, você terá um contêiner pronto para executar seu novo serviço.</span><span class="sxs-lookup"><span data-stu-id="ea382-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="ea382-264">Execute o seguinte comando para iniciar o contêiner e também o serviço:</span><span class="sxs-lookup"><span data-stu-id="ea382-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="ea382-265">A opção `-d` representa a execução do contêiner desanexado do terminal atual.</span><span class="sxs-lookup"><span data-stu-id="ea382-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="ea382-266">Isso significa que você não verá a saída do comando em seu terminal.</span><span class="sxs-lookup"><span data-stu-id="ea382-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="ea382-267">A opção `-p` indica o mapeamento de porta entre o serviço e o host.</span><span class="sxs-lookup"><span data-stu-id="ea382-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="ea382-268">Aqui diz que qualquer solicitação de entrada na porta 80 deve ser encaminhada para a porta 80 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="ea382-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="ea382-269">Usar 80 corresponde à porta em que seu serviço está escutando, que é a porta padrão para aplicativos de produção.</span><span class="sxs-lookup"><span data-stu-id="ea382-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="ea382-270">O argumento `--name` nomeia o contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="ea382-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="ea382-271">É um nome conveniente que você pode usar para trabalhar com esse contêiner.</span><span class="sxs-lookup"><span data-stu-id="ea382-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="ea382-272">É possível ver se a imagem está sendo executada verificando o comando:</span><span class="sxs-lookup"><span data-stu-id="ea382-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="ea382-273">Se o contêiner estiver em execução, você verá uma linha que o lista nos processos em execução.</span><span class="sxs-lookup"><span data-stu-id="ea382-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="ea382-274">(Pode ser o único.)</span><span class="sxs-lookup"><span data-stu-id="ea382-274">(It may be the only one.)</span></span>

<span data-ttu-id="ea382-275">Teste seu serviço abrindo um navegador, navegando até localhost e especificando uma latitude e longitude:</span><span class="sxs-lookup"><span data-stu-id="ea382-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="ea382-276">Anexar um contêiner em execução</span><span class="sxs-lookup"><span data-stu-id="ea382-276">Attaching to a running container</span></span>

<span data-ttu-id="ea382-277">Quando você executa o serviço em uma janela Comando, pode ver informações de diagnóstico impressas para cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="ea382-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="ea382-278">Você não vê essas informações quando o contêiner está sendo executado no modo desconectado.</span><span class="sxs-lookup"><span data-stu-id="ea382-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="ea382-279">O comando attach do Docker permite que você anexe a um contêiner em execução para que você possa ver as informações de log.</span><span class="sxs-lookup"><span data-stu-id="ea382-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="ea382-280">Execute este comando a partir de uma janela de comando:</span><span class="sxs-lookup"><span data-stu-id="ea382-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="ea382-281">O argumento `--sig-proxy=false` significa que os comandos <kbd>Ctrl</kbd>+<kbd>C</kbd> não são enviados ao processo do contêiner, mas, em vez disso, interrompem o comando `docker attach`.</span><span class="sxs-lookup"><span data-stu-id="ea382-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="ea382-282">O argumento final é o nome fornecido ao contêiner no comando `docker run`.</span><span class="sxs-lookup"><span data-stu-id="ea382-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="ea382-283">Use também a ID de contêiner atribuída pelo Docker para se referir a qualquer contêiner.</span><span class="sxs-lookup"><span data-stu-id="ea382-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="ea382-284">Se você não tiver especificado um nome para seu contêiner no `docker run`, use a ID do contêiner.</span><span class="sxs-lookup"><span data-stu-id="ea382-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="ea382-285">Abra um navegador e navegue até seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ea382-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="ea382-286">Você verá as mensagens de diagnóstico nas janelas de comando do contêiner anexado em execução.</span><span class="sxs-lookup"><span data-stu-id="ea382-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="ea382-287">Pressione <kbd>Ctrl</kbd>+<kbd>C</kbd> para interromper o processo de anexar.</span><span class="sxs-lookup"><span data-stu-id="ea382-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="ea382-288">Quando você terminar de trabalhar com seu contêiner, interrompa-o:</span><span class="sxs-lookup"><span data-stu-id="ea382-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="ea382-289">O contêiner e a imagem ainda estão disponíveis para a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="ea382-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="ea382-290">Se você quiser remover o contêiner do seu computador, use este comando:</span><span class="sxs-lookup"><span data-stu-id="ea382-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="ea382-291">Se você quiser remover imagens não usadas do seu computador, use este comando:</span><span class="sxs-lookup"><span data-stu-id="ea382-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="ea382-292">Conclusão</span><span class="sxs-lookup"><span data-stu-id="ea382-292">Conclusion</span></span> 

<span data-ttu-id="ea382-293">Neste tutorial, você criou um microsserviço do ASP.NET Core e adicionou alguns recursos simples.</span><span class="sxs-lookup"><span data-stu-id="ea382-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="ea382-294">Você criou uma imagem de contêiner do Docker para o serviço e executou o contêiner no computador.</span><span class="sxs-lookup"><span data-stu-id="ea382-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="ea382-295">Você anexou uma janela de terminal ao serviço e viu as mensagens de diagnóstico de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ea382-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="ea382-296">Durante o tutorial, você viu vários recursos da linguagem C# em ação.</span><span class="sxs-lookup"><span data-stu-id="ea382-296">Along the way, you saw several features of the C# language in action.</span></span>
