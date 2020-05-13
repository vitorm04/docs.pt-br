---
title: Cria um cliente REST usando .NET Core
description: Este tutorial ensina vários recursos no .NET Core e da linguagem C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: c7b7e9803b0c05f4956f5c007bca8aa4b200cfca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208019"
---
# <a name="rest-client"></a><span data-ttu-id="4cb73-103">Cliente REST</span><span class="sxs-lookup"><span data-stu-id="4cb73-103">REST client</span></span>

<span data-ttu-id="4cb73-104">Este tutorial ensina vários recursos no .NET Core e da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="4cb73-105">Você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="4cb73-105">You’ll learn:</span></span>

* <span data-ttu-id="4cb73-106">As noções básicas do CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4cb73-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="4cb73-107">Uma visão geral dos recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="4cb73-108">Gerenciamento de dependências com o NuGet</span><span class="sxs-lookup"><span data-stu-id="4cb73-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="4cb73-109">Comunicações HTTP</span><span class="sxs-lookup"><span data-stu-id="4cb73-109">HTTP Communications</span></span>
* <span data-ttu-id="4cb73-110">Processamento de informações de JSON</span><span class="sxs-lookup"><span data-stu-id="4cb73-110">Processing JSON information</span></span>
* <span data-ttu-id="4cb73-111">Gerenciamento de configuração com Atributos.</span><span class="sxs-lookup"><span data-stu-id="4cb73-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="4cb73-112">Você compilará um aplicativo que emite solicitações HTTP para um serviço REST no GitHub.</span><span class="sxs-lookup"><span data-stu-id="4cb73-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="4cb73-113">Você lerá informações no formato JSON e converterá esse pacote JSON em objetos C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="4cb73-114">Por fim, você verá como trabalhar com objetos C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="4cb73-115">Há muitos recursos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="4cb73-115">There are many features in this tutorial.</span></span> <span data-ttu-id="4cb73-116">Vamos compilá-los individualmente.</span><span class="sxs-lookup"><span data-stu-id="4cb73-116">Let’s build them one by one.</span></span>

