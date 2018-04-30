---
title: Microsserviços hospedados no Docker - C#
description: Aprenda a criar serviços asp.net core que são executados em contêineres do Docker
keywords: .NET, .NET Core, Docker, C#, ASP.NET, Microsserviço
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 253b622618ef62c28ac13a287c34b9d9049dd066
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="852ab-104">Microsserviços hospedados no Docker</span><span class="sxs-lookup"><span data-stu-id="852ab-104">Microservices hosted in Docker</span></span>

<span data-ttu-id="852ab-105">Este tutorial detalha as tarefas necessárias para compilar e implantar um microsserviço ASP.NET Core em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-105">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="852ab-106">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="852ab-106">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="852ab-107">Como gerar um aplicativo ASP.NET Core usando Yeoman</span><span class="sxs-lookup"><span data-stu-id="852ab-107">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="852ab-108">Como criar um ambiente de desenvolvimento do Docker</span><span class="sxs-lookup"><span data-stu-id="852ab-108">How to create a development Docker environment</span></span>
* <span data-ttu-id="852ab-109">Como compilar uma imagem do Docker com base em uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="852ab-109">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="852ab-110">Como implantar seu serviço em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-110">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="852ab-111">Ao longo do caminho, você também verá alguns recursos da linguagem C#:</span><span class="sxs-lookup"><span data-stu-id="852ab-111">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="852ab-112">Como converter objetos C# em cargas JSON.</span><span class="sxs-lookup"><span data-stu-id="852ab-112">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="852ab-113">Como compilar Objetos de Transferência de Dados imutáveis</span><span class="sxs-lookup"><span data-stu-id="852ab-113">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="852ab-114">Como processar solicitações HTTP de entrada e gerar a resposta HTTP</span><span class="sxs-lookup"><span data-stu-id="852ab-114">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="852ab-115">Como trabalhar com tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="852ab-115">How to work with nullable value types</span></span>

<span data-ttu-id="852ab-116">Você pode [exibir ou baixar o aplicativo de exemplo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) deste tópico.</span><span class="sxs-lookup"><span data-stu-id="852ab-116">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="852ab-117">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="852ab-117">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="852ab-118">Por que o Docker?</span><span class="sxs-lookup"><span data-stu-id="852ab-118">Why Docker?</span></span>

<span data-ttu-id="852ab-119">O Docker facilita a criação de imagens de máquina padrão para hospedar seus serviços em um data center ou na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="852ab-119">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="852ab-120">O Docker permite que você configure a imagem e replique-a conforme o necessário para dimensionar a instalação de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-120">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="852ab-121">Todo o código neste tutorial funcionará em qualquer ambiente .NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-121">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="852ab-122">As tarefas adicionais para uma instalação do Docker funcionarão para um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-122">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="852ab-123">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="852ab-123">Prerequisites</span></span>
<span data-ttu-id="852ab-124">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-124">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="852ab-125">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="852ab-125">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="852ab-126">Você pode executar esse aplicativo no Windows, Ubuntu Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-126">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="852ab-127">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="852ab-127">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="852ab-128">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="852ab-128">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="852ab-129">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="852ab-129">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="852ab-130">Também precisará instalar o mecanismo Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-130">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="852ab-131">Consulte a [página Instalação de Docker](http://www.docker.com/products/docker) para obter instruções para sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="852ab-131">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="852ab-132">O Docker pode ser instalado em muitas distribuições do Linux, macOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="852ab-132">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="852ab-133">A página mencionada acima contém seções para cada uma das instalações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="852ab-133">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="852ab-134">A maioria das instalações dos componentes é realizada por um gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="852ab-134">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="852ab-135">Se o gerenciador de pacotes do node.js `npm` estiver instalado, ignore esta etapa.</span><span class="sxs-lookup"><span data-stu-id="852ab-135">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="852ab-136">Caso contrário, instale o NodeJs mais recente do [nodejs.org](https://nodejs.org), que instalará o gerenciador de pacotes npm.</span><span class="sxs-lookup"><span data-stu-id="852ab-136">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="852ab-137">Aqui, você precisará instalar uma série de ferramentas de linha de comando que oferecem suporte ao desenvolvimento em ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-137">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="852ab-138">Os modelos de linha de comando usam Yeoman, Bower, Grunt e Gulp.</span><span class="sxs-lookup"><span data-stu-id="852ab-138">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="852ab-139">Se você os tiver instalado, ótimo, caso contrário, digite o seguinte em seu shell favorito:</span><span class="sxs-lookup"><span data-stu-id="852ab-139">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="852ab-140">A opção `-g` indica que é uma instalação global, e essas ferramentas estão disponíveis em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="852ab-140">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="852ab-141">(Uma instalação local define o escopo do pacote para um único projeto).</span><span class="sxs-lookup"><span data-stu-id="852ab-141">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="852ab-142">Após a instalação dessas ferramentas básicas, você precisará instalar os geradores de modelo ASP.NET do Yeoman:</span><span class="sxs-lookup"><span data-stu-id="852ab-142">Once you've installed those core tools, you need to install the yeoman ASP.NET template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="852ab-143">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="852ab-143">Create the Application</span></span>

