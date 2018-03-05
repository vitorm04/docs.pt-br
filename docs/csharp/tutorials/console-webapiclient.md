---
title: Cria um cliente REST usando .NET Core
description: "Este tutorial ensina vários recursos no .NET Core e da linguagem C#."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 22391c4db3027c0fad2115c767b5e2808fee28a0
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="rest-client"></a><span data-ttu-id="b292e-104">Cliente REST</span><span class="sxs-lookup"><span data-stu-id="b292e-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="b292e-105">Introdução</span><span class="sxs-lookup"><span data-stu-id="b292e-105">Introduction</span></span>
<span data-ttu-id="b292e-106">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="b292e-107">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="b292e-107">You’ll learn:</span></span>
*   <span data-ttu-id="b292e-108">As noções básicas da CLI (Interface de Linha de Comando) do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b292e-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="b292e-109">Uma visão geral dos recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="b292e-110">Gerenciamento de dependências com o NuGet</span><span class="sxs-lookup"><span data-stu-id="b292e-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="b292e-111">Comunicações HTTP</span><span class="sxs-lookup"><span data-stu-id="b292e-111">HTTP Communications</span></span>
*   <span data-ttu-id="b292e-112">Processamento de informações de JSON</span><span class="sxs-lookup"><span data-stu-id="b292e-112">Processing JSON information</span></span>
*   <span data-ttu-id="b292e-113">Gerenciamento de configuração com Atributos.</span><span class="sxs-lookup"><span data-stu-id="b292e-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="b292e-114">Você compilará um aplicativo que emite solicitações HTTP para um serviço REST no GitHub.</span><span class="sxs-lookup"><span data-stu-id="b292e-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="b292e-115">Você lerá informações no formato JSON e converterá esse pacote JSON em objetos C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="b292e-116">Por fim, você verá como trabalhar com objetos C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="b292e-117">Há vários recursos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="b292e-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="b292e-118">Vamos compilá-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="b292e-118">Let’s build them one by one.</span></span>

