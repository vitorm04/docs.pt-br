---
title: Cria um cliente REST usando .NET Core
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 776d0ca65944e943c1c5114f95801c20d31a2b74
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900730"
---
# <a name="rest-client"></a><span data-ttu-id="11d8e-103">Cliente REST</span><span class="sxs-lookup"><span data-stu-id="11d8e-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="11d8e-104">Introdução</span><span class="sxs-lookup"><span data-stu-id="11d8e-104">Introduction</span></span>

<span data-ttu-id="11d8e-105">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="11d8e-106">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="11d8e-106">You’ll learn:</span></span>

* <span data-ttu-id="11d8e-107">As noções básicas da CLI (Interface de Linha de Comando) do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11d8e-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="11d8e-108">Uma visão geral dos recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="11d8e-109">Gerenciamento de dependências com o NuGet</span><span class="sxs-lookup"><span data-stu-id="11d8e-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="11d8e-110">Comunicações HTTP</span><span class="sxs-lookup"><span data-stu-id="11d8e-110">HTTP Communications</span></span>
* <span data-ttu-id="11d8e-111">Processamento de informações de JSON</span><span class="sxs-lookup"><span data-stu-id="11d8e-111">Processing JSON information</span></span>
* <span data-ttu-id="11d8e-112">Gerenciamento de configuração com Atributos.</span><span class="sxs-lookup"><span data-stu-id="11d8e-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="11d8e-113">Você compilará um aplicativo que emite solicitações HTTP para um serviço REST no GitHub.</span><span class="sxs-lookup"><span data-stu-id="11d8e-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="11d8e-114">Você lerá informações no formato JSON e converterá esse pacote JSON em objetos C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="11d8e-115">Por fim, você verá como trabalhar com objetos C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="11d8e-116">Há vários recursos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="11d8e-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="11d8e-117">Vamos compilá-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="11d8e-117">Let’s build them one by one.</span></span>

<span data-ttu-id="11d8e-118">Se preferir acompanhar com o [exemplo final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) para esse tópico, você poderá baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="11d8e-119">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="11d8e-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="11d8e-120">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="11d8e-120">Prerequisites</span></span>

