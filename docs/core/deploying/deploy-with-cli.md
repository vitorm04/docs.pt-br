---
title: Implantação de aplicativos .NET Core com as ferramentas da CLI
description: Aprenda a implantação de aplicativos .NET Core com ferramentas da CLI (interface de linha de comando)
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.openlocfilehash: 7b009068422686442ebff83b9400c365f34a3154
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244738"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="1a8fd-103">Implantando aplicativos .NET Core com ferramentas da CLI (interface de linha de comando)</span><span class="sxs-lookup"><span data-stu-id="1a8fd-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="1a8fd-104">Você pode implantar um aplicativo .NET Core como uma *implantação dependente de estrutura*, que inclui os binários do seu aplicativo, mas depende da presença do .NET Core no sistema de destino, ou como uma *implantação autocontida*, que inclui os binários do seu aplicativo e do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="1a8fd-105">Para obter uma visão geral, consulte [Implantação de aplicativos .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="1a8fd-106">As seções a seguir mostram como usar [ferramentas de interface de linha de comando do .NET Core](../tools/index.md) para criar os seguintes tipos de implantações:</span><span class="sxs-lookup"><span data-stu-id="1a8fd-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="1a8fd-107">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="1a8fd-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="1a8fd-108">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1a8fd-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="1a8fd-109">Implantação autocontida</span><span class="sxs-lookup"><span data-stu-id="1a8fd-109">Self-contained deployment</span></span>
- <span data-ttu-id="1a8fd-110">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1a8fd-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="1a8fd-111">Ao trabalhar na linha de comando, você pode usar um editor de programa de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="1a8fd-112">Se o editor de programa for o [Visual Studio Code](https://code.visualstudio.com), você poderá abrir um console de comando dentro do ambiente do Visual Studio Code selecionando **Exibir** > **Terminal Integrado**.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="1a8fd-113">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="1a8fd-113">Framework-dependent deployment</span></span>

<span data-ttu-id="1a8fd-114">Implantar uma implantação dependente de estrutura sem dependências de terceiros significa simplesmente compilar, testar e publicar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="1a8fd-115">Um exemplo simples criado em C# ilustra o processo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-115">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="1a8fd-116">Crie um diretório de projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-116">Create a project directory.</span></span>

   <span data-ttu-id="1a8fd-117">Crie um diretório para seu projeto e torne-o o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="1a8fd-118">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-118">Create the project.</span></span>

   <span data-ttu-id="1a8fd-119">Na linha de comando, digite [dotnet new console](../tools/dotnet-new.md) para criar um novo projeto de console em C# naquele diretório.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="1a8fd-120">Adicione o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-120">Add the application's source code.</span></span>

   <span data-ttu-id="1a8fd-121">Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-121">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="1a8fd-122">Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="1a8fd-123">Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="1a8fd-124">Atualize as ferramentas e as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-124">Update the project's dependencies and tools.</span></span>
 
   <span data-ttu-id="1a8fd-125">Execute o comando [dotnet restore](../tools/dotnet-restore.md) ([veja observação](#dotnet-restore-note)) para restaurar as dependências especificadas no projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="1a8fd-126">Crie um build de depuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="1a8fd-127">Use o comando [dotnet build](../tools/dotnet-build.md) para compilar o aplicativo ou o comando [dotnet run](../tools/dotnet-run.md) para compilá-lo e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="1a8fd-128">Implante seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-128">Deploy your app.</span></span>

   <span data-ttu-id="1a8fd-129">Depois de ter depurado e testado o programa, crie a implantação usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="1a8fd-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="1a8fd-130">Isso cria uma versão de Lançamento (em vez de Depuração) de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="1a8fd-131">Os arquivos resultantes são colocados em um diretório chamado *publish*, que está em um subdiretório do diretório *bin* do projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="1a8fd-132">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1a8fd-133">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1a8fd-134">Você pode optar por não distribui-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="1a8fd-135">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="1a8fd-136">Você pode implantar o conjunto completo de arquivos de aplicativo da maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="1a8fd-137">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="1a8fd-138">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="1a8fd-138">Run your app</span></span>

   <span data-ttu-id="1a8fd-139">Uma vez instalado, os usuários podem executar seu aplicativo usando o comando `dotnet` e fornecendo o nome de arquivo de aplicativo, como `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="1a8fd-140">Além dos binários do aplicativo, o instalador deverá também agrupar o instalador da estrutura compartilhada ou procurar por ele como um pré-requisito como parte da instalação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="1a8fd-141">A instalação da estrutura compartilhada requer acesso de Administrador/raiz.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="1a8fd-142">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1a8fd-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="1a8fd-143">Implantar uma implantação dependente de estrutura com uma ou mais dependências de terceiros requer que as dependências estejam disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="1a8fd-144">São necessárias duas etapas adicionais antes de executar o comando `dotnet restore` ([veja observação](#dotnet-restore-note)):</span><span class="sxs-lookup"><span data-stu-id="1a8fd-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="1a8fd-145">Adicione referências para as bibliotecas de terceiros necessárias à seção `<ItemGroup>` do arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="1a8fd-146">A seção `<ItemGroup>` a seguir contém uma dependência no [Json.NET](http://www.newtonsoft.com/json) como uma biblioteca de terceiros:</span><span class="sxs-lookup"><span data-stu-id="1a8fd-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="1a8fd-147">Se você ainda não o fez, baixe o pacote NuGet contendo a dependência de terceiros.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="1a8fd-148">Para baixar o pacote, execute o comando `dotnet restore` ([veja observação](#dotnet-restore-note)) depois de adicionar a dependência.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="1a8fd-149">Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="1a8fd-150">Observe que uma implantação dependente de estrutura com dependências de terceiros tem a mesma portabilidade que suas dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="1a8fd-151">Por exemplo, se uma biblioteca de terceiros der suporte apenas a macOS, o aplicativo não será portátil para sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="1a8fd-152">Isso acontecerá se a dependência de terceiros em si depender do código nativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="1a8fd-153">Um bom exemplo disso é o [servidor Kestrel](/aspnet/core/fundamentals/servers/kestrel), que requer uma dependência nativa no [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="1a8fd-154">Quando uma FDD é criada para um aplicativo com esse tipo de dependência de terceiros, a saída publicada contém uma pasta para cada [RID (Identificador de Tempo de Execução)](../rid-catalog.md) que dá suporte a dependência nativa (e que existe em seu pacote NuGet).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="1a8fd-155">Implantação autocontida sem dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1a8fd-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="1a8fd-156">Implantar uma implantação autocontida sem dependências de terceiros inclui a criação do projeto, a modificação do arquivo *csproj*, a compilação, os testes e a publicação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="1a8fd-157">Um exemplo simples criado em C# ilustra o processo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="1a8fd-158">O exemplo mostra como criar uma implantação autocontida usando o [utilitário dotnet](../tools/dotnet.md) da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="1a8fd-159">Crie um diretório para o projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-159">Create a directory for the project.</span></span>

   <span data-ttu-id="1a8fd-160">Crie um diretório para seu projeto e torne-o o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="1a8fd-161">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-161">Create the project.</span></span>

   <span data-ttu-id="1a8fd-162">Na linha de comando, digite [dotnet new console](../tools/dotnet-new.md) para criar um novo projeto de console em C# naquele diretório.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="1a8fd-163">Adicione o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-163">Add the application's source code.</span></span>

   <span data-ttu-id="1a8fd-164">Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="1a8fd-165">Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="1a8fd-166">Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="1a8fd-167">Defina as plataformas às quais seu aplicativo se destinará.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="1a8fd-168">Crie uma marcação `<RuntimeIdentifiers>` na seção `<PropertyGroup>` de seu arquivo *csproj* que define as plataformas de destino do seu aplicativo e especifique o RID (identificador de tempo de execução) de cada plataforma que você selecionar.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="1a8fd-169">Observe que você também precisa adicionar um ponto e vírgula para separar os RIDs.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="1a8fd-170">Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="1a8fd-171">Por exemplo, a seção `<PropertyGroup>` a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.11 de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="1a8fd-172">Observe que o elemento `<RuntimeIdentifiers>` pode aparecer em qualquer `<PropertyGroup>` em seu arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="1a8fd-173">Um arquivo *csproj* de exemplo completo aparece mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="1a8fd-174">Atualize as ferramentas e as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="1a8fd-175">Execute o comando [dotnet restore](../tools/dotnet-restore.md) ([veja observação](#dotnet-restore-note)) para restaurar as dependências especificadas no projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="1a8fd-176">Crie um build de depuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-176">Create a Debug build of your app.</span></span>

   <span data-ttu-id="1a8fd-177">Na linha de comando, use o comando [dotnet build](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="1a8fd-177">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="1a8fd-178">Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-178">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="1a8fd-179">Use o comando `dotnet publish` para as duas plataformas de destino da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1a8fd-179">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="1a8fd-180">Isso cria uma versão de Lançamento (em vez de Depuração) do seu aplicativo para cada plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-180">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="1a8fd-181">Os arquivos resultantes são colocados em um subdiretório chamado *publish* que está em um subdiretório de *.\bin\Release\netcoreapp1.1\<runtime_identifier>* do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-181">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="1a8fd-182">Observe que cada subdiretório contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-182">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="1a8fd-183">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-183">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1a8fd-184">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-184">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1a8fd-185">Você pode optar por não empacotá-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-185">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="1a8fd-186">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-186">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="1a8fd-187">Implante os arquivos publicados na maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-187">Deploy the published files in any way you like.</span></span> <span data-ttu-id="1a8fd-188">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-188">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="1a8fd-189">A seguir está o arquivo *csproj* completo para esse projeto.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-189">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="1a8fd-190">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1a8fd-190">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="1a8fd-191">Implantar uma implantação autocontida com uma ou mais dependências de terceiros envolve adicionar as dependências.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-191">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="1a8fd-192">São necessárias duas etapas adicionais antes de executar o comando `dotnet restore` ([veja observação](#dotnet-restore-note)):</span><span class="sxs-lookup"><span data-stu-id="1a8fd-192">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="1a8fd-193">Adicione referências a quaisquer bibliotecas de terceiros à seção `<ItemGroup>` de seu arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-193">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="1a8fd-194">A seção `<ItemGroup>` a seguir usa Json.NET como uma biblioteca de terceiros.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-194">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="1a8fd-195">Se você ainda não o fez, baixe o pacote NuGet que contém a dependência de terceiros para seu sistema.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-195">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="1a8fd-196">Para disponibilizar a dependência para seu aplicativo, execute o comando `dotnet restore` ([veja observação](#dotnet-restore-note)) depois de adicionar a dependência.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-196">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="1a8fd-197">Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-197">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="1a8fd-198">A seguir está o arquivo *csproj* completo para esse projeto:</span><span class="sxs-lookup"><span data-stu-id="1a8fd-198">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="1a8fd-199">Quando você implanta seu aplicativo, todas as dependências de terceiros usadas em seu aplicativo também contém os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-199">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="1a8fd-200">As bibliotecas de terceiros não são necessárias no sistema em que o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-200">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="1a8fd-201">Observe que você só pode implantar uma implantação autocontida com uma biblioteca de terceiros para plataformas compatíveis com essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-201">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="1a8fd-202">Isso é semelhante a ter dependências de terceiros com dependências nativas em uma implantação dependente de estrutura, em que as dependências nativas devem ser compatíveis com a plataforma para a qual o aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="1a8fd-202">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a><span data-ttu-id="1a8fd-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a8fd-203">See also</span></span>

<span data-ttu-id="1a8fd-204">[Implantação de aplicativos .NET Core](index.md) </span><span class="sxs-lookup"><span data-stu-id="1a8fd-204">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="1a8fd-205">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1a8fd-205">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   