<span data-ttu-id="4cb73-117">Se preferir acompanhar com o [exemplo final](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) para esse tópico, você poderá baixá-lo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="4cb73-118">Para obter instruções de download, consulte [Exemplos e tutoriais](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4cb73-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4cb73-119">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4cb73-119">Prerequisites</span></span>

<span data-ttu-id="4cb73-120">Você precisará configurar seu computador para executar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4cb73-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="4cb73-121">Você pode encontrar as instruções de instalação na página de [downloads do .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="4cb73-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="4cb73-122">Execute esse aplicativo no Windows, Linux, macOS ou em um contêiner do Docker.</span><span class="sxs-lookup"><span data-stu-id="4cb73-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="4cb73-123">Será necessário instalar o editor de código de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="4cb73-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="4cb73-124">As descrições a seguir usam o [Visual Studio Code](https://code.visualstudio.com/), que é uma software livre, no editor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="4cb73-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="4cb73-125">No entanto, você pode usar quaisquer ferramentas que esteja familiarizado.</span><span class="sxs-lookup"><span data-stu-id="4cb73-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="4cb73-126">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="4cb73-126">Create the Application</span></span>

<span data-ttu-id="4cb73-127">A primeira etapa é criar um novo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-127">The first step is to create a new application.</span></span> <span data-ttu-id="4cb73-128">Abra um prompt de comando e crie um novo diretório para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="4cb73-129">Torne ele o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="4cb73-129">Make that the current directory.</span></span> <span data-ttu-id="4cb73-130">Digite o seguinte comando em uma janela de console:</span><span class="sxs-lookup"><span data-stu-id="4cb73-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="4cb73-131">Isso cria os arquivos iniciais de um aplicativo "Olá, Mundo" básico.</span><span class="sxs-lookup"><span data-stu-id="4cb73-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="4cb73-132">O nome do projeto é "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="4cb73-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="4cb73-133">Como esse é um novo projeto, nenhuma das dependências está em vigor.</span><span class="sxs-lookup"><span data-stu-id="4cb73-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="4cb73-134">A primeira execução baixará o .NET Core Framework, instalará um certificado de desenvolvimento e executará o Gerenciador de pacotes NuGet para restaurar as dependências ausentes.</span><span class="sxs-lookup"><span data-stu-id="4cb73-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="4cb73-135">Antes de começar a fazer modificações, digite `dotnet run` ([veja a observação](#dotnet-restore-note)) no prompt de comando para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="4cb73-136">`dotnet run` executará automaticamente `dotnet restore` se estiverem faltando dependências em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="4cb73-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="4cb73-137">Ele também executará `dotnet build` se seu aplicativo precisar ser reconstruído.</span><span class="sxs-lookup"><span data-stu-id="4cb73-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="4cb73-138">Após sua configuração inicial, você só precisará executar `dotnet restore` ou `dotnet build` quando fizer sentido para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4cb73-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="4cb73-139">Adicionar novas dependências</span><span class="sxs-lookup"><span data-stu-id="4cb73-139">Adding New Dependencies</span></span>

<span data-ttu-id="4cb73-140">Uma das principais metas de design para o .NET Core é minimizar o tamanho da instalação do .NET.</span><span class="sxs-lookup"><span data-stu-id="4cb73-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="4cb73-141">Se um aplicativo precisar de mais bibliotecas para alguns de seus recursos, adicione essas dependências ao seu arquivo de projeto de C# (\*.csproj).</span><span class="sxs-lookup"><span data-stu-id="4cb73-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="4cb73-142">Para nosso exemplo, você precisará adicionar o `System.Runtime.Serialization.Json` pacote, para que seu aplicativo possa processar respostas JSON.</span><span class="sxs-lookup"><span data-stu-id="4cb73-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="4cb73-143">Você precisará do `System.Runtime.Serialization.Json` pacote para este aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="4cb73-144">Adicione-o ao seu projeto executando o seguinte comando da [CLI do .net](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="4cb73-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="4cb73-145">Como fazer solicitações da Web</span><span class="sxs-lookup"><span data-stu-id="4cb73-145">Making Web Requests</span></span>

<span data-ttu-id="4cb73-146">Agora você está pronto para começar a obter dados da Web.</span><span class="sxs-lookup"><span data-stu-id="4cb73-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="4cb73-147">Neste aplicativo, você lerá informações da [API do GitHub](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="4cb73-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="4cb73-148">Vamos ler informações sobre os projetos em [.NET Foundation](https://www.dotnetfoundation.org/).</span><span class="sxs-lookup"><span data-stu-id="4cb73-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="4cb73-149">Comece fazendo a solicitação à API do GitHub para recuperar informações sobre os projetos.</span><span class="sxs-lookup"><span data-stu-id="4cb73-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="4cb73-150">O ponto de extremidade que você usará é: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="4cb73-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="4cb73-151">Você quer obter todas as informações sobre esses projetos, portanto, use uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="4cb73-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="4cb73-152">O navegador também usa solicitações HTTP GET, para que você possa colar essa URL em seu navegador e ver as informações que receberá.</span><span class="sxs-lookup"><span data-stu-id="4cb73-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="4cb73-153">Use a classe <xref:System.Net.Http.HttpClient> para fazer solicitações da Web.</span><span class="sxs-lookup"><span data-stu-id="4cb73-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="4cb73-154">Como todas as APIs .NET modernas, a <xref:System.Net.Http.HttpClient> oferece suporte apenas aos métodos assíncronos para suas APIs de longa execução.</span><span class="sxs-lookup"><span data-stu-id="4cb73-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="4cb73-155">Comece criando um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="4cb73-155">Start by making an async method.</span></span> <span data-ttu-id="4cb73-156">Você preencherá a implementação à medida que compila a funcionalidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="4cb73-157">Comece abrindo o arquivo `program.cs` no diretório do projeto e adicionando o seguinte método à classe `Program`:</span><span class="sxs-lookup"><span data-stu-id="4cb73-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="4cb73-158">Você precisará adicionar uma `using` diretiva na parte superior do seu `Main` método para que o compilador C# reconheça o <xref:System.Threading.Tasks.Task> tipo:</span><span class="sxs-lookup"><span data-stu-id="4cb73-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="4cb73-159">Se você compilar o projeto neste momento, receberá um aviso gerado para esse método, pois ele não contém operadores `await` e executará de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="4cb73-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="4cb73-160">Ignore isso por enquanto. Adicione os operadores `await` à medida que você preenche o método.</span><span class="sxs-lookup"><span data-stu-id="4cb73-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="4cb73-161">Em seguida, atualize o `Main` método para chamar o `ProcessRepositories` método.</span><span class="sxs-lookup"><span data-stu-id="4cb73-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="4cb73-162">O `ProcessRepositories` método retorna uma tarefa e você não deve sair do programa antes que essa tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="4cb73-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="4cb73-163">Portanto, você deve alterar a assinatura de `Main` .</span><span class="sxs-lookup"><span data-stu-id="4cb73-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="4cb73-164">Adicione o `async` modificador e altere o tipo de retorno para `Task` .</span><span class="sxs-lookup"><span data-stu-id="4cb73-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="4cb73-165">Em seguida, no corpo do método, adicione uma chamada para `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="4cb73-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="4cb73-166">Adicione a `await` palavra-chave a essa chamada de método:</span><span class="sxs-lookup"><span data-stu-id="4cb73-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="4cb73-167">Agora, você tem um programa que não faz nada, mas o faz de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="4cb73-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="4cb73-168">Vamos melhorar isso.</span><span class="sxs-lookup"><span data-stu-id="4cb73-168">Let's improve it.</span></span>

<span data-ttu-id="4cb73-169">Primeiro você precisa de um objeto que é capaz de recuperar dados da Web; você pode usar um <xref:System.Net.Http.HttpClient> para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="4cb73-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="4cb73-170">Esse objeto manipula a solicitação e as respostas.</span><span class="sxs-lookup"><span data-stu-id="4cb73-170">This object handles the request and the responses.</span></span> <span data-ttu-id="4cb73-171">Crie uma instância única desse tipo na `Program` classe dentro do arquivo *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="4cb73-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="4cb73-172">Vamos voltar ao método `ProcessRepositories` e preencher uma primeira versão dele:</span><span class="sxs-lookup"><span data-stu-id="4cb73-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="4cb73-173">Você também precisará adicionar duas novas `using` diretivas na parte superior do arquivo para que isso seja compilado:</span><span class="sxs-lookup"><span data-stu-id="4cb73-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="4cb73-174">A primeira versão faz uma solicitação da Web para ler a lista de todos os repositórios na organização dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="4cb73-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="4cb73-175">(A ID do gitHub para o .NET Foundation é 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="4cb73-175">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="4cb73-176">As primeiras linhas configuram o <xref:System.Net.Http.HttpClient> para essa solicitação.</span><span class="sxs-lookup"><span data-stu-id="4cb73-176">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="4cb73-177">Primeiro, ele é configurado para aceitar as respostas JSON do GitHub.</span><span class="sxs-lookup"><span data-stu-id="4cb73-177">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="4cb73-178">Esse formato é simplesmente JSON.</span><span class="sxs-lookup"><span data-stu-id="4cb73-178">This format is simply JSON.</span></span> <span data-ttu-id="4cb73-179">A próxima linha adiciona um cabeçalho de agente do usuário para todas as solicitações deste objeto.</span><span class="sxs-lookup"><span data-stu-id="4cb73-179">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="4cb73-180">Esses dois cabeçalhos são verificados pelo código do servidor GitHub e são necessários para recuperar informações do GitHub.</span><span class="sxs-lookup"><span data-stu-id="4cb73-180">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="4cb73-181">Depois de configurar o <xref:System.Net.Http.HttpClient>, faça uma solicitação da Web e recupere a resposta.</span><span class="sxs-lookup"><span data-stu-id="4cb73-181">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="4cb73-182">Nesta primeira versão, você usa o método de conveniência <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4cb73-182">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="4cb73-183">Este método prático inicia uma tarefa que faz a solicitação da Web e, depois, quando a solicitação retornar, ele lê o fluxo de resposta e extrai o conteúdo do fluxo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-183">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="4cb73-184">O corpo da resposta retorna como um <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4cb73-184">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="4cb73-185">A cadeia de caracteres fica disponível após a conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="4cb73-185">The string is available when the task completes.</span></span>

<span data-ttu-id="4cb73-186">As duas últimas linhas desse método aguardam a tarefa e, depois, imprimem a resposta no console.</span><span class="sxs-lookup"><span data-stu-id="4cb73-186">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="4cb73-187">Compilar o aplicativo e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-187">Build the app, and run it.</span></span> <span data-ttu-id="4cb73-188">O aviso de compilação desapareceu, pois agora o `ProcessRepositories` contêm um operador `await`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-188">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="4cb73-189">Você verá uma longa exibição do texto formatado em JSON.</span><span class="sxs-lookup"><span data-stu-id="4cb73-189">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="4cb73-190">Processar o resultado JSON</span><span class="sxs-lookup"><span data-stu-id="4cb73-190">Processing the JSON Result</span></span>

<span data-ttu-id="4cb73-191">Neste ponto, você já escreveu o código para recuperar uma resposta de um servidor da Web e exibiu o texto contido nessa resposta.</span><span class="sxs-lookup"><span data-stu-id="4cb73-191">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="4cb73-192">Agora, vamos converter essa resposta em JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-192">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="4cb73-193">A <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> classe serializa objetos para JSON e DESSERIALIZA JSON em objetos.</span><span class="sxs-lookup"><span data-stu-id="4cb73-193">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="4cb73-194">Comece definindo uma classe para representar o `repo` objeto JSON retornado da API do github:</span><span class="sxs-lookup"><span data-stu-id="4cb73-194">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

<span data-ttu-id="4cb73-195">Coloque o código acima em um novo arquivo chamado 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="4cb73-195">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="4cb73-196">Esta versão da classe representa o caminho mais simples para processar os dados em JSON.</span><span class="sxs-lookup"><span data-stu-id="4cb73-196">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="4cb73-197">O nome da classe e o nome do membro corresponderem aos nomes usados no pacote JSON, em vez de seguir as convenções em C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-197">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="4cb73-198">Corrija isso mais tarde fornecendo alguns atributos de configuração.</span><span class="sxs-lookup"><span data-stu-id="4cb73-198">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="4cb73-199">Essa classe demonstra outro recurso importante de serialização e desserialização em JSON: nem todos os campos no pacote JSON fazem parte dessa classe.</span><span class="sxs-lookup"><span data-stu-id="4cb73-199">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="4cb73-200">O serializador JSON ignorará as informações que não estão incluídas no tipo de classe que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="4cb73-200">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="4cb73-201">Esse recurso facilita a criação de tipos que funcionam apenas com um subconjunto dos campos no pacote JSON.</span><span class="sxs-lookup"><span data-stu-id="4cb73-201">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="4cb73-202">Agora que você criou o tipo, vamos desserializá-lo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-202">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="4cb73-203">Em seguida, você usará o serializador para converter JSON em objetos de C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-203">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="4cb73-204">Substitua a chamada para <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> no seu `ProcessRepositories` método pelas seguintes linhas:</span><span class="sxs-lookup"><span data-stu-id="4cb73-204">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="4cb73-205">Você está usando um novo namespace, portanto, você precisará adicioná-lo na parte superior do arquivo também:</span><span class="sxs-lookup"><span data-stu-id="4cb73-205">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="4cb73-206">Observe que agora você está usando <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> em vez de <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="4cb73-206">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="4cb73-207">O serializador usa um fluxo, em vez de uma cadeia de caracteres, como sua fonte.</span><span class="sxs-lookup"><span data-stu-id="4cb73-207">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="4cb73-208">Vamos explicar alguns recursos da linguagem C# que estão sendo usados na segunda linha do trecho de código anterior.</span><span class="sxs-lookup"><span data-stu-id="4cb73-208">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="4cb73-209">O primeiro argumento para <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> é uma `await` expressão.</span><span class="sxs-lookup"><span data-stu-id="4cb73-209">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="4cb73-210">(Os outros dois parâmetros são opcionais e são omitidos no trecho de código.) As expressões Await podem aparecer quase em qualquer lugar no seu código, embora até agora você as tenha visto apenas como parte de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="4cb73-210">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="4cb73-211">O `Deserialize` método é *genérico*, o que significa que você deve fornecer argumentos de tipo para o tipo de objeto que deve ser criado a partir do texto JSON.</span><span class="sxs-lookup"><span data-stu-id="4cb73-211">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="4cb73-212">Neste exemplo, você está desserializando para um `List<Repository>` , que é outro objeto genérico, o <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4cb73-212">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4cb73-213">A `List<>` classe armazena uma coleção de objetos.</span><span class="sxs-lookup"><span data-stu-id="4cb73-213">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="4cb73-214">O argumento Type declara o tipo de objetos armazenados no `List<>` .</span><span class="sxs-lookup"><span data-stu-id="4cb73-214">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="4cb73-215">O texto JSON representa uma coleção de objetos de repositório, portanto, o argumento de tipo é `Repository` .</span><span class="sxs-lookup"><span data-stu-id="4cb73-215">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="4cb73-216">Você está quase terminando esta seção.</span><span class="sxs-lookup"><span data-stu-id="4cb73-216">You're almost done with this section.</span></span> <span data-ttu-id="4cb73-217">Agora que você converteu o JSON em objetos C#, vamos exibir o nome de cada repositório.</span><span class="sxs-lookup"><span data-stu-id="4cb73-217">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="4cb73-218">Substitua as linhas que mostram:</span><span class="sxs-lookup"><span data-stu-id="4cb73-218">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="4cb73-219">pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="4cb73-219">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="4cb73-220">Compile e execute o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-220">Compile and run the application.</span></span> <span data-ttu-id="4cb73-221">Ele imprimirá os nomes dos repositórios que fazem parte do .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="4cb73-221">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="4cb73-222">Controle da serialização</span><span class="sxs-lookup"><span data-stu-id="4cb73-222">Controlling Serialization</span></span>

<span data-ttu-id="4cb73-223">Antes de adicionar mais recursos, vamos abordar a `name` propriedade usando o `[JsonPropertyName]` atributo.</span><span class="sxs-lookup"><span data-stu-id="4cb73-223">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="4cb73-224">Faça as seguintes alterações na declaração do campo `name` em repo.cs:</span><span class="sxs-lookup"><span data-stu-id="4cb73-224">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="4cb73-225">Para usar o `[JsonPropertyName]` atributo, será necessário adicionar o <xref:System.Text.Json.Serialization> namespace às `using` diretivas:</span><span class="sxs-lookup"><span data-stu-id="4cb73-225">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="4cb73-226">Essa alteração significa que você precisa alterar o código que grava o nome de cada repositório em program.cs:</span><span class="sxs-lookup"><span data-stu-id="4cb73-226">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="4cb73-227">Execute `dotnet run` para certificar-se de que você tem os mapeamentos corretos.</span><span class="sxs-lookup"><span data-stu-id="4cb73-227">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="4cb73-228">Você deve ver o mesmo resultado de antes.</span><span class="sxs-lookup"><span data-stu-id="4cb73-228">You should see the same output as before.</span></span>

<span data-ttu-id="4cb73-229">Vamos fazer mais uma alteração antes de adicionar novos recursos.</span><span class="sxs-lookup"><span data-stu-id="4cb73-229">Let's make one more change before adding new features.</span></span> <span data-ttu-id="4cb73-230">O método `ProcessRepositories` pode fazer o trabalho assíncrono e retornar uma coleção de repositórios.</span><span class="sxs-lookup"><span data-stu-id="4cb73-230">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="4cb73-231">Vamos retornar o `List<Repository>` desse método e mover o código que grava as informações no método `Main`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-231">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="4cb73-232">Altere a assinatura de `ProcessRepositories` para retornar uma tarefa cujo resultado é uma lista de objetos `Repository`:</span><span class="sxs-lookup"><span data-stu-id="4cb73-232">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="4cb73-233">Depois, basta retornar os repositórios depois de processar a resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="4cb73-233">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="4cb73-234">O compilador gera o objeto `Task<T>` para o retorno porque você marcou esse método como `async`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-234">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="4cb73-235">Em seguida, vamos modificar o método `Main` para que ele capture esses resultados e grave cada nome de repositório no console.</span><span class="sxs-lookup"><span data-stu-id="4cb73-235">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="4cb73-236">Seu método `Main` terá a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="4cb73-236">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="4cb73-237">Ler mais informações</span><span class="sxs-lookup"><span data-stu-id="4cb73-237">Reading More Information</span></span>

<span data-ttu-id="4cb73-238">Vamos concluir isso processando mais algumas propriedades no pacote JSON que são enviadas da API do GitHub.</span><span class="sxs-lookup"><span data-stu-id="4cb73-238">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="4cb73-239">Não convém capturar tudo, mas a adição de algumas propriedades demonstrará mais alguns recursos da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-239">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="4cb73-240">Vamos começar pela adição de alguns tipos mais simples para a definição de classe `Repository`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-240">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="4cb73-241">Adicione essas propriedades à classe:</span><span class="sxs-lookup"><span data-stu-id="4cb73-241">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="4cb73-242">Essas propriedades têm conversões internas do tipo cadeia de caracteres (que é o que os pacotes JSON contêm) para o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="4cb73-242">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="4cb73-243">O tipo <xref:System.Uri> pode ser novidade para você.</span><span class="sxs-lookup"><span data-stu-id="4cb73-243">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="4cb73-244">Ele representa um URI, ou, nesse caso, uma URL.</span><span class="sxs-lookup"><span data-stu-id="4cb73-244">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="4cb73-245">No caso dos tipos `Uri` e `int`, se o pacote JSON contiver dados que não são convertidos para o tipo de destino, a ação de serialização lançará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4cb73-245">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="4cb73-246">Depois de adicioná-los, atualize o método `Main` para exibir esses elementos:</span><span class="sxs-lookup"><span data-stu-id="4cb73-246">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="4cb73-247">Como etapa final, vamos adicionar as informações para a última operação de envio por push.</span><span class="sxs-lookup"><span data-stu-id="4cb73-247">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="4cb73-248">Essas informações são formatadas dessa maneira na resposta JSON:</span><span class="sxs-lookup"><span data-stu-id="4cb73-248">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="4cb73-249">Esse formato está em UTC (tempo Universal Coordenado), portanto, você obterá um <xref:System.DateTime> valor cuja <xref:System.DateTime.Kind%2A> propriedade é <xref:System.DateTimeKind.Utc> .</span><span class="sxs-lookup"><span data-stu-id="4cb73-249">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="4cb73-250">Se você preferir uma data representada em seu fuso horário, precisará escrever um método de conversão personalizado.</span><span class="sxs-lookup"><span data-stu-id="4cb73-250">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="4cb73-251">Primeiro, defina uma `public` propriedade que conterá a representação UTC da data e hora em sua `Repository` classe e uma `LastPush` `readonly` propriedade que retorna a data convertida para a hora local:</span><span class="sxs-lookup"><span data-stu-id="4cb73-251">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="4cb73-252">Vamos examinar as novas construções que acabamos de definir.</span><span class="sxs-lookup"><span data-stu-id="4cb73-252">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="4cb73-253">A `LastPush` propriedade é definida usando um *membro expression-apto para* para o `get` acessador.</span><span class="sxs-lookup"><span data-stu-id="4cb73-253">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="4cb73-254">Não há nenhum acessador `set`.</span><span class="sxs-lookup"><span data-stu-id="4cb73-254">There is no `set` accessor.</span></span> <span data-ttu-id="4cb73-255">Omitir o `set` acessador é como você define uma propriedade *somente leitura* em C#.</span><span class="sxs-lookup"><span data-stu-id="4cb73-255">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="4cb73-256">(Sim, você pode criar propriedades *somente gravação* em C#, mas o valor delas é limitado.)</span><span class="sxs-lookup"><span data-stu-id="4cb73-256">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="4cb73-257">Por fim, adicione mais uma instrução de saída no console, e você estará pronto para compilar e executar esse aplicativo novamente:</span><span class="sxs-lookup"><span data-stu-id="4cb73-257">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="4cb73-258">Agora, sua versão deve corresponder ao [exemplo finalizado](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="4cb73-258">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="4cb73-259">Conclusão</span><span class="sxs-lookup"><span data-stu-id="4cb73-259">Conclusion</span></span>

<span data-ttu-id="4cb73-260">Este tutorial mostrou como fazer solicitações da Web, analisar o resultados e exibir as propriedades dos resultados.</span><span class="sxs-lookup"><span data-stu-id="4cb73-260">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="4cb73-261">Você também adicionou novos pacotes como dependências em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="4cb73-261">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="4cb73-262">Você viu alguns dos recursos da linguagem C# que dão suporte a técnicas orientadas a objeto.</span><span class="sxs-lookup"><span data-stu-id="4cb73-262">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