<span data-ttu-id="11d8e-121">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="11d8e-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="11d8e-122">Você pode encontrar as instruções de instalação na página de [downloads do .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="11d8e-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="11d8e-123">Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="11d8e-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="11d8e-124">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="11d8e-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="11d8e-125">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="11d8e-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="11d8e-126">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="11d8e-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="11d8e-127">{1&gt;Criar o aplicativo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="11d8e-127">Create the Application</span></span>

<span data-ttu-id="11d8e-128">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-128">The first step is to create a new application.</span></span> <span data-ttu-id="11d8e-129">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="11d8e-130">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="11d8e-130">Make that the current directory.</span></span> <span data-ttu-id="11d8e-131">Digite o seguinte comando em uma janela de console:</span><span class="sxs-lookup"><span data-stu-id="11d8e-131">Enter the following command in a console window:</span></span>

```console
dotnet new console --name WebApiClient
```

<span data-ttu-id="11d8e-132">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="11d8e-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="11d8e-133">O nome do projeto é "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="11d8e-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="11d8e-134">Como esse é um novo projeto, nenhuma das dependências está em vigor, portanto, a primeira execução baixará o .NET Core Framework, instalará um certificado de desenvolvimento e executará o gerenciador de pacotes do NuGet para restaurar dependências ausentes.</span><span class="sxs-lookup"><span data-stu-id="11d8e-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="11d8e-135">Antes de começar a fazer modificações, digite `dotnet run` ([veja a observação](#dotnet-restore-note)) no prompt de comando para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="11d8e-136">`dotnet run` executará automaticamente `dotnet restore` se estiverem faltando dependências em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="11d8e-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="11d8e-137">Ele também executará `dotnet build` se seu aplicativo precisar ser reconstruído.</span><span class="sxs-lookup"><span data-stu-id="11d8e-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="11d8e-138">Após sua configuração inicial, você só precisará executar `dotnet restore` ou `dotnet build` quando fizer sentido para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="11d8e-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="11d8e-139">Adicionar novas dependências</span><span class="sxs-lookup"><span data-stu-id="11d8e-139">Adding New Dependencies</span></span>

<span data-ttu-id="11d8e-140">Uma das principais metas de design para o .NET Core é minimizar o tamanho da instalação do .NET.</span><span class="sxs-lookup"><span data-stu-id="11d8e-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="11d8e-141">Se um aplicativo precisar de mais bibliotecas para alguns de seus recursos, adicione essas dependências ao seu arquivo de projeto de C# (\*.csproj).</span><span class="sxs-lookup"><span data-stu-id="11d8e-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="11d8e-142">Para nosso exemplo, você precisará adicionar o pacote `System.Runtime.Serialization.Json`, para que seu aplicativo possa processar respostas JSON.</span><span class="sxs-lookup"><span data-stu-id="11d8e-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="11d8e-143">Você precisará do pacote de `System.Runtime.Serialization.Json` para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="11d8e-144">Adicione-o ao seu projeto executando o seguinte comando da [CLI do .net](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="11d8e-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="11d8e-145">Como fazer solicitações da Web</span><span class="sxs-lookup"><span data-stu-id="11d8e-145">Making Web Requests</span></span>

<span data-ttu-id="11d8e-146">Agora você está pronto para começar a obter dados da Web.</span><span class="sxs-lookup"><span data-stu-id="11d8e-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="11d8e-147">Neste aplicativo, você lerá informações da [API do GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="11d8e-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="11d8e-148">Vamos ler informações sobre os projetos em [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="11d8e-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="11d8e-149">Comece fazendo a solicitação à API do GitHub para recuperar informações sobre os projetos.</span><span class="sxs-lookup"><span data-stu-id="11d8e-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="11d8e-150">O ponto de extremidade que você usará é: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="11d8e-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="11d8e-151">Você quer obter todas as informações sobre esses projetos, portanto, use uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="11d8e-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="11d8e-152">O navegador também usa solicitações HTTP GET, para que você possa colar essa URL em seu navegador e ver as informações que receberá.</span><span class="sxs-lookup"><span data-stu-id="11d8e-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="11d8e-153">Use a classe <xref:System.Net.Http.HttpClient> para fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="11d8e-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="11d8e-154">Como todas as APIs .NET modernas, a <xref:System.Net.Http.HttpClient> oferece suporte apenas aos métodos assíncronos para suas APIs de longa execução.</span><span class="sxs-lookup"><span data-stu-id="11d8e-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="11d8e-155">Comece criando um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="11d8e-155">Start by making an async method.</span></span> <span data-ttu-id="11d8e-156">Você preencherá a implementação à medida que compila a funcionalidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="11d8e-157">Comece abrindo o arquivo `program.cs` no diretório do projeto e adicionando o seguinte método à classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="11d8e-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="11d8e-158">Será necessário adicionar uma instrução `using` na parte superior de seu método `Main` para que o compilador de C# reconheça o tipo <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="11d8e-158">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="11d8e-159">Se você compilar o projeto neste momento, receberá um aviso gerado para esse método, pois ele não contém operadores `await` e executará de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="11d8e-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="11d8e-160">Ignore isso por enquanto. Adicione os operadores `await` à medida que você preenche o método.</span><span class="sxs-lookup"><span data-stu-id="11d8e-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="11d8e-161">Em seguida, renomeie o namespace definido na instrução `namespace`, alterando o padrão de `ConsoleApp` para `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="11d8e-162">Posteriormente, definiremos uma classe `repo` neste namespace.</span><span class="sxs-lookup"><span data-stu-id="11d8e-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="11d8e-163">Em seguida, atualize o método `Main` para chamar esse método.</span><span class="sxs-lookup"><span data-stu-id="11d8e-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="11d8e-164">O método `ProcessRepositories` retorna uma Tarefa, e você não deve sair do programa antes da conclusão dessa tarefa.</span><span class="sxs-lookup"><span data-stu-id="11d8e-164">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="11d8e-165">Portanto, você deve alterar a assinatura de `Main`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="11d8e-166">Adicione o modificador de `async` e altere o tipo de retorno para `Task`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="11d8e-167">Em seguida, no corpo do método, adicione uma chamada para `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="11d8e-168">Adicione a palavra-chave `await` quando essa chamada de método:</span><span class="sxs-lookup"><span data-stu-id="11d8e-168">Add the `await` keyword when to that method call:</span></span>

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="11d8e-169">Agora, você tem um programa que não faz nada, mas o faz de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="11d8e-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="11d8e-170">Vamos melhorar isso.</span><span class="sxs-lookup"><span data-stu-id="11d8e-170">Let's improve it.</span></span>

<span data-ttu-id="11d8e-171">Primeiro você precisa de um objeto que é capaz de recuperar dados da Web; você pode usar um <xref:System.Net.Http.HttpClient> para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="11d8e-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="11d8e-172">Esse objeto manipula a solicitação e as respostas.</span><span class="sxs-lookup"><span data-stu-id="11d8e-172">This object handles the request and the responses.</span></span> <span data-ttu-id="11d8e-173">Crie uma única instância desse tipo na classe `Program` dentro do arquivo Program.cs.</span><span class="sxs-lookup"><span data-stu-id="11d8e-173">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="11d8e-174">Vamos voltar ao método `ProcessRepositories` e preencher uma primeira versão dele:</span><span class="sxs-lookup"><span data-stu-id="11d8e-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="11d8e-175">Também será necessário adicionar duas instruções using novas na parte superior do arquivo para que isso seja compilado:</span><span class="sxs-lookup"><span data-stu-id="11d8e-175">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="11d8e-176">A primeira versão faz uma solicitação da Web para ler a lista de todos os repositórios na organização dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="11d8e-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="11d8e-177">(A ID do gitHub para o .NET Foundation é 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="11d8e-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="11d8e-178">As primeiras linhas configuram o <xref:System.Net.Http.HttpClient> para essa solicitação.</span><span class="sxs-lookup"><span data-stu-id="11d8e-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="11d8e-179">Primeiro, ele é configurado para aceitar as respostas JSON do GitHub.</span><span class="sxs-lookup"><span data-stu-id="11d8e-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="11d8e-180">Esse formato é simplesmente JSON.</span><span class="sxs-lookup"><span data-stu-id="11d8e-180">This format is simply JSON.</span></span> <span data-ttu-id="11d8e-181">A próxima linha adiciona um cabeçalho de agente do usuário para todas as solicitações deste objeto.</span><span class="sxs-lookup"><span data-stu-id="11d8e-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="11d8e-182">Esses dois cabeçalhos são verificados pelo código do servidor GitHub e são necessários para recuperar informações do GitHub.</span><span class="sxs-lookup"><span data-stu-id="11d8e-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="11d8e-183">Depois de configurar o <xref:System.Net.Http.HttpClient>, faça uma solicitação da Web e recupere a resposta.</span><span class="sxs-lookup"><span data-stu-id="11d8e-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="11d8e-184">Nesta primeira versão, você usa o método de conveniência <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11d8e-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="11d8e-185">Este método prático inicia uma tarefa que faz a solicitação da Web e, depois, quando a solicitação retornar, ele lê o fluxo de resposta e extrai o conteúdo do fluxo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="11d8e-186">O corpo da resposta retorna como um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="11d8e-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="11d8e-187">A cadeia de caracteres fica disponível após a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="11d8e-187">The string is available when the task completes.</span></span>

<span data-ttu-id="11d8e-188">As duas últimas linhas desse método aguardam a tarefa e, depois, imprimem a resposta no console.</span><span class="sxs-lookup"><span data-stu-id="11d8e-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="11d8e-189">Compilar o aplicativo e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-189">Build the app, and run it.</span></span> <span data-ttu-id="11d8e-190">O aviso de compilação desapareceu, pois agora o `ProcessRepositories` contêm um operador `await`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="11d8e-191">Você verá uma longa exibição do texto formatado em JSON.</span><span class="sxs-lookup"><span data-stu-id="11d8e-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="11d8e-192">Processar o resultado JSON</span><span class="sxs-lookup"><span data-stu-id="11d8e-192">Processing the JSON Result</span></span>

<span data-ttu-id="11d8e-193">Neste ponto, você já escreveu o código para recuperar uma resposta de um servidor da Web e exibiu o texto contido nessa resposta.</span><span class="sxs-lookup"><span data-stu-id="11d8e-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="11d8e-194">Agora, vamos converter essa resposta em JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="11d8e-195">A classe <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializa objetos para JSON e desserializa JSON em objetos.</span><span class="sxs-lookup"><span data-stu-id="11d8e-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="11d8e-196">Comece definindo uma classe para representar o `repo` objeto JSON retornado da API do GitHub:</span><span class="sxs-lookup"><span data-stu-id="11d8e-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

<span data-ttu-id="11d8e-197">Coloque o código acima em um novo arquivo chamado 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="11d8e-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="11d8e-198">Esta versão da classe representa o caminho mais simples para processar os dados em JSON.</span><span class="sxs-lookup"><span data-stu-id="11d8e-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="11d8e-199">O nome da classe e o nome do membro corresponderem aos nomes usados no pacote JSON, em vez de seguir as convenções em C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="11d8e-200">Corrija isso mais tarde fornecendo alguns atributos de configuração.</span><span class="sxs-lookup"><span data-stu-id="11d8e-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="11d8e-201">Essa classe demonstra outro recurso importante de serialização e desserialização em JSON: nem todos os campos no pacote JSON fazem parte dessa classe.</span><span class="sxs-lookup"><span data-stu-id="11d8e-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="11d8e-202">O serializador JSON ignorará as informações que não estão incluídas no tipo de classe que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="11d8e-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="11d8e-203">Esse recurso facilita a criação de tipos que funcionam apenas com um subconjunto dos campos no pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="11d8e-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="11d8e-204">Agora que você criou o tipo, vamos desserializá-lo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-204">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="11d8e-205">Em seguida, você usará o serializador para converter JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="11d8e-206">Substitua a chamada para <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> em seu método `ProcessRepositories` com as três linhas a seguir:</span><span class="sxs-lookup"><span data-stu-id="11d8e-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="11d8e-207">Você está usando um novo namespace, portanto, você precisará adicioná-lo na parte superior do arquivo também:</span><span class="sxs-lookup"><span data-stu-id="11d8e-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="11d8e-208">Observe que agora você está usando <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> em vez de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="11d8e-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="11d8e-209">O serializador usa um fluxo, em vez de uma cadeia de caracteres, como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="11d8e-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="11d8e-210">Vamos explicar alguns recursos do C# idioma que estão sendo usados na segunda linha do trecho de código anterior.</span><span class="sxs-lookup"><span data-stu-id="11d8e-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="11d8e-211">O primeiro argumento para <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> é uma expressão de `await`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="11d8e-212">(Os outros dois parâmetros são opcionais e são omitidos no trecho de código.) As expressões Await podem aparecer quase em qualquer lugar no seu código, embora até agora você as tenha visto apenas como parte de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="11d8e-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="11d8e-213">O método `Deserialize` é *genérico*, o que significa que você deve fornecer argumentos de tipo para o tipo de objeto que deve ser criado a partir do texto JSON.</span><span class="sxs-lookup"><span data-stu-id="11d8e-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="11d8e-214">Neste exemplo, você está desserializando para um `List<Repository>`, que é outro objeto genérico, o <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="11d8e-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="11d8e-215">A classe `List<>` armazena uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="11d8e-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="11d8e-216">O argumento Type declara o tipo de objetos armazenados no `List<>`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="11d8e-217">O texto JSON representa uma coleção de objetos de repositório, portanto, o argumento de tipo é `Repository`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="11d8e-218">Você está quase terminando esta seção.</span><span class="sxs-lookup"><span data-stu-id="11d8e-218">You're almost done with this section.</span></span> <span data-ttu-id="11d8e-219">Agora que você converteu o JSON em objetos C#, vamos exibir o nome de cada repositório.</span><span class="sxs-lookup"><span data-stu-id="11d8e-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="11d8e-220">Substitua as linhas que mostram:</span><span class="sxs-lookup"><span data-stu-id="11d8e-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="11d8e-221">pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="11d8e-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="11d8e-222">Compile e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11d8e-222">Compile and run the application.</span></span> <span data-ttu-id="11d8e-223">Ele imprimirá os nomes dos repositórios que fazem parte do .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="11d8e-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="11d8e-224">Controle da serialização</span><span class="sxs-lookup"><span data-stu-id="11d8e-224">Controlling Serialization</span></span>

<span data-ttu-id="11d8e-225">Antes de adicionar mais recursos, vamos abordar a propriedade `name` usando o atributo `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="11d8e-226">Faça as seguintes alterações na declaração do campo `name` em repo.cs:</span><span class="sxs-lookup"><span data-stu-id="11d8e-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="11d8e-227">Essa alteração significa que você precisa alterar o código que grava o nome de cada repositório em program.cs:</span><span class="sxs-lookup"><span data-stu-id="11d8e-227">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="11d8e-228">Execute `dotnet run` para certificar-se de que você tem os mapeamentos corretos.</span><span class="sxs-lookup"><span data-stu-id="11d8e-228">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="11d8e-229">Você deve ver o mesmo resultado de antes.</span><span class="sxs-lookup"><span data-stu-id="11d8e-229">You should see the same output as before.</span></span>

<span data-ttu-id="11d8e-230">Vamos fazer mais uma alteração antes de adicionar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="11d8e-230">Let's make one more change before adding new features.</span></span> <span data-ttu-id="11d8e-231">O método `ProcessRepositories` pode fazer o trabalho assíncrono e retornar uma coleção de repositórios.</span><span class="sxs-lookup"><span data-stu-id="11d8e-231">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="11d8e-232">Vamos retornar o `List<Repository>` desse método e mover o código que grava as informações no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-232">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="11d8e-233">Altere a assinatura de `ProcessRepositories` para retornar uma tarefa cujo resultado é uma lista de objetos `Repository`:</span><span class="sxs-lookup"><span data-stu-id="11d8e-233">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="11d8e-234">Depois, basta retornar os repositórios depois de processar a resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="11d8e-234">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="11d8e-235">O compilador gera o objeto `Task<T>` para o retorno porque você marcou esse método como `async`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-235">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="11d8e-236">Em seguida, vamos modificar o método `Main` para que ele capture esses resultados e grave cada nome de repositório no console.</span><span class="sxs-lookup"><span data-stu-id="11d8e-236">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="11d8e-237">Seu método `Main` terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="11d8e-237">Your `Main` method now looks like this:</span></span>

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="11d8e-238">Ler mais informações</span><span class="sxs-lookup"><span data-stu-id="11d8e-238">Reading More Information</span></span>

<span data-ttu-id="11d8e-239">Vamos concluir isso processando mais algumas propriedades no pacote JSON que são enviadas da API do GitHub.</span><span class="sxs-lookup"><span data-stu-id="11d8e-239">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="11d8e-240">Não convém capturar tudo, mas a adição de algumas propriedades demonstrará mais alguns recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-240">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="11d8e-241">Vamos começar pela adição de alguns tipos mais simples para a definição de classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-241">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="11d8e-242">Adicione essas propriedades à classe:</span><span class="sxs-lookup"><span data-stu-id="11d8e-242">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="11d8e-243">Essas propriedades têm conversões internas do tipo cadeia de caracteres (que é o que os pacotes JSON contêm) para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="11d8e-243">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="11d8e-244">O tipo <xref:System.Uri> pode ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="11d8e-244">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="11d8e-245">Ele representa um URI, ou, nesse caso, uma URL.</span><span class="sxs-lookup"><span data-stu-id="11d8e-245">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="11d8e-246">No caso dos tipos `Uri` e `int`, se o pacote JSON contiver dados que não são convertidos para o tipo de destino, a ação de serialização lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="11d8e-246">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="11d8e-247">Depois de adicioná-los, atualize o método `Main` para exibir esses elementos:</span><span class="sxs-lookup"><span data-stu-id="11d8e-247">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="11d8e-248">Como etapa final, vamos adicionar as informações para a última operação de envio por push.</span><span class="sxs-lookup"><span data-stu-id="11d8e-248">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="11d8e-249">Essas informações são formatadas dessa maneira na resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="11d8e-249">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="11d8e-250">Esse formato não segue o formato <xref:System.DateTime> padrão do .NET.</span><span class="sxs-lookup"><span data-stu-id="11d8e-250">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="11d8e-251">Por isso, você precisará escrever um método de conversão personalizado.</span><span class="sxs-lookup"><span data-stu-id="11d8e-251">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="11d8e-252">Provavelmente você também não quer expor a cadeia de caracteres bruta aos usuários da classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-252">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="11d8e-253">Os atributos podem ajudar a controlar isto também.</span><span class="sxs-lookup"><span data-stu-id="11d8e-253">Attributes can help control that as well.</span></span> <span data-ttu-id="11d8e-254">Primeiro, defina uma propriedade `public` que conterá a representação da cadeia de caracteres da data e hora em sua classe `Repository` e uma propriedade `LastPush` `readonly` que retorna uma cadeia de caracteres formatada que representa a data de retorno:</span><span class="sxs-lookup"><span data-stu-id="11d8e-254">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="11d8e-255">Vamos examinar as novas construções que acabamos de definir.</span><span class="sxs-lookup"><span data-stu-id="11d8e-255">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="11d8e-256">A propriedade `LastPush` é definida usando um *membro expression-apto para* para o acessador `get`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-256">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="11d8e-257">Não há nenhum acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-257">There is no `set` accessor.</span></span> <span data-ttu-id="11d8e-258">Omitir o acessador de `set` é como você define uma propriedade *somente leitura* no C#.</span><span class="sxs-lookup"><span data-stu-id="11d8e-258">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="11d8e-259">(Sim, você pode criar propriedades *somente gravação* no C#, mas seu valor é limitado.) O método <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analisa uma cadeia de caracteres e cria um objeto <xref:System.DateTime> usando um formato de data fornecido e adiciona metadados adicionais ao `DateTime` usando um objeto `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="11d8e-259">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="11d8e-260">Se a operação de análise falhar, o acessador da propriedade gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="11d8e-260">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="11d8e-261">Para usar <xref:System.Globalization.CultureInfo.InvariantCulture>, você precisará adicionar o namespace <xref:System.Globalization> às instruções `using` em `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="11d8e-261">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="11d8e-262">Por fim, adicione mais uma instrução de saída no console, e você estará pronto para compilar e executar esse aplicativo novamente:</span><span class="sxs-lookup"><span data-stu-id="11d8e-262">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="11d8e-263">Agora, sua versão deve corresponder ao [exemplo finalizado](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="11d8e-263">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="11d8e-264">Conclusão</span><span class="sxs-lookup"><span data-stu-id="11d8e-264">Conclusion</span></span>

<span data-ttu-id="11d8e-265">Este tutorial mostrou como fazer solicitações da Web, analisar o resultados e exibir as propriedades dos resultados.</span><span class="sxs-lookup"><span data-stu-id="11d8e-265">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="11d8e-266">Você também adicionou novos pacotes como dependências em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="11d8e-266">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="11d8e-267">Você viu alguns dos recursos da linguagem C# que dão suporte a técnicas orientadas a objeto.</span><span class="sxs-lookup"><span data-stu-id="11d8e-267">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