<span data-ttu-id="b292e-119">Se preferir acompanhar com o [exemplo final](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) para esse tópico, você poderá baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="b292e-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="b292e-120">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="b292e-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b292e-121">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b292e-121">Prerequisites</span></span>
<span data-ttu-id="b292e-122">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b292e-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="b292e-123">Você encontrará as instruções de instalação na página do [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="b292e-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="b292e-124">Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="b292e-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="b292e-125">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="b292e-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="b292e-126">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b292e-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="b292e-127">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="b292e-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="b292e-128">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b292e-128">Create the Application</span></span>
<span data-ttu-id="b292e-129">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b292e-129">The first step is to create a new application.</span></span> <span data-ttu-id="b292e-130">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b292e-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="b292e-131">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b292e-131">Make that the current directory.</span></span> <span data-ttu-id="b292e-132">Digite o comando `dotnet new console` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="b292e-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="b292e-133">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="b292e-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="b292e-134">Antes de começar as modificações, vamos percorrer as etapas para execução do aplicativo simples Hello World.</span><span class="sxs-lookup"><span data-stu-id="b292e-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="b292e-135">Depois de criar o aplicativo, digite `dotnet restore` ([veja a observação](#dotnet-restore-note)) no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="b292e-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="b292e-136">Esse comando executa o processo de restauração do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="b292e-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="b292e-137">O NuGet é um gerenciador de pacotes do .NET.</span><span class="sxs-lookup"><span data-stu-id="b292e-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="b292e-138">Esse comando baixa qualquer uma das dependências ausentes para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b292e-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="b292e-139">Como esse é um novo projeto, nenhuma das dependências foram aplicadas, portanto, a primeira execução baixará a estrutura do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b292e-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="b292e-140">Após essa etapa inicial, você só precisará executar o `dotnet restore` ([veja a observação](#dotnet-restore-note)) ao adicionar novos pacotes dependentes, ou atualizar as versões de qualquer uma de suas dependências.</span><span class="sxs-lookup"><span data-stu-id="b292e-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="b292e-141">Depois de restaurar os pacotes, execute `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="b292e-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="b292e-142">Isso executa o mecanismo de compilação e cria seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b292e-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="b292e-143">Por fim, execute `dotnet run` para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b292e-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="b292e-144">Adicionar novas dependências</span><span class="sxs-lookup"><span data-stu-id="b292e-144">Adding New Dependencies</span></span>
<span data-ttu-id="b292e-145">Uma das metas principais de design para o .NET Core é minimizar o tamanho da instalação da estrutura do .NET.</span><span class="sxs-lookup"><span data-stu-id="b292e-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="b292e-146">A estrutura do aplicativo .NET Core contém apenas os elementos mais comuns da estrutura completa do .NET.</span><span class="sxs-lookup"><span data-stu-id="b292e-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="b292e-147">Se um aplicativo precisar de mais bibliotecas para alguns de seus recursos, adicione essas dependências ao seu arquivo de projeto de C# (\*.csproj).</span><span class="sxs-lookup"><span data-stu-id="b292e-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="b292e-148">Para nosso exemplo, você precisará adicionar o pacote `System.Runtime.Serialization.Json` para que seu aplicativo possa processar as respostas em JSON.</span><span class="sxs-lookup"><span data-stu-id="b292e-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="b292e-149">Abra seu arquivo de projeto `csproj`.</span><span class="sxs-lookup"><span data-stu-id="b292e-149">Open your `csproj` project file.</span></span> <span data-ttu-id="b292e-150">A primeira linha do arquivo deve aparecer assim:</span><span class="sxs-lookup"><span data-stu-id="b292e-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="b292e-151">Adicione o seguinte logo após esta linha:</span><span class="sxs-lookup"><span data-stu-id="b292e-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="b292e-152">A maioria dos editores de código fornece conclusão para versões diferentes dessas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="b292e-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="b292e-153">Convém usar a versão mais recente de qualquer pacote que você adicionar.</span><span class="sxs-lookup"><span data-stu-id="b292e-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="b292e-154">No entanto, é importante ter certeza de que as versões de todos os pacotes correspondam, e que também correspondam à versão da estrutura de aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b292e-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="b292e-155">Após fazer essas alterações, execute `dotnet restore` ([veja a observação](#dotnet-restore-note)) novamente para que o pacote seja instalado em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="b292e-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="b292e-156">Como fazer solicitações da Web</span><span class="sxs-lookup"><span data-stu-id="b292e-156">Making Web Requests</span></span>
<span data-ttu-id="b292e-157">Agora você está pronto para começar a obter dados da Web.</span><span class="sxs-lookup"><span data-stu-id="b292e-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="b292e-158">Neste aplicativo, você lerá informações da [API do GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="b292e-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="b292e-159">Vamos ler informações sobre os projetos em [.NET Foundation](http://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="b292e-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="b292e-160">Comece fazendo a solicitação à API do GitHub para recuperar informações sobre os projetos.</span><span class="sxs-lookup"><span data-stu-id="b292e-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="b292e-161">Você usará o ponto de extremidade: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="b292e-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="b292e-162">Você quer obter todas as informações sobre esses projetos, portanto, use uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="b292e-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="b292e-163">O navegador também usa solicitações HTTP GET, para que você possa colar essa URL em seu navegador e ver as informações que receberá.</span><span class="sxs-lookup"><span data-stu-id="b292e-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="b292e-164">Use a classe <xref:System.Net.Http.HttpClient> para fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="b292e-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="b292e-165">Como todas as APIs .NET modernas, a <xref:System.Net.Http.HttpClient> oferece suporte apenas aos métodos assíncronos para suas APIs de longa execução.</span><span class="sxs-lookup"><span data-stu-id="b292e-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="b292e-166">Comece criando um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b292e-166">Start by making an async method.</span></span> <span data-ttu-id="b292e-167">Você preencherá a implementação à medida que compila a funcionalidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b292e-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="b292e-168">Comece abrindo o arquivo `program.cs` no diretório do projeto e adicionando o seguinte método à classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="b292e-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="b292e-169">Será necessário adicionar uma instrução `using` na parte superior de seu método `Main` para que o compilador de C# reconheça o tipo <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="b292e-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="b292e-170">Se você compilar o projeto neste momento, receberá um aviso gerado para esse método, pois ele não contém operadores `await` e executará de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="b292e-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="b292e-171">Ignore isso por enquanto. Adicione os operadores `await` à medida que você preenche o método.</span><span class="sxs-lookup"><span data-stu-id="b292e-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="b292e-172">Em seguida, renomeie o namespace definido na instrução `namespace`, alterando o padrão de `ConsoleApp` para `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="b292e-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="b292e-173">Posteriormente, definiremos uma classe `repo` neste namespace.</span><span class="sxs-lookup"><span data-stu-id="b292e-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="b292e-174">Em seguida, atualize o método `Main` para chamar esse método.</span><span class="sxs-lookup"><span data-stu-id="b292e-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="b292e-175">O método `ProcessRepositories` retorna uma Tarefa, e você não deve sair do programa antes da conclusão dessa tarefa.</span><span class="sxs-lookup"><span data-stu-id="b292e-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="b292e-176">Portanto, use o método `Wait` para bloquear e esperar a conclusão da tarefa:</span><span class="sxs-lookup"><span data-stu-id="b292e-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="b292e-177">Agora, você tem um programa que não faz nada, mas o faz de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="b292e-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="b292e-178">Vamos melhorar isso.</span><span class="sxs-lookup"><span data-stu-id="b292e-178">Let's improve it.</span></span>

<span data-ttu-id="b292e-179">Primeiro você precisa de um objeto que é capaz de recuperar dados da Web; você pode usar um <xref:System.Net.Http.HttpClient> para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b292e-179">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="b292e-180">Esse objeto manipula a solicitação e as respostas.</span><span class="sxs-lookup"><span data-stu-id="b292e-180">This object handles the request and the responses.</span></span> <span data-ttu-id="b292e-181">Crie uma única instância desse tipo na classe `Program` dentro do arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="b292e-181">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

 <span data-ttu-id="b292e-182">Vamos voltar ao método `ProcessRepositories` e preencher uma primeira versão dele:</span><span class="sxs-lookup"><span data-stu-id="b292e-182">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="b292e-183">Também será necessário adicionar duas instruções using novas na parte superior do arquivo para que isso seja compilado:</span><span class="sxs-lookup"><span data-stu-id="b292e-183">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="b292e-184">A primeira versão faz uma solicitação da Web para ler a lista de todos os repositórios na organização dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="b292e-184">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="b292e-185">(A ID do gitHub para o .NET Foundation é 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="b292e-185">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="b292e-186">As primeiras linhas configuram o <xref:System.Net.Http.HttpClient> para essa solicitação.</span><span class="sxs-lookup"><span data-stu-id="b292e-186">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="b292e-187">Primeiro, ele é configurado para aceitar as respostas JSON do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b292e-187">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="b292e-188">Esse formato é simplesmente JSON.</span><span class="sxs-lookup"><span data-stu-id="b292e-188">This format is simply JSON.</span></span> <span data-ttu-id="b292e-189">A próxima linha adiciona um cabeçalho de agente do usuário para todas as solicitações deste objeto.</span><span class="sxs-lookup"><span data-stu-id="b292e-189">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="b292e-190">Esses dois cabeçalhos são verificados pelo código do servidor GitHub e são necessários para recuperar informações do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b292e-190">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="b292e-191">Depois de configurar o <xref:System.Net.Http.HttpClient>, faça uma solicitação da Web e recupere a resposta.</span><span class="sxs-lookup"><span data-stu-id="b292e-191">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="b292e-192">Nesta primeira versão, você usa o método de conveniência <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b292e-192">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="b292e-193">Este método prático inicia uma tarefa que faz a solicitação da Web e, depois, quando a solicitação retornar, ele lê o fluxo de resposta e extrai o conteúdo do fluxo.</span><span class="sxs-lookup"><span data-stu-id="b292e-193">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="b292e-194">O corpo da resposta retorna como um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b292e-194">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="b292e-195">A cadeia de caracteres fica disponível após a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="b292e-195">The string is available when the task completes.</span></span> 

<span data-ttu-id="b292e-196">As duas últimas linhas desse método aguardam a tarefa e, depois, imprimem a resposta no console.</span><span class="sxs-lookup"><span data-stu-id="b292e-196">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="b292e-197">Compilar o aplicativo e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="b292e-197">Build the app, and run it.</span></span> <span data-ttu-id="b292e-198">O aviso de compilação desapareceu, pois agora o `ProcessRepositories` contêm um operador `await`.</span><span class="sxs-lookup"><span data-stu-id="b292e-198">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="b292e-199">Você verá uma longa exibição do texto formatado em JSON.</span><span class="sxs-lookup"><span data-stu-id="b292e-199">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="b292e-200">Processar o resultado JSON</span><span class="sxs-lookup"><span data-stu-id="b292e-200">Processing the JSON Result</span></span>

<span data-ttu-id="b292e-201">Neste ponto, você já escreveu o código para recuperar uma resposta de um servidor da Web e exibiu o texto contido nessa resposta.</span><span class="sxs-lookup"><span data-stu-id="b292e-201">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="b292e-202">Agora, vamos converter essa resposta em JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-202">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="b292e-203">O serializador JSON converte os dados em JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-203">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="b292e-204">A primeira tarefa serve para definir um tipo de classe em C# para conter as informações usadas nessa resposta.</span><span class="sxs-lookup"><span data-stu-id="b292e-204">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="b292e-205">Vamos compilar isso lentamente, então comece com um tipo C# simples que contém o nome do repositório:</span><span class="sxs-lookup"><span data-stu-id="b292e-205">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

<span data-ttu-id="b292e-206">Coloque o código acima em um novo arquivo chamado 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="b292e-206">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="b292e-207">Esta versão da classe representa o caminho mais simples para processar os dados em JSON.</span><span class="sxs-lookup"><span data-stu-id="b292e-207">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="b292e-208">O nome da classe e o nome do membro corresponderem aos nomes usados no pacote JSON, em vez de seguir as convenções em C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-208">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="b292e-209">Corrija isso mais tarde fornecendo alguns atributos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b292e-209">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="b292e-210">Essa classe demonstra outro recurso importante de serialização e desserialização em JSON: nem todos os campos no pacote JSON fazem parte dessa classe.</span><span class="sxs-lookup"><span data-stu-id="b292e-210">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="b292e-211">O serializador JSON ignorará as informações que não estão incluídas no tipo de classe que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="b292e-211">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="b292e-212">Esse recurso facilita a criação de tipos que funcionam apenas com um subconjunto dos campos no pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="b292e-212">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="b292e-213">Agora que você criou o tipo, vamos desserializá-lo.</span><span class="sxs-lookup"><span data-stu-id="b292e-213">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="b292e-214">Você precisará criar um objeto <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b292e-214">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="b292e-215">Este objeto deve saber o tipo de CLR esperada para o pacote JSON que ele recupera.</span><span class="sxs-lookup"><span data-stu-id="b292e-215">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="b292e-216">O pacote do GitHub contém uma sequência de repositórios, então um `List<repo>` é o tipo correto.</span><span class="sxs-lookup"><span data-stu-id="b292e-216">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="b292e-217">Adicione a seguinte linha ao seu método `ProcessRepositories`:</span><span class="sxs-lookup"><span data-stu-id="b292e-217">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="b292e-218">Você está usando dois novos namespaces, portanto será necessário adicioná-los também:</span><span class="sxs-lookup"><span data-stu-id="b292e-218">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="b292e-219">Em seguida, você usará o serializador para converter JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-219">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="b292e-220">Substitua a chamada para <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> em seu método `ProcessRepositories` pelas duas linhas a seguir:</span><span class="sxs-lookup"><span data-stu-id="b292e-220">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="b292e-221">Observe que agora você está usando <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> em vez de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="b292e-221">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="b292e-222">O serializador usa um fluxo, em vez de uma cadeia de caracteres, como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="b292e-222">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="b292e-223">Vamos explicar alguns recursos da linguagem C# que estão sendo usados na segunda linha acima.</span><span class="sxs-lookup"><span data-stu-id="b292e-223">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="b292e-224">O argumento <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> é uma expressão `await`.</span><span class="sxs-lookup"><span data-stu-id="b292e-224">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="b292e-225">Expressões await podem aparecer em quase todo lugar em seu código, apesar de que até o momento, você apenas as viu como parte de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="b292e-225">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="b292e-226">Em segundo lugar, o operador `as` converte do tipo de tempo de compilação do `object` para `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="b292e-226">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="b292e-227">A declaração de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declara que ele retorna um objeto do tipo <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b292e-227">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b292e-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> retornará o tipo especificado no momento da construção (`List<repo>` neste tutorial).</span><span class="sxs-lookup"><span data-stu-id="b292e-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="b292e-229">Se a conversão não tiver êxito, o operador `as` será avaliado com `null`, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b292e-229">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="b292e-230">Você está quase terminando esta seção.</span><span class="sxs-lookup"><span data-stu-id="b292e-230">You're almost done with this section.</span></span> <span data-ttu-id="b292e-231">Agora que você converteu o JSON em objetos C#, vamos exibir o nome de cada repositório.</span><span class="sxs-lookup"><span data-stu-id="b292e-231">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="b292e-232">Substitua as linhas que mostram:</span><span class="sxs-lookup"><span data-stu-id="b292e-232">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="b292e-233">pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="b292e-233">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="b292e-234">Compile e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b292e-234">Compile and run the application.</span></span> <span data-ttu-id="b292e-235">Ele imprimirá os nomes dos repositórios que fazem parte do .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="b292e-235">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="b292e-236">Controle da serialização</span><span class="sxs-lookup"><span data-stu-id="b292e-236">Controlling Serialization</span></span>

<span data-ttu-id="b292e-237">Antes de adicionar mais recursos, vamos abordar o tipo `repo` e fazê-lo seguir convenções mais padrão de C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-237">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="b292e-238">Faça isso anotando a tipo `repo` com *atributos* que controlem o modo como o serializador JSON funciona.</span><span class="sxs-lookup"><span data-stu-id="b292e-238">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="b292e-239">Em seu caso, você usará esses atributos para definir um mapeamento entre os nomes de chave JSON e os nomes de classe e de membros de C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-239">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="b292e-240">Os dois atributos usados são `DataContract` e `DataMember`.</span><span class="sxs-lookup"><span data-stu-id="b292e-240">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="b292e-241">Por convenção, todas as classes de atributo terminam com o sufixo `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="b292e-241">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="b292e-242">No entanto, não é necessário usar esse sufixo ao aplicar um atributo.</span><span class="sxs-lookup"><span data-stu-id="b292e-242">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="b292e-243">Os atributos `DataContract` e `DataMember` são atributos em uma biblioteca diferente, então você precisará adicionar essa biblioteca ao seu arquivo de projeto C# como uma dependência.</span><span class="sxs-lookup"><span data-stu-id="b292e-243">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="b292e-244">Adicione a seguinte linha à seção `<ItemGroup>` de seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="b292e-244">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="b292e-245">Depois de salvar o arquivo, execute `dotnet restore` ([veja a observação](#dotnet-restore-note)) para recuperar esse pacote.</span><span class="sxs-lookup"><span data-stu-id="b292e-245">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="b292e-246">Em seguida, abra o arquivo `repo.cs`.</span><span class="sxs-lookup"><span data-stu-id="b292e-246">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="b292e-247">Vamos alterar o nome para usar Pascal Case e soletrar o nome `Repository` completo.</span><span class="sxs-lookup"><span data-stu-id="b292e-247">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="b292e-248">Ainda queremos mapear os nós de 'repositório' de JSON para esse tipo, então será necessário adicionar o atributo `DataContract` à declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="b292e-248">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="b292e-249">Você definirá a propriedade `Name` do atributo como o nome de nós de JSON mapeados para esse tipo:</span><span class="sxs-lookup"><span data-stu-id="b292e-249">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="b292e-250">O <xref:System.Runtime.Serialization.DataContractAttribute> é um membro do namespace <xref:System.Runtime.Serialization>, então você precisará adicionar a instrução `using` apropriado na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="b292e-250">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="b292e-251">Você alterou o nome da classe `repo` para `Repository`, portanto, será necessário fazer a mesma alteração em Program.cs (alguns editores podem oferecer suporte a uma refatoração de renomeação que fará essa alteração automaticamente:)</span><span class="sxs-lookup"><span data-stu-id="b292e-251">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="b292e-252">Em seguida, vamos fazer a mesma alteração com o campo `name` usando a classe <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b292e-252">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="b292e-253">Faça as seguintes alterações na declaração do campo `name` em repo.cs:</span><span class="sxs-lookup"><span data-stu-id="b292e-253">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="b292e-254">Essa alteração significa que você precisa alterar o código que grava o nome de cada repositório em program.cs:</span><span class="sxs-lookup"><span data-stu-id="b292e-254">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="b292e-255">Faça uma `dotnet build` seguido por um `dotnet run` para certificar-se de que você tem os mapeamentos corretos.</span><span class="sxs-lookup"><span data-stu-id="b292e-255">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="b292e-256">Você deve ver o mesmo resultado de antes.</span><span class="sxs-lookup"><span data-stu-id="b292e-256">You should see the same output as before.</span></span> <span data-ttu-id="b292e-257">Antes, processamos mais propriedades do servidor Web, vamos fazer mais uma alteração na classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="b292e-257">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="b292e-258">O membro `Name` é um campo acessível publicamente.</span><span class="sxs-lookup"><span data-stu-id="b292e-258">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="b292e-259">Essa não é uma boa prática orientada a objeto, então vamos alterá-lo para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="b292e-259">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="b292e-260">Para nossos propósitos, não é necessário executar nenhum código específico ao obter ou configurar a propriedade, mas a alteração de uma propriedade facilita a adição dessas alterações posteriormente sem interromper qualquer código que usa a classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="b292e-260">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="b292e-261">Remova a definição de campo e substitua-a por uma [propriedade autoimplementada](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="b292e-261">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="b292e-262">O compilador gera o corpo dos acessadores `get` e `set`, bem como um campo particular para armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="b292e-262">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="b292e-263">Seria semelhante ao código a seguir, que você pode digitar manualmente:</span><span class="sxs-lookup"><span data-stu-id="b292e-263">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="b292e-264">Vamos fazer mais uma alteração antes de adicionar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="b292e-264">Let's make one more change before adding new features.</span></span> <span data-ttu-id="b292e-265">O método `ProcessRepositories` pode fazer o trabalho assíncrono e retornar uma coleção de repositórios.</span><span class="sxs-lookup"><span data-stu-id="b292e-265">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="b292e-266">Vamos retornar o `List<Repository>` desse método e mover o código que grava as informações no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="b292e-266">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="b292e-267">Altere a assinatura de `ProcessRepositories` para retornar uma tarefa cujo resultado é uma lista de objetos `Repository`:</span><span class="sxs-lookup"><span data-stu-id="b292e-267">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="b292e-268">Depois, basta retornar os repositórios depois de processar a resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="b292e-268">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="b292e-269">O compilador gera o objeto `Task<T>` para o retorno porque você marcou esse método como `async`.</span><span class="sxs-lookup"><span data-stu-id="b292e-269">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="b292e-270">Em seguida, vamos modificar o método `Main` para que ele capture esses resultados e grave cada nome de repositório no console.</span><span class="sxs-lookup"><span data-stu-id="b292e-270">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="b292e-271">Seu método `Main` terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="b292e-271">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="b292e-272">O acesso à propriedade `Result` de uma Tarefa é bloqueado até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="b292e-272">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="b292e-273">Normalmente, seria preferível `await` (aguardar) a conclusão da tarefa, como no método `ProcessRepositories`, mas isso não é permitido no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="b292e-273">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="b292e-274">Ler mais informações</span><span class="sxs-lookup"><span data-stu-id="b292e-274">Reading More Information</span></span>

<span data-ttu-id="b292e-275">Vamos concluir isso processando mais algumas propriedades no pacote JSON que são enviadas da API do GitHub.</span><span class="sxs-lookup"><span data-stu-id="b292e-275">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="b292e-276">Não convém capturar tudo, mas a adição de algumas propriedades demonstrará mais alguns recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-276">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="b292e-277">Vamos começar pela adição de alguns tipos mais simples para a definição de classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="b292e-277">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="b292e-278">Adicione essas propriedades à classe:</span><span class="sxs-lookup"><span data-stu-id="b292e-278">Add these properties to that class:</span></span>

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="b292e-279">Essas propriedades têm conversões internas do tipo cadeia de caracteres (que é o que os pacotes JSON contêm) para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="b292e-279">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="b292e-280">O tipo <xref:System.Uri> pode ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="b292e-280">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="b292e-281">Ele representa um URI, ou, nesse caso, uma URL.</span><span class="sxs-lookup"><span data-stu-id="b292e-281">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="b292e-282">No caso dos tipos `Uri` e `int`, se o pacote JSON contiver dados que não são convertidos para o tipo de destino, a ação de serialização lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b292e-282">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="b292e-283">Depois de adicioná-los, atualize o método `Main` para exibir esses elementos:</span><span class="sxs-lookup"><span data-stu-id="b292e-283">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```
<span data-ttu-id="b292e-284">Como etapa final, vamos adicionar as informações para a última operação de envio por push.</span><span class="sxs-lookup"><span data-stu-id="b292e-284">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="b292e-285">Essas informações são formatadas dessa maneira na resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="b292e-285">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="b292e-286">Esse formato não segue o formato <xref:System.DateTime> padrão do .NET.</span><span class="sxs-lookup"><span data-stu-id="b292e-286">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="b292e-287">Por isso, você precisará escrever um método de conversão personalizado.</span><span class="sxs-lookup"><span data-stu-id="b292e-287">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="b292e-288">Provavelmente você também não quer expor a cadeia de caracteres bruta aos usuários da classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="b292e-288">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="b292e-289">Os atributos podem ajudar a controlar isto também.</span><span class="sxs-lookup"><span data-stu-id="b292e-289">Attributes can help control that as well.</span></span> <span data-ttu-id="b292e-290">Primeiro, defina uma propriedade `private` que conterá a representação de cadeia de caracteres da data e hora em sua classe `Repository`:</span><span class="sxs-lookup"><span data-stu-id="b292e-290">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="b292e-291">O atributo `DataMember` informa ao serializador de que isso deve ser processado, mesmo que não seja um membro público.</span><span class="sxs-lookup"><span data-stu-id="b292e-291">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="b292e-292">Em seguida, você precisa escrever uma propriedade pública somente leitura que converte a cadeia de caracteres em um objeto <xref:System.DateTime> válido, e retorna esse <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="b292e-292">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

<span data-ttu-id="b292e-293">Vamos falar sobre as novas construções acima.</span><span class="sxs-lookup"><span data-stu-id="b292e-293">Let's go over the new constructs above.</span></span> <span data-ttu-id="b292e-294">O atributo `IgnoreDataMember` instrui o serializador que esse tipo não deve ser lido para ou gravado de qualquer objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="b292e-294">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="b292e-295">Essa propriedade contém apenas um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="b292e-295">This property contains only a `get` accessor.</span></span> <span data-ttu-id="b292e-296">Não há nenhum acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="b292e-296">There is no `set` accessor.</span></span> <span data-ttu-id="b292e-297">É assim que você define uma propriedade *somente leitura* em C#.</span><span class="sxs-lookup"><span data-stu-id="b292e-297">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="b292e-298">(Sim, você pode criar propriedades *somente gravação* em C#, mas o valor delas é limitado.) O método <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analisa uma cadeia de caracteres e cria um objeto <xref:System.DateTime> usando um formato de data fornecido e adiciona outros metadados a `DateTime` usando um objeto `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="b292e-298">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="b292e-299">Se a operação de análise falhar, o acessador da propriedade gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b292e-299">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="b292e-300">Para usar <xref:System.Globalization.CultureInfo.InvariantCulture>, você precisará adicionar o namespace <xref:System.Globalization> às instruções `using` em `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="b292e-300">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="b292e-301">Por fim, adicione mais uma instrução de saída no console, e você estará pronto para compilar e executar esse aplicativo novamente:</span><span class="sxs-lookup"><span data-stu-id="b292e-301">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="b292e-302">Agora, sua versão deve corresponder ao [exemplo finalizado](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="b292e-302">Your version should now match the [finished sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="b292e-303">Conclusão</span><span class="sxs-lookup"><span data-stu-id="b292e-303">Conclusion</span></span>

<span data-ttu-id="b292e-304">Este tutorial mostrou como fazer solicitações da Web, analisar o resultados e exibir as propriedades dos resultados.</span><span class="sxs-lookup"><span data-stu-id="b292e-304">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="b292e-305">Você também adicionou novos pacotes como dependências em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="b292e-305">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="b292e-306">Você viu alguns dos recursos da linguagem C# que dão suporte a técnicas orientadas a objeto.</span><span class="sxs-lookup"><span data-stu-id="b292e-306">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
