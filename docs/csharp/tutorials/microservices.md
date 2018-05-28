---
title: Microsserviços hospedados no Docker - C#
description: Aprenda a criar serviços asp.net core que são executados em contêineres do Docker
ms.date: 02/03/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 7428051c1d9a29ba98ca1f28288b3c50ea36ae1a
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2018
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="b6420-103">Microsserviços hospedados no Docker</span><span class="sxs-lookup"><span data-stu-id="b6420-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="b6420-104">Este tutorial detalha as tarefas necessárias para compilar e implantar um microsserviço ASP.NET Core em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="b6420-105">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="b6420-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="b6420-106">Como gerar um aplicativo ASP.NET Core usando Yeoman</span><span class="sxs-lookup"><span data-stu-id="b6420-106">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="b6420-107">Como criar um ambiente de desenvolvimento do Docker</span><span class="sxs-lookup"><span data-stu-id="b6420-107">How to create a development Docker environment</span></span>
* <span data-ttu-id="b6420-108">Como compilar uma imagem do Docker com base em uma imagem existente.</span><span class="sxs-lookup"><span data-stu-id="b6420-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="b6420-109">Como implantar seu serviço em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="b6420-110">Ao longo do caminho, você também verá alguns recursos da linguagem C#:</span><span class="sxs-lookup"><span data-stu-id="b6420-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="b6420-111">Como converter objetos C# em cargas JSON.</span><span class="sxs-lookup"><span data-stu-id="b6420-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="b6420-112">Como compilar Objetos de Transferência de Dados imutáveis</span><span class="sxs-lookup"><span data-stu-id="b6420-112">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="b6420-113">Como processar solicitações HTTP de entrada e gerar a resposta HTTP</span><span class="sxs-lookup"><span data-stu-id="b6420-113">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="b6420-114">Como trabalhar com tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="b6420-114">How to work with nullable value types</span></span>