<span data-ttu-id="852ab-144">Agora que você instalou todas as ferramentas, crie um novo aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-144">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="852ab-145">Para usar o gerador de linha de comando, execute o seguinte comando yeoman no shell de sua preferência:</span><span class="sxs-lookup"><span data-stu-id="852ab-145">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="852ab-146">Esse comando solicita a seleção do Tipo de aplicativo que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="852ab-146">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="852ab-147">Para este microsserviço, convém ter o aplicativo Web mais simples e mais leve possível, portanto, selecione 'Aplicativo Web Vazio'.</span><span class="sxs-lookup"><span data-stu-id="852ab-147">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="852ab-148">O modelo solicitará um nome.</span><span class="sxs-lookup"><span data-stu-id="852ab-148">The template will prompt you for a name.</span></span> <span data-ttu-id="852ab-149">Selecione 'WeatherMicroservice'.</span><span class="sxs-lookup"><span data-stu-id="852ab-149">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="852ab-150">O modelo cria oito arquivos para você:</span><span class="sxs-lookup"><span data-stu-id="852ab-150">The template creates eight files for you:</span></span>

* <span data-ttu-id="852ab-151">Um .gitignore, personalizado para aplicativos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-151">A .gitignore, customized for ASP.NET Core applications.</span></span>
* <span data-ttu-id="852ab-152">Um arquivo Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="852ab-152">A Startup.cs file.</span></span> <span data-ttu-id="852ab-153">Contém a base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-153">This contains the basis of the application.</span></span>
* <span data-ttu-id="852ab-154">Um arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="852ab-154">A Program.cs file.</span></span> <span data-ttu-id="852ab-155">Contém o ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-155">This contains the entry point of the application.</span></span>
* <span data-ttu-id="852ab-156">Um arquivo WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="852ab-156">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="852ab-157">Esse é o arquivo de compilação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-157">This is the build file for the application.</span></span>
* <span data-ttu-id="852ab-158">Um dockerfile.</span><span class="sxs-lookup"><span data-stu-id="852ab-158">A Dockerfile.</span></span> <span data-ttu-id="852ab-159">Esse script cria uma imagem do Docker para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-159">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="852ab-160">Um README.md.</span><span class="sxs-lookup"><span data-stu-id="852ab-160">A README.md.</span></span> <span data-ttu-id="852ab-161">Contém links para outros recursos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-161">This contains links to other ASP.NET Core resources.</span></span>
* <span data-ttu-id="852ab-162">Um arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="852ab-162">A web.config file.</span></span> <span data-ttu-id="852ab-163">Contém informações básicas de configuração.</span><span class="sxs-lookup"><span data-stu-id="852ab-163">This contains basic configuration information.</span></span>
* <span data-ttu-id="852ab-164">Um arquivo runtimeconfig.template.json.</span><span class="sxs-lookup"><span data-stu-id="852ab-164">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="852ab-165">Contém as configurações de depuração usadas pelos IDEs.</span><span class="sxs-lookup"><span data-stu-id="852ab-165">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="852ab-166">Agora você pode executar o aplicativo gerado pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="852ab-166">Now you can run the template generated application.</span></span> <span data-ttu-id="852ab-167">Isso é feito usando uma série de ferramentas na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="852ab-167">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="852ab-168">O comando `dotnet` executa as ferramentas necessárias para desenvolvimento em .NET.</span><span class="sxs-lookup"><span data-stu-id="852ab-168">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="852ab-169">Cada verbo executa um comando diferente</span><span class="sxs-lookup"><span data-stu-id="852ab-169">Each verb executes a different command</span></span>

