---
title: Cria um cliente REST usando .NET Core
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850982"
---
# <a name="rest-client"></a><span data-ttu-id="5e48c-103">Cliente REST</span><span class="sxs-lookup"><span data-stu-id="5e48c-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="5e48c-104">Introdução</span><span class="sxs-lookup"><span data-stu-id="5e48c-104">Introduction</span></span>

<span data-ttu-id="5e48c-105">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="5e48c-106">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="5e48c-106">You’ll learn:</span></span>

* <span data-ttu-id="5e48c-107">As noções básicas da CLI (Interface de Linha de Comando) do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e48c-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="5e48c-108">Uma visão geral dos recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="5e48c-109">Gerenciamento de dependências com o NuGet</span><span class="sxs-lookup"><span data-stu-id="5e48c-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="5e48c-110">Comunicações HTTP</span><span class="sxs-lookup"><span data-stu-id="5e48c-110">HTTP Communications</span></span>
* <span data-ttu-id="5e48c-111">Processamento de informações de JSON</span><span class="sxs-lookup"><span data-stu-id="5e48c-111">Processing JSON information</span></span>
* <span data-ttu-id="5e48c-112">Gerenciamento de configuração com Atributos.</span><span class="sxs-lookup"><span data-stu-id="5e48c-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="5e48c-113">Você compilará um aplicativo que emite solicitações HTTP para um serviço REST no GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e48c-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="5e48c-114">Você lerá informações no formato JSON e converterá esse pacote JSON em objetos C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="5e48c-115">Por fim, você verá como trabalhar com objetos C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="5e48c-116">Há vários recursos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="5e48c-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="5e48c-117">Vamos compilá-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="5e48c-117">Let’s build them one by one.</span></span>

<span data-ttu-id="5e48c-118">Se preferir acompanhar com o [exemplo final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) para esse tópico, você poderá baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="5e48c-119">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="5e48c-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e48c-120">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5e48c-120">Prerequisites</span></span>