<span data-ttu-id="b6420-115">Você pode [exibir ou baixar o aplicativo de exemplo](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b6420-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="b6420-116">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b6420-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="b6420-117">Por que o Docker?</span><span class="sxs-lookup"><span data-stu-id="b6420-117">Why Docker?</span></span>

<span data-ttu-id="b6420-118">O Docker facilita a criação de imagens de máquina padrão para hospedar seus serviços em um data center ou na nuvem pública.</span><span class="sxs-lookup"><span data-stu-id="b6420-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="b6420-119">O Docker permite que você configure a imagem e replique-a conforme o necessário para dimensionar a instalação de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="b6420-120">Todo o código neste tutorial funcionará em qualquer ambiente .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="b6420-121">As tarefas adicionais para uma instalação do Docker funcionarão para um aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="b6420-122">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b6420-122">Prerequisites</span></span>
<span data-ttu-id="b6420-123">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-123">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="b6420-124">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="b6420-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="b6420-125">Você pode executar esse aplicativo no Windows, Ubuntu Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-125">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="b6420-126">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="b6420-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="b6420-127">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b6420-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="b6420-128">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="b6420-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="b6420-129">Também precisará instalar o mecanismo Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="b6420-130">Consulte a [página Instalação de Docker](http://www.docker.com/products/docker) para obter instruções para sua plataforma.</span><span class="sxs-lookup"><span data-stu-id="b6420-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="b6420-131">O Docker pode ser instalado em muitas distribuições do Linux, macOS ou Windows.</span><span class="sxs-lookup"><span data-stu-id="b6420-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="b6420-132">A página mencionada acima contém seções para cada uma das instalações disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b6420-132">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="b6420-133">A maioria das instalações dos componentes é realizada por um gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="b6420-133">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="b6420-134">Se o gerenciador de pacotes do node.js `npm` estiver instalado, ignore esta etapa.</span><span class="sxs-lookup"><span data-stu-id="b6420-134">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="b6420-135">Caso contrário, instale o NodeJs mais recente do [nodejs.org](https://nodejs.org), que instalará o gerenciador de pacotes npm.</span><span class="sxs-lookup"><span data-stu-id="b6420-135">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="b6420-136">Aqui, você precisará instalar uma série de ferramentas de linha de comando que oferecem suporte ao desenvolvimento em ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-136">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="b6420-137">Os modelos de linha de comando usam Yeoman, Bower, Grunt e Gulp.</span><span class="sxs-lookup"><span data-stu-id="b6420-137">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="b6420-138">Se você os tiver instalado, ótimo, caso contrário, digite o seguinte em seu shell favorito:</span><span class="sxs-lookup"><span data-stu-id="b6420-138">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="b6420-139">A opção `-g` indica que é uma instalação global, e essas ferramentas estão disponíveis em todo o sistema.</span><span class="sxs-lookup"><span data-stu-id="b6420-139">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="b6420-140">(Uma instalação local define o escopo do pacote para um único projeto).</span><span class="sxs-lookup"><span data-stu-id="b6420-140">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="b6420-141">Após a instalação dessas ferramentas básicas, você precisará instalar os geradores de modelo ASP.NET do Yeoman:</span><span class="sxs-lookup"><span data-stu-id="b6420-141">Once you've installed those core tools, you need to install the yeoman ASP.NET template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="b6420-142">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b6420-142">Create the Application</span></span>

<span data-ttu-id="b6420-143">Agora que você instalou todas as ferramentas, crie um novo aplicativo ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-143">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="b6420-144">Para usar o gerador de linha de comando, execute o seguinte comando yeoman no shell de sua preferência:</span><span class="sxs-lookup"><span data-stu-id="b6420-144">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="b6420-145">Esse comando solicita a seleção do Tipo de aplicativo que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="b6420-145">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="b6420-146">Para este microsserviço, convém ter o aplicativo Web mais simples e mais leve possível, portanto, selecione 'Aplicativo Web Vazio'.</span><span class="sxs-lookup"><span data-stu-id="b6420-146">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="b6420-147">O modelo solicitará um nome.</span><span class="sxs-lookup"><span data-stu-id="b6420-147">The template will prompt you for a name.</span></span> <span data-ttu-id="b6420-148">Selecione 'WeatherMicroservice'.</span><span class="sxs-lookup"><span data-stu-id="b6420-148">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="b6420-149">O modelo cria oito arquivos para você:</span><span class="sxs-lookup"><span data-stu-id="b6420-149">The template creates eight files for you:</span></span>

* <span data-ttu-id="b6420-150">Um .gitignore, personalizado para aplicativos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-150">A .gitignore, customized for ASP.NET Core applications.</span></span>
* <span data-ttu-id="b6420-151">Um arquivo Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="b6420-151">A Startup.cs file.</span></span> <span data-ttu-id="b6420-152">Contém a base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-152">This contains the basis of the application.</span></span>
* <span data-ttu-id="b6420-153">Um arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="b6420-153">A Program.cs file.</span></span> <span data-ttu-id="b6420-154">Contém o ponto de entrada do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-154">This contains the entry point of the application.</span></span>
* <span data-ttu-id="b6420-155">Um arquivo WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="b6420-155">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="b6420-156">Esse é o arquivo de compilação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-156">This is the build file for the application.</span></span>
* <span data-ttu-id="b6420-157">Um dockerfile.</span><span class="sxs-lookup"><span data-stu-id="b6420-157">A Dockerfile.</span></span> <span data-ttu-id="b6420-158">Esse script cria uma imagem do Docker para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-158">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="b6420-159">Um README.md.</span><span class="sxs-lookup"><span data-stu-id="b6420-159">A README.md.</span></span> <span data-ttu-id="b6420-160">Contém links para outros recursos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-160">This contains links to other ASP.NET Core resources.</span></span>
* <span data-ttu-id="b6420-161">Um arquivo web.config.</span><span class="sxs-lookup"><span data-stu-id="b6420-161">A web.config file.</span></span> <span data-ttu-id="b6420-162">Contém informações básicas de configuração.</span><span class="sxs-lookup"><span data-stu-id="b6420-162">This contains basic configuration information.</span></span>
* <span data-ttu-id="b6420-163">Um arquivo runtimeconfig.template.json.</span><span class="sxs-lookup"><span data-stu-id="b6420-163">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="b6420-164">Contém as configurações de depuração usadas pelos IDEs.</span><span class="sxs-lookup"><span data-stu-id="b6420-164">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="b6420-165">Agora você pode executar o aplicativo gerado pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="b6420-165">Now you can run the template generated application.</span></span> <span data-ttu-id="b6420-166">Isso é feito usando uma série de ferramentas na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="b6420-166">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="b6420-167">O comando `dotnet` executa as ferramentas necessárias para desenvolvimento em .NET.</span><span class="sxs-lookup"><span data-stu-id="b6420-167">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="b6420-168">Cada verbo executa um comando diferente</span><span class="sxs-lookup"><span data-stu-id="b6420-168">Each verb executes a different command</span></span>

<span data-ttu-id="b6420-169">A primeira etapa é restaurar todas as dependências:</span><span class="sxs-lookup"><span data-stu-id="b6420-169">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="b6420-170">A restauração do dotnet usa o gerenciador de pacotes do NuGet para instalar todos os pacotes necessários no diretório do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-170">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="b6420-171">Ele também gera um arquivo project.json.lock.</span><span class="sxs-lookup"><span data-stu-id="b6420-171">It also generates a project.json.lock file.</span></span> <span data-ttu-id="b6420-172">Esse arquivo contém informações sobre cada pacote referenciado.</span><span class="sxs-lookup"><span data-stu-id="b6420-172">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="b6420-173">Depois de restaurar todas as dependências, compile o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b6420-173">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b6420-174">E, depois de compilar o aplicativo, execute-o na linha de comando:</span><span class="sxs-lookup"><span data-stu-id="b6420-174">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="b6420-175">A configuração padrão escuta `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="b6420-175">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="b6420-176">Abra um navegador, navegue até a página e veja uma mensagem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="b6420-176">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="b6420-177">.</span><span class="sxs-lookup"><span data-stu-id="b6420-177">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="b6420-178">Anatomia de um aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b6420-178">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="b6420-179">Agora que você criou o aplicativo, vamos analisar como essa funcionalidade é implementada.</span><span class="sxs-lookup"><span data-stu-id="b6420-179">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="b6420-180">Há dois dos arquivos gerados que são particularmente interessantes neste ponto: project.json e Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="b6420-180">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="b6420-181">Project.json contém informações sobre o projeto.</span><span class="sxs-lookup"><span data-stu-id="b6420-181">Project.json contains information about the project.</span></span> <span data-ttu-id="b6420-182">Os dois nós com os quais você trabalhará com frequência são 'dependências' e 'estruturas'.</span><span class="sxs-lookup"><span data-stu-id="b6420-182">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="b6420-183">O nó dependências lista todos os pacotes necessários para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-183">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="b6420-184">No momento, este é um nó pequeno que precisa apenas dos pacotes que executam o servidor Web.</span><span class="sxs-lookup"><span data-stu-id="b6420-184">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="b6420-185">O nó 'estruturas' especifica as versões e as configurações da estrutura .NET que executará esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-185">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="b6420-186">O aplicativo é implementado em Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="b6420-186">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="b6420-187">Esse arquivo contém a classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="b6420-187">This file contains the startup class.</span></span>

<span data-ttu-id="b6420-188">Os dois métodos são chamados pela infraestrutura do ASP.NET Core para configurar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-188">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="b6420-189">O método `ConfigureServices` descreve os serviços que são necessários para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-189">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="b6420-190">Você está compilando um microsserviço enxuto, portanto, não precisa configurar dependências.</span><span class="sxs-lookup"><span data-stu-id="b6420-190">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="b6420-191">O método `Configure` configura os manipuladores para solicitações HTTP de entrada.</span><span class="sxs-lookup"><span data-stu-id="b6420-191">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="b6420-192">O modelo gera um manipulador simples que responde a qualquer solicitação com o texto "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="b6420-192">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="b6420-193">Criar um microsserviço</span><span class="sxs-lookup"><span data-stu-id="b6420-193">Build a microservice</span></span>

<span data-ttu-id="b6420-194">O serviço criado fornecerá relatórios meteorológicos de qualquer lugar do mundo.</span><span class="sxs-lookup"><span data-stu-id="b6420-194">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="b6420-195">Em um aplicativo de produção, você chamaria algum serviço para obter os dados meteorológicos.</span><span class="sxs-lookup"><span data-stu-id="b6420-195">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="b6420-196">Em nosso exemplo, geraremos uma previsão do tempo aleatória.</span><span class="sxs-lookup"><span data-stu-id="b6420-196">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="b6420-197">Há várias tarefas que você precisará executar para implementar nosso serviço meteorológico aleatório:</span><span class="sxs-lookup"><span data-stu-id="b6420-197">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="b6420-198">Analise a solicitação de entrada para ler a latitude e a longitude.</span><span class="sxs-lookup"><span data-stu-id="b6420-198">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="b6420-199">Gere alguns dados de previsão aleatórios.</span><span class="sxs-lookup"><span data-stu-id="b6420-199">Generate some random forecast data.</span></span>
* <span data-ttu-id="b6420-200">Converta esses dados de previsão aleatórios de objetos C# para pacotes JSON.</span><span class="sxs-lookup"><span data-stu-id="b6420-200">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="b6420-201">Defina o cabeçalho de resposta para indicar que o serviço retorna JSON.</span><span class="sxs-lookup"><span data-stu-id="b6420-201">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="b6420-202">Escreva a resposta.</span><span class="sxs-lookup"><span data-stu-id="b6420-202">Write the response.</span></span>

<span data-ttu-id="b6420-203">As próximas seções orientarão você por cada uma dessas etapas.</span><span class="sxs-lookup"><span data-stu-id="b6420-203">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="b6420-204">Análise da cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="b6420-204">Parsing the Query String.</span></span>

<span data-ttu-id="b6420-205">Você começará pela análise de cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="b6420-205">You'll begin by parsing the query string.</span></span> <span data-ttu-id="b6420-206">O serviço aceitará os argumentos 'lat' e 'long' na cadeia de consulta nesta forma:</span><span class="sxs-lookup"><span data-stu-id="b6420-206">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="b6420-207">Todas as alterações que você precisa fazer estão na expressão lambda definida como o argumento `app.Run` em sua classe de inicialização.</span><span class="sxs-lookup"><span data-stu-id="b6420-207">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="b6420-208">O argumento na expressão lambda é o `HttpContext` para a solicitação.</span><span class="sxs-lookup"><span data-stu-id="b6420-208">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="b6420-209">Uma de suas propriedades é o objeto `Request`.</span><span class="sxs-lookup"><span data-stu-id="b6420-209">One of its properties is the `Request` object.</span></span> <span data-ttu-id="b6420-210">O objeto `Request` tem uma propriedade `Query` que contém um dicionário com todos os valores na cadeia de consulta da solicitação.</span><span class="sxs-lookup"><span data-stu-id="b6420-210">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="b6420-211">A primeira adição serve para encontrar os valores de latitude e longitude:</span><span class="sxs-lookup"><span data-stu-id="b6420-211">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="b6420-212">Os valores de dicionário de Consulta são do tipo `StringValue`.</span><span class="sxs-lookup"><span data-stu-id="b6420-212">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="b6420-213">Esse tipo pode conter uma coleção de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6420-213">That type can contain a collection of strings.</span></span> <span data-ttu-id="b6420-214">Para o serviço meteorológico, cada valor é uma cadeia de caracteres única.</span><span class="sxs-lookup"><span data-stu-id="b6420-214">For your weather service, each value is a single string.</span></span> <span data-ttu-id="b6420-215">É por isso que há a chamada para `FirstOrDefault()` no código acima.</span><span class="sxs-lookup"><span data-stu-id="b6420-215">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="b6420-216">Em seguida, você precisa converter as cadeias de caracteres em doubles.</span><span class="sxs-lookup"><span data-stu-id="b6420-216">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="b6420-217">O método que você usará para converter a cadeia de caracteres em um double é `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="b6420-217">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="b6420-218">Esse método utiliza parâmetros C# para indicar se a cadeia de caracteres de entrada pode ser convertida em um double.</span><span class="sxs-lookup"><span data-stu-id="b6420-218">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="b6420-219">Se a cadeia de caracteres for uma representação válida de um double, o método retornará true, e o argumento `result` conterá o valor.</span><span class="sxs-lookup"><span data-stu-id="b6420-219">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="b6420-220">Se a cadeia de caracteres não representar um double válida, o método retornará false.</span><span class="sxs-lookup"><span data-stu-id="b6420-220">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="b6420-221">Adapte essa API com o uso de um *método de extensão* que retorna um *double anulável*.</span><span class="sxs-lookup"><span data-stu-id="b6420-221">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="b6420-222">O *tipo de valor anulável* é um tipo que representa algum tipo de valor e também pode apresentar um valor ausente ou nulo.</span><span class="sxs-lookup"><span data-stu-id="b6420-222">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="b6420-223">Um tipo que permite valor nulo é representado por meio do acréscimo do caractere `?` à declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="b6420-223">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="b6420-224">Métodos de extensão são métodos definidos como estáticos, mas ao adicionar o modificador `this` no primeiro parâmetro é possível chamá-los como se fossem membros dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b6420-224">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="b6420-225">Os métodos de extensão só podem ser definidos em classes estáticas.</span><span class="sxs-lookup"><span data-stu-id="b6420-225">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="b6420-226">Confira aqui a definição da classe que contém o método de extensão para análise:</span><span class="sxs-lookup"><span data-stu-id="b6420-226">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="b6420-227">A expressão `default(double?)` retorna o valor padrão para o tipo `double?`.</span><span class="sxs-lookup"><span data-stu-id="b6420-227">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="b6420-228">O valor padrão é o valor nulo (ou ausente).</span><span class="sxs-lookup"><span data-stu-id="b6420-228">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="b6420-229">Use esse método de extensão para converter os argumentos da cadeia de caracteres de consulta no tipo double:</span><span class="sxs-lookup"><span data-stu-id="b6420-229">You can use this extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="b6420-230">Para testar o código de análise com facilidade, atualize a resposta para incluir os valores dos argumentos:</span><span class="sxs-lookup"><span data-stu-id="b6420-230">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="b6420-231">Neste ponto, você pode executar o aplicativo Web e verificar se o código de análise está funcionando.</span><span class="sxs-lookup"><span data-stu-id="b6420-231">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="b6420-232">Adicione valores à solicitação da Web em um navegador e você verá os resultados atualizados.</span><span class="sxs-lookup"><span data-stu-id="b6420-232">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="b6420-233">Compilar uma previsão do tempo aleatória</span><span class="sxs-lookup"><span data-stu-id="b6420-233">Build a random weather forecast</span></span>

<span data-ttu-id="b6420-234">A próxima tarefa é compilar uma previsão do tempo aleatória.</span><span class="sxs-lookup"><span data-stu-id="b6420-234">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="b6420-235">Vamos começar com um contêiner de dados com os valores que você gostaria para uma previsão do tempo:</span><span class="sxs-lookup"><span data-stu-id="b6420-235">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

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

<span data-ttu-id="b6420-236">Em seguida, compile um construtor que define aleatoriamente os valores.</span><span class="sxs-lookup"><span data-stu-id="b6420-236">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="b6420-237">Este construtor usa os valores de latitude e longitude para propagar o Gerador de número aleatório.</span><span class="sxs-lookup"><span data-stu-id="b6420-237">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="b6420-238">Isso significa que a previsão para o mesmo local é a mesma.</span><span class="sxs-lookup"><span data-stu-id="b6420-238">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="b6420-239">Se você alterar os argumentos para a latitude e longitude, obterá uma previsão diferente (porque começou com uma propagação diferente.)</span><span class="sxs-lookup"><span data-stu-id="b6420-239">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="b6420-240">Agora você pode gerar a previsão de cinco dias em seu método de resposta:</span><span class="sxs-lookup"><span data-stu-id="b6420-240">You can now generate the 5-day forecast in your response method:</span></span>

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a><span data-ttu-id="b6420-241">Compile a resposta JSON.</span><span class="sxs-lookup"><span data-stu-id="b6420-241">Build the JSON response.</span></span>

<span data-ttu-id="b6420-242">A tarefa de código final no servidor é converter a matriz WeatherReport em um pacote JSON e enviá-lo de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b6420-242">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="b6420-243">Vamos começar criando o pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="b6420-243">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="b6420-244">Você adicionará o Serializador de JSON da NewtonSoft à lista de dependências.</span><span class="sxs-lookup"><span data-stu-id="b6420-244">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="b6420-245">Faça isso usando a CLI `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="b6420-245">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="b6420-246">Em seguida, use a classe `JsonConvert` para gravar o objeto em uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="b6420-246">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="b6420-247">O código acima converte o objeto de previsão (uma lista de `WeatherForecast` objetos) em um pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="b6420-247">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="b6420-248">Após a construção do pacote de resposta, defina o tipo de conteúdo como `application/json` e grave a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6420-248">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="b6420-249">Agora, o aplicativo é executado e retorna previsões aleatórias.</span><span class="sxs-lookup"><span data-stu-id="b6420-249">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="b6420-250">Criar uma imagem do Docker</span><span class="sxs-lookup"><span data-stu-id="b6420-250">Build a Docker image</span></span>

<span data-ttu-id="b6420-251">Nossa tarefa final é executar o aplicativo no Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-251">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="b6420-252">Vamos criar um contêiner do Docker que executa uma imagem do Docker que representa nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-252">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="b6420-253">Uma ***imagem do Docker*** é um arquivo que define o ambiente para execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-253">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="b6420-254">Um ***Contêiner do Docker*** representa uma instância em execução de uma imagem do Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-254">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="b6420-255">Por analogia, você pode considerar a *imagem do Docker* como uma *classe* e o *Contêiner do Docker* como um objeto ou uma instância dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b6420-255">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="b6420-256">O Dockerfile criado pelo modelo ASP.NET servirá para nossos objetivos.</span><span class="sxs-lookup"><span data-stu-id="b6420-256">The Dockerfile created by the ASP.NET template will serve for our purposes.</span></span> <span data-ttu-id="b6420-257">Vamos analisar o conteúdo.</span><span class="sxs-lookup"><span data-stu-id="b6420-257">Let's go over its contents.</span></span>

<span data-ttu-id="b6420-258">A primeira linha especifica a imagem de origem:</span><span class="sxs-lookup"><span data-stu-id="b6420-258">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="b6420-259">O Docker permite que você configure uma imagem de máquina com base em um modelo de origem.</span><span class="sxs-lookup"><span data-stu-id="b6420-259">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="b6420-260">Isso significa que não é necessário fornecer todos os parâmetros da máquina ao iniciar, você só precisa fornecer as alterações.</span><span class="sxs-lookup"><span data-stu-id="b6420-260">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="b6420-261">As alterações feitas aqui servem para incluir nosso aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-261">The changes here will be to include our application.</span></span>

<span data-ttu-id="b6420-262">Neste primeiro exemplo, usaremos a versão `1.1-sdk-msbuild` da imagem do dotnet.</span><span class="sxs-lookup"><span data-stu-id="b6420-262">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="b6420-263">Essa é a maneira mais fácil de criar um ambiente funcional do Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-263">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="b6420-264">Essa imagem inclui o tempo de execução do dotnet core e o SDK do dotnet.</span><span class="sxs-lookup"><span data-stu-id="b6420-264">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="b6420-265">Isso facilita o início e a compilação, mas cria uma imagem maior.</span><span class="sxs-lookup"><span data-stu-id="b6420-265">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="b6420-266">As próximas cinco linhas configuram e compilam seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b6420-266">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroService.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b6420-267">Isso copiará o arquivo de projeto do diretório atual para a VM do Docker e restaurará todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="b6420-267">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="b6420-268">Usar a CLI do dotnet significa que a imagem do Docker deve incluir o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6420-268">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="b6420-269">Depois disso, o restante de seu aplicativo será copiado e o comando publish do dotnet compilará e empacotará seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b6420-269">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="b6420-270">A linha final do arquivo executa o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="b6420-270">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroService.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="b6420-271">Essa porta configurada é referenciada no argumento `--server.urls` para `dotnet` na última linha do Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="b6420-271">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="b6420-272">O comando `ENTRYPOINT` informa ao Docker qual comando e quais opções de linha de comando iniciarão o serviço.</span><span class="sxs-lookup"><span data-stu-id="b6420-272">The `ENTRYPOINT` command informs Docker what command and command-line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="b6420-273">Crie e execute a imagem em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-273">Building and running the image in a container.</span></span>

<span data-ttu-id="b6420-274">Vamos compilar uma imagem e executar o serviço dentro de um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="b6420-274">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="b6420-275">Você não quer que todos os arquivos de seu diretório local sejam copiados na imagem.</span><span class="sxs-lookup"><span data-stu-id="b6420-275">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="b6420-276">Em vez disso, compile o aplicativo no contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-276">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="b6420-277">Você criará um arquivo `.dockerignore` para especificar os diretórios que não são copiados na imagem.</span><span class="sxs-lookup"><span data-stu-id="b6420-277">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="b6420-278">Você não que copiar nenhum ativo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b6420-278">You don't want any of the build assets copied.</span></span> <span data-ttu-id="b6420-279">Especifique os diretórios de compilação e publicação no arquivo `.dockerignore`:</span><span class="sxs-lookup"><span data-stu-id="b6420-279">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="b6420-280">Crie a imagem usando o comando `docker build`.</span><span class="sxs-lookup"><span data-stu-id="b6420-280">You build the image using the `docker build` command.</span></span> <span data-ttu-id="b6420-281">Execute o seguinte comando no diretório que contém seu código.</span><span class="sxs-lookup"><span data-stu-id="b6420-281">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="b6420-282">Esse comando compila a imagem do contêiner com base em todas as informações de seu Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="b6420-282">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="b6420-283">O argumento `-t` fornece uma marca, ou nome, para essa imagem de contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-283">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="b6420-284">Na linha de comando acima, a marca usada para o contêiner do Docker é `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="b6420-284">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="b6420-285">Quando esse comando for concluído, você terá um contêiner pronto para executar seu novo serviço.</span><span class="sxs-lookup"><span data-stu-id="b6420-285">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="b6420-286">Execute o seguinte comando para iniciar o contêiner e também o serviço:</span><span class="sxs-lookup"><span data-stu-id="b6420-286">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="b6420-287">A opção `-d` representa a execução do contêiner desanexado do terminal atual.</span><span class="sxs-lookup"><span data-stu-id="b6420-287">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="b6420-288">Isso significa que você não verá a saída do comando em seu terminal.</span><span class="sxs-lookup"><span data-stu-id="b6420-288">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="b6420-289">A opção `-p` indica o mapeamento de porta entre o serviço e o host.</span><span class="sxs-lookup"><span data-stu-id="b6420-289">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="b6420-290">Aqui ela informa que qualquer solicitação de entrada na porta 80 deve ser encaminhada para a porta 5000 no contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-290">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="b6420-291">5000 corresponde à porta na qual o serviço está escutando a partir dos argumentos de linha de comando especificados no Dockerfile acima.</span><span class="sxs-lookup"><span data-stu-id="b6420-291">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="b6420-292">O argumento `--name` nomeia o contêiner em execução.</span><span class="sxs-lookup"><span data-stu-id="b6420-292">The `--name` argument names your running container.</span></span> <span data-ttu-id="b6420-293">É um nome conveniente que você pode usar para trabalhar com esse contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-293">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="b6420-294">É possível ver se a imagem está sendo executada verificando o comando:</span><span class="sxs-lookup"><span data-stu-id="b6420-294">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="b6420-295">Se o contêiner estiver em execução, você verá uma linha que o lista nos processos em execução.</span><span class="sxs-lookup"><span data-stu-id="b6420-295">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="b6420-296">(Pode ser o único).</span><span class="sxs-lookup"><span data-stu-id="b6420-296">(It may be the only one).</span></span>

<span data-ttu-id="b6420-297">Teste seu serviço abrindo um navegador, navegando até localhost e especificando uma latitude e longitude:</span><span class="sxs-lookup"><span data-stu-id="b6420-297">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="b6420-298">Anexar um contêiner em execução</span><span class="sxs-lookup"><span data-stu-id="b6420-298">Attaching to a running container</span></span>

<span data-ttu-id="b6420-299">Quando você executa o serviço em uma janela de comando, pode ver informações de diagnóstico impressas para cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="b6420-299">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="b6420-300">Você não vê essas informações quando o contêiner está sendo executado no modo desconectado.</span><span class="sxs-lookup"><span data-stu-id="b6420-300">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="b6420-301">O comando attach do Docker permite que você anexe a um contêiner em execução para que você possa ver as informações de log.</span><span class="sxs-lookup"><span data-stu-id="b6420-301">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="b6420-302">Execute este comando a partir de uma janela de comando:</span><span class="sxs-lookup"><span data-stu-id="b6420-302">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="b6420-303">O argumento `--sig-proxy=false` significa que os comandos `Ctrl-C` não são enviados ao processo do contêiner, mas, em vez disso, interrompem o comando `docker attach`.</span><span class="sxs-lookup"><span data-stu-id="b6420-303">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="b6420-304">O argumento final é o nome fornecido ao contêiner no comando `docker run`.</span><span class="sxs-lookup"><span data-stu-id="b6420-304">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="b6420-305">Use também a ID de contêiner atribuída pelo Docker para se referir a qualquer contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-305">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="b6420-306">Se você não tiver especificado um nome para seu contêiner no `docker run`, use a id do contêiner.</span><span class="sxs-lookup"><span data-stu-id="b6420-306">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="b6420-307">Abra um navegador e navegue até seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b6420-307">Open a browser and navigate to your service.</span></span> <span data-ttu-id="b6420-308">Você verá as mensagens de diagnóstico nas janelas de comando do contêiner anexado em execução.</span><span class="sxs-lookup"><span data-stu-id="b6420-308">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="b6420-309">Pressione `Ctrl-C` para interromper o processo de conexão.</span><span class="sxs-lookup"><span data-stu-id="b6420-309">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="b6420-310">Quando você terminar de trabalhar com seu contêiner, interrompa-o:</span><span class="sxs-lookup"><span data-stu-id="b6420-310">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="b6420-311">O contêiner e a imagem ainda estão disponíveis para a reinicialização.</span><span class="sxs-lookup"><span data-stu-id="b6420-311">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="b6420-312">Se você quiser remover o contêiner do seu computador, use este comando:</span><span class="sxs-lookup"><span data-stu-id="b6420-312">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="b6420-313">Se você quiser remover imagens não usadas do seu computador, use este comando:</span><span class="sxs-lookup"><span data-stu-id="b6420-313">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="b6420-314">Conclusão</span><span class="sxs-lookup"><span data-stu-id="b6420-314">Conclusion</span></span> 

<span data-ttu-id="b6420-315">Neste tutorial, você criou um microsserviço do ASP.NET Core e adicionou alguns recursos simples.</span><span class="sxs-lookup"><span data-stu-id="b6420-315">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="b6420-316">Você criou uma imagem de contêiner do Docker para o serviço e executou o contêiner no computador.</span><span class="sxs-lookup"><span data-stu-id="b6420-316">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="b6420-317">Você anexou uma janela de terminal ao serviço e viu as mensagens de diagnóstico de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b6420-317">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="b6420-318">Durante o tutorial, você viu vários recursos da linguagem C# em ação.</span><span class="sxs-lookup"><span data-stu-id="b6420-318">Along the way, you saw several features of the C# language in action.</span></span>