<span data-ttu-id="852ab-170">A primeira etapa é restaurar todas as dependências:</span><span class="sxs-lookup"><span data-stu-id="852ab-170">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="852ab-171">A restauração do dotnet usa o gerenciador de pacotes do NuGet para instalar todos os pacotes necessários no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-171">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="852ab-172">Ele também gera um arquivo project.json.lock.</span><span class="sxs-lookup"><span data-stu-id="852ab-172">It also generates a project.json.lock file.</span></span> <span data-ttu-id="852ab-173">Esse arquivo contém informações sobre cada pacote referenciado.</span><span class="sxs-lookup"><span data-stu-id="852ab-173">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="852ab-174">Depois de restaurar todas as dependências, compile o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="852ab-174">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="852ab-175">E, depois de compilar o aplicativo, execute-o na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="852ab-175">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="852ab-176">A configuração padrão escuta `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="852ab-176">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="852ab-177">Abra um navegador, navegue até a página e veja uma mensagem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="852ab-177">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="852ab-178">.</span><span class="sxs-lookup"><span data-stu-id="852ab-178">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="852ab-179">Anatomia de um aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="852ab-179">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="852ab-180">Agora que você criou o aplicativo, vamos analisar como essa funcionalidade é implementada.</span><span class="sxs-lookup"><span data-stu-id="852ab-180">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="852ab-181">Há dois dos arquivos gerados que são particularmente interessantes neste ponto: project.json e Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="852ab-181">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="852ab-182">Project.json contém informações sobre o projeto.</span><span class="sxs-lookup"><span data-stu-id="852ab-182">Project.json contains information about the project.</span></span> <span data-ttu-id="852ab-183">Os dois nós com os quais você trabalhará com frequência são 'dependências' e 'estruturas'.</span><span class="sxs-lookup"><span data-stu-id="852ab-183">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="852ab-184">O nó dependências lista todos os pacotes necessários para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-184">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="852ab-185">No momento, este é um nó pequeno que precisa apenas dos pacotes que executam o servidor Web.</span><span class="sxs-lookup"><span data-stu-id="852ab-185">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="852ab-186">O nó 'estruturas' especifica as versões e as configurações da estrutura .NET que executará esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-186">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="852ab-187">O aplicativo é implementado em Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="852ab-187">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="852ab-188">Esse arquivo contém a classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="852ab-188">This file contains the startup class.</span></span>

<span data-ttu-id="852ab-189">Os dois métodos são chamados pela infraestrutura do ASP.NET Core para configurar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-189">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="852ab-190">O método `ConfigureServices` descreve os serviços que são necessários para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-190">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="852ab-191">Você está compilando um microsserviço enxuto, portanto, não precisa configurar dependências.</span><span class="sxs-lookup"><span data-stu-id="852ab-191">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="852ab-192">O método `Configure` configura os manipuladores para solicitações HTTP de entrada.</span><span class="sxs-lookup"><span data-stu-id="852ab-192">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="852ab-193">O modelo gera um manipulador simples que responde a qualquer solicitação com o texto "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="852ab-193">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="852ab-194">Criar um microsserviço</span><span class="sxs-lookup"><span data-stu-id="852ab-194">Build a microservice</span></span>