<span data-ttu-id="5e48c-121">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e48c-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="5e48c-122">Você pode encontrar as instruções de instalação na página de [downloads do .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="5e48c-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="5e48c-123">Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="5e48c-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="5e48c-124">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="5e48c-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="5e48c-125">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="5e48c-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="5e48c-126">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="5e48c-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="5e48c-127">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e48c-127">Create the Application</span></span>

<span data-ttu-id="5e48c-128">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-128">The first step is to create a new application.</span></span> <span data-ttu-id="5e48c-129">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="5e48c-130">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="5e48c-130">Make that the current directory.</span></span> <span data-ttu-id="5e48c-131">Digite o comando `dotnet new console` no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="5e48c-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="5e48c-132">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="5e48c-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="5e48c-133">Como esse é um novo projeto, nenhuma das dependências está em vigor, portanto, a primeira execução baixará o .NET Core Framework, instalará um certificado de desenvolvimento e executará o gerenciador de pacotes do NuGet para restaurar dependências ausentes.</span><span class="sxs-lookup"><span data-stu-id="5e48c-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="5e48c-134">Antes de começar a fazer modificações, digite `dotnet run` ([veja a observação](#dotnet-restore-note)) no prompt de comando para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-134">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="5e48c-135">`dotnet run` executará automaticamente `dotnet restore` se estiverem faltando dependências em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="5e48c-135">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="5e48c-136">Ele também executará `dotnet build` se seu aplicativo precisar ser reconstruído.</span><span class="sxs-lookup"><span data-stu-id="5e48c-136">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="5e48c-137">Após sua configuração inicial, você só precisará executar `dotnet restore` ou `dotnet build` quando fizer sentido para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5e48c-137">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="5e48c-138">Adicionar novas dependências</span><span class="sxs-lookup"><span data-stu-id="5e48c-138">Adding New Dependencies</span></span>

<span data-ttu-id="5e48c-139">Uma das principais metas de design para o .NET Core é minimizar o tamanho da instalação do .NET.</span><span class="sxs-lookup"><span data-stu-id="5e48c-139">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="5e48c-140">Se um aplicativo precisar de mais bibliotecas para alguns de seus recursos, adicione essas dependências ao seu arquivo de projeto de C# (\*.csproj).</span><span class="sxs-lookup"><span data-stu-id="5e48c-140">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="5e48c-141">Para nosso exemplo, você precisará adicionar o pacote `System.Runtime.Serialization.Json` para que seu aplicativo possa processar as respostas em JSON.</span><span class="sxs-lookup"><span data-stu-id="5e48c-141">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="5e48c-142">Abra seu arquivo de projeto `csproj`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-142">Open your `csproj` project file.</span></span> <span data-ttu-id="5e48c-143">A primeira linha do arquivo deve aparecer assim:</span><span class="sxs-lookup"><span data-stu-id="5e48c-143">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="5e48c-144">Adicione o seguinte logo após esta linha:</span><span class="sxs-lookup"><span data-stu-id="5e48c-144">Add the following immediately after this line:</span></span>

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

<span data-ttu-id="5e48c-145">A maioria dos editores de código fornece conclusão para versões diferentes dessas bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="5e48c-145">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="5e48c-146">Convém usar a versão mais recente de qualquer pacote que você adicionar.</span><span class="sxs-lookup"><span data-stu-id="5e48c-146">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="5e48c-147">No entanto, é importante ter certeza de que as versões de todos os pacotes correspondam, e que também correspondam à versão da estrutura de aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e48c-147">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="5e48c-148">Após fazer essas alterações, execute `dotnet restore` ([veja a observação](#dotnet-restore-note)) para que o pacote seja instalado em seu sistema.</span><span class="sxs-lookup"><span data-stu-id="5e48c-148">After you've made these changes, execute `dotnet restore` ([see note](#dotnet-restore-note)) so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="5e48c-149">Como fazer solicitações da Web</span><span class="sxs-lookup"><span data-stu-id="5e48c-149">Making Web Requests</span></span>

<span data-ttu-id="5e48c-150">Agora você está pronto para começar a obter dados da Web.</span><span class="sxs-lookup"><span data-stu-id="5e48c-150">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="5e48c-151">Neste aplicativo, você lerá informações da [API do GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="5e48c-151">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="5e48c-152">Vamos ler informações sobre os projetos em [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="5e48c-152">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="5e48c-153">Comece fazendo a solicitação à API do GitHub para recuperar informações sobre os projetos.</span><span class="sxs-lookup"><span data-stu-id="5e48c-153">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="5e48c-154">O ponto de extremidade que você usará é: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-154">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="5e48c-155">Você quer obter todas as informações sobre esses projetos, portanto, use uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="5e48c-155">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="5e48c-156">O navegador também usa solicitações HTTP GET, para que você possa colar essa URL em seu navegador e ver as informações que receberá.</span><span class="sxs-lookup"><span data-stu-id="5e48c-156">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="5e48c-157">Use a classe <xref:System.Net.Http.HttpClient> para fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="5e48c-157">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="5e48c-158">Como todas as APIs .NET modernas, a <xref:System.Net.Http.HttpClient> oferece suporte apenas aos métodos assíncronos para suas APIs de longa execução.</span><span class="sxs-lookup"><span data-stu-id="5e48c-158">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="5e48c-159">Comece criando um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="5e48c-159">Start by making an async method.</span></span> <span data-ttu-id="5e48c-160">Você preencherá a implementação à medida que compila a funcionalidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-160">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="5e48c-161">Comece abrindo o arquivo `program.cs` no diretório do projeto e adicionando o seguinte método à classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="5e48c-161">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="5e48c-162">Será necessário adicionar uma instrução `using` na parte superior de seu método `Main` para que o compilador de C# reconheça o tipo <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="5e48c-162">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="5e48c-163">Se você compilar o projeto neste momento, receberá um aviso gerado para esse método, pois ele não contém operadores `await` e executará de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="5e48c-163">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="5e48c-164">Ignore isso por enquanto. Adicione os operadores `await` à medida que você preenche o método.</span><span class="sxs-lookup"><span data-stu-id="5e48c-164">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="5e48c-165">Em seguida, renomeie o namespace definido na instrução `namespace`, alterando o padrão de `ConsoleApp` para `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-165">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="5e48c-166">Posteriormente, definiremos uma classe `repo` neste namespace.</span><span class="sxs-lookup"><span data-stu-id="5e48c-166">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="5e48c-167">Em seguida, atualize o método `Main` para chamar esse método.</span><span class="sxs-lookup"><span data-stu-id="5e48c-167">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="5e48c-168">O método `ProcessRepositories` retorna uma Tarefa, e você não deve sair do programa antes da conclusão dessa tarefa.</span><span class="sxs-lookup"><span data-stu-id="5e48c-168">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="5e48c-169">Portanto, use o método `Wait` para bloquear e esperar a conclusão da tarefa:</span><span class="sxs-lookup"><span data-stu-id="5e48c-169">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="5e48c-170">Agora, você tem um programa que não faz nada, mas o faz de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="5e48c-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="5e48c-171">Vamos melhorar isso.</span><span class="sxs-lookup"><span data-stu-id="5e48c-171">Let's improve it.</span></span>

<span data-ttu-id="5e48c-172">Primeiro você precisa de um objeto que é capaz de recuperar dados da Web; você pode usar um <xref:System.Net.Http.HttpClient> para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="5e48c-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="5e48c-173">Esse objeto manipula a solicitação e as respostas.</span><span class="sxs-lookup"><span data-stu-id="5e48c-173">This object handles the request and the responses.</span></span> <span data-ttu-id="5e48c-174">Crie uma única instância desse tipo na classe `Program` dentro do arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="5e48c-174">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

<span data-ttu-id="5e48c-175">Vamos voltar ao método `ProcessRepositories` e preencher uma primeira versão dele:</span><span class="sxs-lookup"><span data-stu-id="5e48c-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="5e48c-176">Também será necessário adicionar duas instruções using novas na parte superior do arquivo para que isso seja compilado:</span><span class="sxs-lookup"><span data-stu-id="5e48c-176">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="5e48c-177">A primeira versão faz uma solicitação da Web para ler a lista de todos os repositórios na organização dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="5e48c-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="5e48c-178">(A ID do gitHub para o .NET Foundation é 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="5e48c-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="5e48c-179">As primeiras linhas configuram o <xref:System.Net.Http.HttpClient> para essa solicitação.</span><span class="sxs-lookup"><span data-stu-id="5e48c-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="5e48c-180">Primeiro, ele é configurado para aceitar as respostas JSON do GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e48c-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="5e48c-181">Esse formato é simplesmente JSON.</span><span class="sxs-lookup"><span data-stu-id="5e48c-181">This format is simply JSON.</span></span> <span data-ttu-id="5e48c-182">A próxima linha adiciona um cabeçalho de agente do usuário para todas as solicitações deste objeto.</span><span class="sxs-lookup"><span data-stu-id="5e48c-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="5e48c-183">Esses dois cabeçalhos são verificados pelo código do servidor GitHub e são necessários para recuperar informações do GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e48c-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="5e48c-184">Depois de configurar o <xref:System.Net.Http.HttpClient>, faça uma solicitação da Web e recupere a resposta.</span><span class="sxs-lookup"><span data-stu-id="5e48c-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="5e48c-185">Nesta primeira versão, você usa o método de conveniência <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="5e48c-186">Este método prático inicia uma tarefa que faz a solicitação da Web e, depois, quando a solicitação retornar, ele lê o fluxo de resposta e extrai o conteúdo do fluxo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="5e48c-187">O corpo da resposta retorna como um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="5e48c-188">A cadeia de caracteres fica disponível após a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="5e48c-188">The string is available when the task completes.</span></span>

<span data-ttu-id="5e48c-189">As duas últimas linhas desse método aguardam a tarefa e, depois, imprimem a resposta no console.</span><span class="sxs-lookup"><span data-stu-id="5e48c-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="5e48c-190">Compilar o aplicativo e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-190">Build the app, and run it.</span></span> <span data-ttu-id="5e48c-191">O aviso de compilação desapareceu, pois agora o `ProcessRepositories` contêm um operador `await`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="5e48c-192">Você verá uma longa exibição do texto formatado em JSON.</span><span class="sxs-lookup"><span data-stu-id="5e48c-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="5e48c-193">Processar o resultado JSON</span><span class="sxs-lookup"><span data-stu-id="5e48c-193">Processing the JSON Result</span></span>

<span data-ttu-id="5e48c-194">Neste ponto, você já escreveu o código para recuperar uma resposta de um servidor da Web e exibiu o texto contido nessa resposta.</span><span class="sxs-lookup"><span data-stu-id="5e48c-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="5e48c-195">Agora, vamos converter essa resposta em JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="5e48c-196">O serializador JSON converte os dados em JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-196">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="5e48c-197">A primeira tarefa serve para definir um tipo de classe em C# para conter as informações usadas nessa resposta.</span><span class="sxs-lookup"><span data-stu-id="5e48c-197">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="5e48c-198">Vamos compilar isso lentamente, então comece com um tipo C# simples que contém o nome do repositório:</span><span class="sxs-lookup"><span data-stu-id="5e48c-198">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="5e48c-199">Coloque o código acima em um novo arquivo chamado 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="5e48c-199">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="5e48c-200">Esta versão da classe representa o caminho mais simples para processar os dados em JSON.</span><span class="sxs-lookup"><span data-stu-id="5e48c-200">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="5e48c-201">O nome da classe e o nome do membro corresponderem aos nomes usados no pacote JSON, em vez de seguir as convenções em C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-201">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="5e48c-202">Corrija isso mais tarde fornecendo alguns atributos de configuração.</span><span class="sxs-lookup"><span data-stu-id="5e48c-202">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="5e48c-203">Essa classe demonstra outro recurso importante da serialização e desserialização JSON: Nem todos os campos no pacote JSON fazem parte dessa classe.</span><span class="sxs-lookup"><span data-stu-id="5e48c-203">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="5e48c-204">O serializador JSON ignorará as informações que não estão incluídas no tipo de classe que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="5e48c-204">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="5e48c-205">Esse recurso facilita a criação de tipos que funcionam apenas com um subconjunto dos campos no pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="5e48c-205">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="5e48c-206">Agora que você criou o tipo, vamos desserializá-lo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-206">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="5e48c-207">Você precisará criar um objeto <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-207">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="5e48c-208">Este objeto deve saber o tipo de CLR esperada para o pacote JSON que ele recupera.</span><span class="sxs-lookup"><span data-stu-id="5e48c-208">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="5e48c-209">O pacote do GitHub contém uma sequência de repositórios, então um `List<repo>` é o tipo correto.</span><span class="sxs-lookup"><span data-stu-id="5e48c-209">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="5e48c-210">Adicione a seguinte linha ao seu método `ProcessRepositories`:</span><span class="sxs-lookup"><span data-stu-id="5e48c-210">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="5e48c-211">Você está usando dois novos namespaces, portanto será necessário adicioná-los também:</span><span class="sxs-lookup"><span data-stu-id="5e48c-211">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="5e48c-212">Em seguida, você usará o serializador para converter JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-212">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="5e48c-213">Substitua a chamada para <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> em seu método `ProcessRepositories` pelas duas linhas a seguir:</span><span class="sxs-lookup"><span data-stu-id="5e48c-213">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="5e48c-214">Observe que agora você está usando <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> em vez de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-214">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="5e48c-215">O serializador usa um fluxo, em vez de uma cadeia de caracteres, como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="5e48c-215">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="5e48c-216">Vamos explicar alguns recursos da linguagem C# que estão sendo usados na segunda linha acima.</span><span class="sxs-lookup"><span data-stu-id="5e48c-216">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="5e48c-217">O argumento <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> é uma expressão `await`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-217">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="5e48c-218">Expressões await podem aparecer em quase todo lugar em seu código, apesar de que até o momento, você apenas as viu como parte de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="5e48c-218">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="5e48c-219">Em segundo lugar, o operador `as` converte do tipo de tempo de compilação do `object` para `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-219">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span>
<span data-ttu-id="5e48c-220">A declaração de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declara que ele retorna um objeto do tipo <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-220">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e48c-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> retornará o tipo especificado no momento da construção (`List<repo>` neste tutorial).</span><span class="sxs-lookup"><span data-stu-id="5e48c-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="5e48c-222">Se a conversão não tiver êxito, o operador `as` será avaliado com `null`, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5e48c-222">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="5e48c-223">Você está quase terminando esta seção.</span><span class="sxs-lookup"><span data-stu-id="5e48c-223">You're almost done with this section.</span></span> <span data-ttu-id="5e48c-224">Agora que você converteu o JSON em objetos C#, vamos exibir o nome de cada repositório.</span><span class="sxs-lookup"><span data-stu-id="5e48c-224">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="5e48c-225">Substitua as linhas que mostram:</span><span class="sxs-lookup"><span data-stu-id="5e48c-225">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="5e48c-226">pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5e48c-226">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="5e48c-227">Compile e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-227">Compile and run the application.</span></span> <span data-ttu-id="5e48c-228">Ele imprimirá os nomes dos repositórios que fazem parte do .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="5e48c-228">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="5e48c-229">Controle da serialização</span><span class="sxs-lookup"><span data-stu-id="5e48c-229">Controlling Serialization</span></span>

<span data-ttu-id="5e48c-230">Antes de adicionar mais recursos, vamos abordar o tipo `repo` e fazê-lo seguir convenções mais padrão de C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-230">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="5e48c-231">Faça isso anotando a tipo `repo` com *atributos* que controlem o modo como o serializador JSON funciona.</span><span class="sxs-lookup"><span data-stu-id="5e48c-231">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="5e48c-232">Em seu caso, você usará esses atributos para definir um mapeamento entre os nomes de chave JSON e os nomes de classe e de membros de C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-232">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="5e48c-233">Os dois atributos usados são os atributos <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-233">The two attributes used are the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="5e48c-234">Por convenção, todas as classes de atributo terminam com o sufixo `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-234">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="5e48c-235">No entanto, não é necessário usar esse sufixo ao aplicar um atributo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-235">However, you do not need to use that suffix when you apply an attribute.</span></span>

<span data-ttu-id="5e48c-236">Os atributos <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> são atributos em uma biblioteca diferente, então você precisará adicionar essa biblioteca ao seu arquivo de projeto C# como uma dependência.</span><span class="sxs-lookup"><span data-stu-id="5e48c-236">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="5e48c-237">Adicione a seguinte linha à seção `<ItemGroup>` de seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="5e48c-237">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="5e48c-238">Depois de salvar o arquivo, execute `dotnet restore` ([veja a observação](#dotnet-restore-note)) para recuperar esse pacote.</span><span class="sxs-lookup"><span data-stu-id="5e48c-238">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="5e48c-239">Em seguida, abra o arquivo `repo.cs`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-239">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="5e48c-240">Vamos alterar o nome para usar Pascal Case e soletrar o nome `Repository` completo.</span><span class="sxs-lookup"><span data-stu-id="5e48c-240">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="5e48c-241">Ainda queremos mapear os nós de 'repositório' de JSON para esse tipo, então será necessário adicionar o atributo <xref:System.Runtime.Serialization.DataContractAttribute> à declaração de classe.</span><span class="sxs-lookup"><span data-stu-id="5e48c-241">We still want to map JSON 'repo' nodes to this type, so you'll need to add the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class declaration.</span></span> <span data-ttu-id="5e48c-242">Você definirá a propriedade `Name` do atributo como o nome de nós de JSON mapeados para esse tipo:</span><span class="sxs-lookup"><span data-stu-id="5e48c-242">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="5e48c-243">O <xref:System.Runtime.Serialization.DataContractAttribute> é um membro do namespace <xref:System.Runtime.Serialization>, então você precisará adicionar a instrução `using` apropriado na parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="5e48c-243">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="5e48c-244">Você alterou o nome da classe `repo` para `Repository`, portanto, será necessário fazer a mesma alteração em Program.cs (alguns editores podem oferecer suporte a uma refatoração de renomeação que fará essa alteração automaticamente:)</span><span class="sxs-lookup"><span data-stu-id="5e48c-244">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="5e48c-245">Em seguida, vamos fazer a mesma alteração com o campo `name` usando a classe <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5e48c-245">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="5e48c-246">Faça as seguintes alterações na declaração do campo `name` em repo.cs:</span><span class="sxs-lookup"><span data-stu-id="5e48c-246">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="5e48c-247">Essa alteração significa que você precisa alterar o código que grava o nome de cada repositório em program.cs:</span><span class="sxs-lookup"><span data-stu-id="5e48c-247">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="5e48c-248">Faça uma `dotnet build` seguido por um `dotnet run` para certificar-se de que você tem os mapeamentos corretos.</span><span class="sxs-lookup"><span data-stu-id="5e48c-248">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="5e48c-249">Você deve ver o mesmo resultado de antes.</span><span class="sxs-lookup"><span data-stu-id="5e48c-249">You should see the same output as before.</span></span> <span data-ttu-id="5e48c-250">Antes, processamos mais propriedades do servidor Web, vamos fazer mais uma alteração na classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-250">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="5e48c-251">O membro `Name` é um campo acessível publicamente.</span><span class="sxs-lookup"><span data-stu-id="5e48c-251">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="5e48c-252">Essa não é uma boa prática orientada a objeto, então vamos alterá-lo para uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="5e48c-252">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="5e48c-253">Para nossos propósitos, não é necessário executar nenhum código específico ao obter ou configurar a propriedade, mas a alteração de uma propriedade facilita a adição dessas alterações posteriormente sem interromper qualquer código que usa a classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-253">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="5e48c-254">Remova a definição de campo e substitua-a por uma [propriedade autoimplementada](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="5e48c-254">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="5e48c-255">O compilador gera o corpo dos acessadores `get` e `set`, bem como um campo particular para armazenar o nome.</span><span class="sxs-lookup"><span data-stu-id="5e48c-255">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="5e48c-256">Seria semelhante ao código a seguir, que você pode digitar manualmente:</span><span class="sxs-lookup"><span data-stu-id="5e48c-256">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="5e48c-257">Vamos fazer mais uma alteração antes de adicionar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="5e48c-257">Let's make one more change before adding new features.</span></span> <span data-ttu-id="5e48c-258">O método `ProcessRepositories` pode fazer o trabalho assíncrono e retornar uma coleção de repositórios.</span><span class="sxs-lookup"><span data-stu-id="5e48c-258">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="5e48c-259">Vamos retornar o `List<Repository>` desse método e mover o código que grava as informações no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-259">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="5e48c-260">Altere a assinatura de `ProcessRepositories` para retornar uma tarefa cujo resultado é uma lista de objetos `Repository`:</span><span class="sxs-lookup"><span data-stu-id="5e48c-260">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="5e48c-261">Depois, basta retornar os repositórios depois de processar a resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="5e48c-261">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="5e48c-262">O compilador gera o objeto `Task<T>` para o retorno porque você marcou esse método como `async`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-262">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="5e48c-263">Em seguida, vamos modificar o método `Main` para que ele capture esses resultados e grave cada nome de repositório no console.</span><span class="sxs-lookup"><span data-stu-id="5e48c-263">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="5e48c-264">Seu método `Main` terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="5e48c-264">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="5e48c-265">O acesso à propriedade `Result` de uma Tarefa é bloqueado até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="5e48c-265">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="5e48c-266">Normalmente, seria preferível `await` (aguardar) a conclusão da tarefa, como no método `ProcessRepositories`, mas isso não é permitido no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-266">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="5e48c-267">Ler mais informações</span><span class="sxs-lookup"><span data-stu-id="5e48c-267">Reading More Information</span></span>

<span data-ttu-id="5e48c-268">Vamos concluir isso processando mais algumas propriedades no pacote JSON que são enviadas da API do GitHub.</span><span class="sxs-lookup"><span data-stu-id="5e48c-268">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="5e48c-269">Não convém capturar tudo, mas a adição de algumas propriedades demonstrará mais alguns recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-269">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="5e48c-270">Vamos começar pela adição de alguns tipos mais simples para a definição de classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-270">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="5e48c-271">Adicione essas propriedades à classe:</span><span class="sxs-lookup"><span data-stu-id="5e48c-271">Add these properties to that class:</span></span>

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

<span data-ttu-id="5e48c-272">Essas propriedades têm conversões internas do tipo cadeia de caracteres (que é o que os pacotes JSON contêm) para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="5e48c-272">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="5e48c-273">O tipo <xref:System.Uri> pode ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="5e48c-273">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="5e48c-274">Ele representa um URI, ou, nesse caso, uma URL.</span><span class="sxs-lookup"><span data-stu-id="5e48c-274">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="5e48c-275">No caso dos tipos `Uri` e `int`, se o pacote JSON contiver dados que não são convertidos para o tipo de destino, a ação de serialização lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5e48c-275">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="5e48c-276">Depois de adicioná-los, atualize o método `Main` para exibir esses elementos:</span><span class="sxs-lookup"><span data-stu-id="5e48c-276">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="5e48c-277">Como etapa final, vamos adicionar as informações para a última operação de envio por push.</span><span class="sxs-lookup"><span data-stu-id="5e48c-277">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="5e48c-278">Essas informações são formatadas dessa maneira na resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="5e48c-278">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="5e48c-279">Esse formato não segue o formato <xref:System.DateTime> padrão do .NET.</span><span class="sxs-lookup"><span data-stu-id="5e48c-279">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="5e48c-280">Por isso, você precisará escrever um método de conversão personalizado.</span><span class="sxs-lookup"><span data-stu-id="5e48c-280">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="5e48c-281">Provavelmente você também não quer expor a cadeia de caracteres bruta aos usuários da classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-281">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="5e48c-282">Os atributos podem ajudar a controlar isto também.</span><span class="sxs-lookup"><span data-stu-id="5e48c-282">Attributes can help control that as well.</span></span> <span data-ttu-id="5e48c-283">Primeiro, defina uma propriedade `private` que conterá a representação de cadeia de caracteres da data e hora em sua classe `Repository`:</span><span class="sxs-lookup"><span data-stu-id="5e48c-283">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="5e48c-284">O atributo <xref:System.Runtime.Serialization.DataMemberAttribute> informa ao serializador de que isso deve ser processado, mesmo que não seja um membro público.</span><span class="sxs-lookup"><span data-stu-id="5e48c-284">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="5e48c-285">Em seguida, você precisa escrever uma propriedade pública somente leitura que converte a cadeia de caracteres em um objeto <xref:System.DateTime> válido, e retorna esse <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="5e48c-285">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="5e48c-286">Vamos falar sobre as novas construções acima.</span><span class="sxs-lookup"><span data-stu-id="5e48c-286">Let's go over the new constructs above.</span></span> <span data-ttu-id="5e48c-287">O atributo `IgnoreDataMember` instrui o serializador que esse tipo não deve ser lido para ou gravado de qualquer objeto JSON.</span><span class="sxs-lookup"><span data-stu-id="5e48c-287">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="5e48c-288">Essa propriedade contém apenas um acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-288">This property contains only a `get` accessor.</span></span> <span data-ttu-id="5e48c-289">Não há nenhum acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-289">There is no `set` accessor.</span></span> <span data-ttu-id="5e48c-290">É assim que você define uma propriedade *somente leitura* em C#.</span><span class="sxs-lookup"><span data-stu-id="5e48c-290">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="5e48c-291">(Sim, você pode criar propriedades *somente gravação* em C#, mas o valor delas é limitado.) O método <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analisa uma cadeia de caracteres e cria um objeto <xref:System.DateTime> usando um formato de data fornecido e adiciona outros metadados a `DateTime` usando um objeto `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="5e48c-291">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="5e48c-292">Se a operação de análise falhar, o acessador da propriedade gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5e48c-292">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="5e48c-293">Para usar <xref:System.Globalization.CultureInfo.InvariantCulture>, você precisará adicionar o namespace <xref:System.Globalization> às instruções `using` em `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="5e48c-293">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="5e48c-294">Por fim, adicione mais uma instrução de saída no console, e você estará pronto para compilar e executar esse aplicativo novamente:</span><span class="sxs-lookup"><span data-stu-id="5e48c-294">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="5e48c-295">Agora, sua versão deve corresponder ao [exemplo finalizado](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="5e48c-295">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="5e48c-296">Conclusão</span><span class="sxs-lookup"><span data-stu-id="5e48c-296">Conclusion</span></span>

<span data-ttu-id="5e48c-297">Este tutorial mostrou como fazer solicitações da Web, analisar o resultados e exibir as propriedades dos resultados.</span><span class="sxs-lookup"><span data-stu-id="5e48c-297">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="5e48c-298">Você também adicionou novos pacotes como dependências em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5e48c-298">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="5e48c-299">Você viu alguns dos recursos da linguagem C# que dão suporte a técnicas orientadas a objeto.</span><span class="sxs-lookup"><span data-stu-id="5e48c-299">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