<span data-ttu-id="852ab-195">O serviço criado fornecerá relatórios meteorológicos de qualquer lugar do mundo.</span><span class="sxs-lookup"><span data-stu-id="852ab-195">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="852ab-196">Em um aplicativo de produção, você chamaria algum serviço para obter os dados meteorológicos.</span><span class="sxs-lookup"><span data-stu-id="852ab-196">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="852ab-197">Em nosso exemplo, geraremos uma previsão do tempo aleatória.</span><span class="sxs-lookup"><span data-stu-id="852ab-197">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="852ab-198">Há várias tarefas que você precisará executar para implementar nosso serviço meteorológico aleatório:</span><span class="sxs-lookup"><span data-stu-id="852ab-198">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="852ab-199">Analise a solicitação de entrada para ler a latitude e a longitude.</span><span class="sxs-lookup"><span data-stu-id="852ab-199">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="852ab-200">Gere alguns dados de previsão aleatórios.</span><span class="sxs-lookup"><span data-stu-id="852ab-200">Generate some random forecast data.</span></span>
* <span data-ttu-id="852ab-201">Converta esses dados de previsão aleatórios de objetos C# para pacotes JSON.</span><span class="sxs-lookup"><span data-stu-id="852ab-201">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="852ab-202">Defina o cabeçalho de resposta para indicar que o serviço retorna JSON.</span><span class="sxs-lookup"><span data-stu-id="852ab-202">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="852ab-203">Escreva a resposta.</span><span class="sxs-lookup"><span data-stu-id="852ab-203">Write the response.</span></span>

<span data-ttu-id="852ab-204">As próximas seções orientarão você por cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="852ab-204">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="852ab-205">Análise da cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="852ab-205">Parsing the Query String.</span></span>

<span data-ttu-id="852ab-206">Você começará pela análise de cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="852ab-206">You'll begin by parsing the query string.</span></span> <span data-ttu-id="852ab-207">O serviço aceitará os argumentos 'lat' e 'long' na cadeia de consulta nesta forma:</span><span class="sxs-lookup"><span data-stu-id="852ab-207">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="852ab-208">Todas as alterações que você precisa fazer estão na expressão lambda definida como o argumento `app.Run` em sua classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="852ab-208">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="852ab-209">O argumento na expressão lambda é o `HttpContext` para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="852ab-209">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="852ab-210">Uma de suas propriedades é o objeto `Request`.</span><span class="sxs-lookup"><span data-stu-id="852ab-210">One of its properties is the `Request` object.</span></span> <span data-ttu-id="852ab-211">O objeto `Request` tem uma propriedade `Query` que contém um dicionário com todos os valores na cadeia de consulta da solicitação.</span><span class="sxs-lookup"><span data-stu-id="852ab-211">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="852ab-212">A primeira adição serve para encontrar os valores de latitude e longitude:</span><span class="sxs-lookup"><span data-stu-id="852ab-212">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="852ab-213">Os valores de dicionário de Consulta são do tipo `StringValue`.</span><span class="sxs-lookup"><span data-stu-id="852ab-213">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="852ab-214">Esse tipo pode conter uma coleção de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="852ab-214">That type can contain a collection of strings.</span></span> <span data-ttu-id="852ab-215">Para o serviço meteorológico, cada valor é uma cadeia de caracteres única.</span><span class="sxs-lookup"><span data-stu-id="852ab-215">For your weather service, each value is a single string.</span></span> <span data-ttu-id="852ab-216">É por isso que há a chamada para `FirstOrDefault()` no código acima.</span><span class="sxs-lookup"><span data-stu-id="852ab-216">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="852ab-217">Em seguida, você precisa converter as cadeias de caracteres em doubles.</span><span class="sxs-lookup"><span data-stu-id="852ab-217">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="852ab-218">O método que você usará para converter a cadeia de caracteres em um double é `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="852ab-218">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="852ab-219">Esse método utiliza parâmetros C# para indicar se a cadeia de caracteres de entrada pode ser convertida em um double.</span><span class="sxs-lookup"><span data-stu-id="852ab-219">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="852ab-220">Se a cadeia de caracteres for uma representação válida de um double, o método retornará true, e o argumento `result` conterá o valor.</span><span class="sxs-lookup"><span data-stu-id="852ab-220">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="852ab-221">Se a cadeia de caracteres não representar um double válida, o método retornará false.</span><span class="sxs-lookup"><span data-stu-id="852ab-221">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="852ab-222">Adapte essa API com o uso de um *método de extensão* que retorna um *double anulável*.</span><span class="sxs-lookup"><span data-stu-id="852ab-222">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="852ab-223">O *tipo de valor anulável* é um tipo que representa algum tipo de valor e também pode apresentar um valor ausente ou nulo.</span><span class="sxs-lookup"><span data-stu-id="852ab-223">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="852ab-224">Um tipo que permite valor nulo é representado por meio do acréscimo do caractere `?` à declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="852ab-224">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="852ab-225">Métodos de extensão são métodos definidos como estáticos, mas ao adicionar o modificador `this` no primeiro parâmetro é possível chamá-los como se fossem membros dessa classe.</span><span class="sxs-lookup"><span data-stu-id="852ab-225">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="852ab-226">Os métodos de extensão só podem ser definidos em classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="852ab-226">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="852ab-227">Confira aqui a definição da classe que contém o método de extensão para análise:</span><span class="sxs-lookup"><span data-stu-id="852ab-227">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="852ab-228">A expressão `default(double?)` retorna o valor padrão para o tipo `double?`.</span><span class="sxs-lookup"><span data-stu-id="852ab-228">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="852ab-229">O valor padrão é o valor nulo (ou ausente).</span><span class="sxs-lookup"><span data-stu-id="852ab-229">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="852ab-230">Use esse método de extensão para converter os argumentos da cadeia de caracteres de consulta no tipo double:</span><span class="sxs-lookup"><span data-stu-id="852ab-230">You can use this extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="852ab-231">Para testar o código de análise com facilidade, atualize a resposta para incluir os valores dos argumentos:</span><span class="sxs-lookup"><span data-stu-id="852ab-231">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="852ab-232">Neste ponto, você pode executar o aplicativo Web e verificar se o código de análise está funcionando.</span><span class="sxs-lookup"><span data-stu-id="852ab-232">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="852ab-233">Adicione valores à solicitação da Web em um navegador e você verá os resultados atualizados.</span><span class="sxs-lookup"><span data-stu-id="852ab-233">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="852ab-234">Compilar uma previsão do tempo aleatória</span><span class="sxs-lookup"><span data-stu-id="852ab-234">Build a random weather forecast</span></span>

<span data-ttu-id="852ab-235">A próxima tarefa é compilar uma previsão do tempo aleatória.</span><span class="sxs-lookup"><span data-stu-id="852ab-235">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="852ab-236">Vamos começar com um contêiner de dados com os valores que você gostaria para uma previsão do tempo:</span><span class="sxs-lookup"><span data-stu-id="852ab-236">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="852ab-237">Em seguida, compile um construtor que define aleatoriamente os valores.</span><span class="sxs-lookup"><span data-stu-id="852ab-237">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="852ab-238">Este construtor usa os valores de latitude e longitude para propagar o Gerador de número aleatório.</span><span class="sxs-lookup"><span data-stu-id="852ab-238">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="852ab-239">Isso significa que a previsão para o mesmo local é a mesma.</span><span class="sxs-lookup"><span data-stu-id="852ab-239">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="852ab-240">Se você alterar os argumentos para a latitude e longitude, obterá uma previsão diferente (porque começou com uma propagação diferente.)</span><span class="sxs-lookup"><span data-stu-id="852ab-240">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="852ab-241">Agora você pode gerar a previsão de cinco dias em seu método de resposta:</span><span class="sxs-lookup"><span data-stu-id="852ab-241">You can now generate the 5-day forecast in your response method:</span></span>

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a><span data-ttu-id="852ab-242">Compile a resposta JSON.</span><span class="sxs-lookup"><span data-stu-id="852ab-242">Build the JSON response.</span></span>

<span data-ttu-id="852ab-243">A tarefa de código final no servidor é converter a matriz WeatherReport em um pacote JSON e enviá-lo de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="852ab-243">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="852ab-244">Vamos começar criando o pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="852ab-244">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="852ab-245">Você adicionará o Serializador de JSON da NewtonSoft à lista de dependências.</span><span class="sxs-lookup"><span data-stu-id="852ab-245">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="852ab-246">Faça isso usando a CLI `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="852ab-246">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="852ab-247">Em seguida, use a classe `JsonConvert` para gravar o objeto em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="852ab-247">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="852ab-248">O código acima converte o objeto de previsão (uma lista de `WeatherForecast` objetos) em um pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="852ab-248">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="852ab-249">Após a construção do pacote de resposta, defina o tipo de conteúdo como `application/json` e grave a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="852ab-249">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="852ab-250">Agora, o aplicativo é executado e retorna previsões aleatórias.</span><span class="sxs-lookup"><span data-stu-id="852ab-250">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="852ab-251">Criar uma imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="852ab-251">Build a Docker image</span></span>

<span data-ttu-id="852ab-252">Nossa tarefa final é executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-252">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="852ab-253">Vamos criar um contêiner do Docker que executa uma imagem do Docker que representa nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-253">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="852ab-254">Uma ***imagem do Docker*** é um arquivo que define o ambiente para execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-254">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="852ab-255">Um ***Contêiner do Docker*** representa uma instância em execução de uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-255">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="852ab-256">Por analogia, você pode considerar a *imagem do Docker* como uma *classe* e o *Contêiner do Docker* como um objeto ou uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="852ab-256">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="852ab-257">O Dockerfile criado pelo modelo ASP.NET servirá para nossos objetivos.</span><span class="sxs-lookup"><span data-stu-id="852ab-257">The Dockerfile created by the ASP.NET template will serve for our purposes.</span></span> <span data-ttu-id="852ab-258">Vamos analisar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="852ab-258">Let's go over its contents.</span></span>

<span data-ttu-id="852ab-259">A primeira linha especifica a imagem de origem:</span><span class="sxs-lookup"><span data-stu-id="852ab-259">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="852ab-260">O Docker permite que você configure uma imagem de máquina com base em um modelo de origem.</span><span class="sxs-lookup"><span data-stu-id="852ab-260">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="852ab-261">Isso significa que não é necessário fornecer todos os parâmetros da máquina ao iniciar, você só precisa fornecer as alterações.</span><span class="sxs-lookup"><span data-stu-id="852ab-261">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="852ab-262">As alterações feitas aqui servem para incluir nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-262">The changes here will be to include our application.</span></span>

<span data-ttu-id="852ab-263">Neste primeiro exemplo, usaremos a versão `1.1-sdk-msbuild` da imagem do dotnet.</span><span class="sxs-lookup"><span data-stu-id="852ab-263">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="852ab-264">Essa é a maneira mais fácil de criar um ambiente funcional do Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-264">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="852ab-265">Essa imagem inclui o tempo de execução do dotnet core e o SDK do dotnet.</span><span class="sxs-lookup"><span data-stu-id="852ab-265">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="852ab-266">Isso facilita o início e a compilação, mas cria uma imagem maior.</span><span class="sxs-lookup"><span data-stu-id="852ab-266">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="852ab-267">As próximas cinco linhas configuram e compilam seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="852ab-267">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="852ab-268">Isso copiará o arquivo de projeto do diretório atual para a VM do Docker e restaurará todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="852ab-268">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="852ab-269">Usar a CLI do dotnet significa que a imagem do Docker deve incluir o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="852ab-269">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="852ab-270">Depois disso, o restante de seu aplicativo será copiado e o comando publish do dotnet compilará e empacotará seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="852ab-270">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="852ab-271">A linha final do arquivo executa o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="852ab-271">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="852ab-272">Essa porta configurada é referenciada no argumento `--server.urls` para `dotnet` na última linha do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="852ab-272">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="852ab-273">O comando `ENTRYPOINT` informa ao Docker qual comando e quais opções de linha de comando iniciarão o serviço.</span><span class="sxs-lookup"><span data-stu-id="852ab-273">The `ENTRYPOINT` command informs Docker what command and command-line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="852ab-274">Crie e execute a imagem em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-274">Building and running the image in a container.</span></span>

<span data-ttu-id="852ab-275">Vamos compilar uma imagem e executar o serviço dentro de um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="852ab-275">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="852ab-276">Você não quer que todos os arquivos de seu diretório local sejam copiados na imagem.</span><span class="sxs-lookup"><span data-stu-id="852ab-276">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="852ab-277">Em vez disso, compile o aplicativo no contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-277">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="852ab-278">Você criará um arquivo `.dockerignore` para especificar os diretórios que não são copiados na imagem.</span><span class="sxs-lookup"><span data-stu-id="852ab-278">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="852ab-279">Você não que copiar nenhum ativo de compilação.</span><span class="sxs-lookup"><span data-stu-id="852ab-279">You don't want any of the build assets copied.</span></span> <span data-ttu-id="852ab-280">Especifique os diretórios de compilação e publicação no arquivo `.dockerignore`:</span><span class="sxs-lookup"><span data-stu-id="852ab-280">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="852ab-281">Crie a imagem usando o comando `docker build`.</span><span class="sxs-lookup"><span data-stu-id="852ab-281">You build the image using the `docker build` command.</span></span> <span data-ttu-id="852ab-282">Execute o seguinte comando no diretório que contém seu código.</span><span class="sxs-lookup"><span data-stu-id="852ab-282">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="852ab-283">Esse comando compila a imagem do contêiner com base em todas as informações de seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="852ab-283">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="852ab-284">O argumento `-t` fornece uma marca, ou nome, para essa imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-284">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="852ab-285">Na linha de comando acima, a marca usada para o contêiner do Docker é `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="852ab-285">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="852ab-286">Quando esse comando for concluído, você terá um contêiner pronto para executar seu novo serviço.</span><span class="sxs-lookup"><span data-stu-id="852ab-286">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="852ab-287">Execute o seguinte comando para iniciar o contêiner e também o serviço:</span><span class="sxs-lookup"><span data-stu-id="852ab-287">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="852ab-288">A opção `-d` representa a execução do contêiner desanexado do terminal atual.</span><span class="sxs-lookup"><span data-stu-id="852ab-288">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="852ab-289">Isso significa que você não verá a saída do comando em seu terminal.</span><span class="sxs-lookup"><span data-stu-id="852ab-289">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="852ab-290">A opção `-p` indica o mapeamento de porta entre o serviço e o host.</span><span class="sxs-lookup"><span data-stu-id="852ab-290">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="852ab-291">Aqui ela informa que qualquer solicitação de entrada na porta 80 deve ser encaminhada para a porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-291">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="852ab-292">5000 corresponde à porta na qual o serviço está escutando a partir dos argumentos de linha de comando especificados no Dockerfile acima.</span><span class="sxs-lookup"><span data-stu-id="852ab-292">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="852ab-293">O argumento `--name` nomeia o contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="852ab-293">The `--name` argument names your running container.</span></span> <span data-ttu-id="852ab-294">É um nome conveniente que você pode usar para trabalhar com esse contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-294">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="852ab-295">É possível ver se a imagem está sendo executada verificando o comando:</span><span class="sxs-lookup"><span data-stu-id="852ab-295">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="852ab-296">Se o contêiner estiver em execução, você verá uma linha que o lista nos processos em execução.</span><span class="sxs-lookup"><span data-stu-id="852ab-296">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="852ab-297">(Pode ser o único).</span><span class="sxs-lookup"><span data-stu-id="852ab-297">(It may be the only one).</span></span>

<span data-ttu-id="852ab-298">Teste seu serviço abrindo um navegador, navegando até localhost e especificando uma latitude e longitude:</span><span class="sxs-lookup"><span data-stu-id="852ab-298">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="852ab-299">Anexar um contêiner em execução</span><span class="sxs-lookup"><span data-stu-id="852ab-299">Attaching to a running container</span></span>

<span data-ttu-id="852ab-300">Quando você executa o serviço em uma janela de comando, pode ver informações de diagnóstico impressas para cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="852ab-300">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="852ab-301">Você não vê essas informações quando o contêiner está sendo executado no modo desconectado.</span><span class="sxs-lookup"><span data-stu-id="852ab-301">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="852ab-302">O comando attach do Docker permite que você anexe a um contêiner em execução para que você possa ver as informações de log.</span><span class="sxs-lookup"><span data-stu-id="852ab-302">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="852ab-303">Execute este comando a partir de uma janela de comando:</span><span class="sxs-lookup"><span data-stu-id="852ab-303">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="852ab-304">O argumento `--sig-proxy=false` significa que os comandos `Ctrl-C` não são enviados ao processo do contêiner, mas, em vez disso, interrompem o comando `docker attach`.</span><span class="sxs-lookup"><span data-stu-id="852ab-304">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="852ab-305">O argumento final é o nome fornecido ao contêiner no comando `docker run`.</span><span class="sxs-lookup"><span data-stu-id="852ab-305">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="852ab-306">Use também a ID de contêiner atribuída pelo Docker para se referir a qualquer contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-306">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="852ab-307">Se você não tiver especificado um nome para seu contêiner no `docker run`, use a id do contêiner.</span><span class="sxs-lookup"><span data-stu-id="852ab-307">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="852ab-308">Abra um navegador e navegue até seu serviço.</span><span class="sxs-lookup"><span data-stu-id="852ab-308">Open a browser and navigate to your service.</span></span> <span data-ttu-id="852ab-309">Você verá as mensagens de diagnóstico nas janelas de comando do contêiner anexado em execução.</span><span class="sxs-lookup"><span data-stu-id="852ab-309">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="852ab-310">Pressione `Ctrl-C` para interromper o processo de conexão.</span><span class="sxs-lookup"><span data-stu-id="852ab-310">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="852ab-311">Quando você terminar de trabalhar com seu contêiner, interrompa-o:</span><span class="sxs-lookup"><span data-stu-id="852ab-311">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="852ab-312">O contêiner e a imagem ainda estão disponíveis para a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="852ab-312">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="852ab-313">Se você quiser remover o contêiner do seu computador, use este comando:</span><span class="sxs-lookup"><span data-stu-id="852ab-313">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="852ab-314">Se você quiser remover imagens não usadas do seu computador, use este comando:</span><span class="sxs-lookup"><span data-stu-id="852ab-314">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="852ab-315">Conclusão</span><span class="sxs-lookup"><span data-stu-id="852ab-315">Conclusion</span></span> 

<span data-ttu-id="852ab-316">Neste tutorial, você criou um microsserviço do ASP.NET Core e adicionou alguns recursos simples.</span><span class="sxs-lookup"><span data-stu-id="852ab-316">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="852ab-317">Você criou uma imagem de contêiner do Docker para o serviço e executou o contêiner no computador.</span><span class="sxs-lookup"><span data-stu-id="852ab-317">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="852ab-318">Você anexou uma janela de terminal ao serviço e viu as mensagens de diagnóstico de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="852ab-318">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="852ab-319">Durante o tutorial, você viu vários recursos da linguagem C# em ação.</span><span class="sxs-lookup"><span data-stu-id="852ab-319">Along the way, you saw several features of the C# language in action.</span></span>
