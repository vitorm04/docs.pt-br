---
title: Implantar aplicativos .NET Core com ferramentas de CLI (interface de linha de comando)
description: Aprender a implantar um aplicativo .NET Core com ferramentas de CLI (interface de linha de comando)
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: 05460174e9b8472a2862c829cd58b72aec26b549
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151090"
---
# <a name="deploy-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="5ed73-103">Implantar aplicativos .NET Core com ferramentas de CLI (interface de linha de comando)</span><span class="sxs-lookup"><span data-stu-id="5ed73-103">Deploy .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="5ed73-104">Você pode implantar um aplicativo .NET Core como uma *implantação dependente de estrutura*, que inclui os binários do seu aplicativo, mas depende da presença do .NET Core no sistema de destino, ou como uma *implantação autocontida*, que inclui os binários do seu aplicativo e do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5ed73-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="5ed73-105">Para obter uma visão geral, consulte [Implantação de aplicativos .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="5ed73-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="5ed73-106">As seções a seguir mostram como usar [ferramentas de interface de linha de comando do .NET Core](../tools/index.md) para criar os seguintes tipos de implantações:</span><span class="sxs-lookup"><span data-stu-id="5ed73-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="5ed73-107">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="5ed73-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="5ed73-108">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="5ed73-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="5ed73-109">Implantação autocontida</span><span class="sxs-lookup"><span data-stu-id="5ed73-109">Self-contained deployment</span></span>
- <span data-ttu-id="5ed73-110">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="5ed73-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="5ed73-111">Ao trabalhar na linha de comando, você pode usar um editor de programa de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="5ed73-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="5ed73-112">Se o editor de programa for o [Visual Studio Code](https://code.visualstudio.com), você poderá abrir um console de comando dentro do ambiente do Visual Studio Code selecionando **Exibir** > **Terminal Integrado**.</span><span class="sxs-lookup"><span data-stu-id="5ed73-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="5ed73-113">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="5ed73-113">Framework-dependent deployment</span></span>

<span data-ttu-id="5ed73-114">Implantar uma implantação dependente de estrutura sem dependências de terceiros significa simplesmente compilar, testar e publicar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="5ed73-115">Um exemplo simples criado em C# ilustra o processo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-115">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="5ed73-116">Crie um diretório de projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-116">Create a project directory.</span></span>

   <span data-ttu-id="5ed73-117">Crie um diretório para seu projeto e torne-o o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="5ed73-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="5ed73-118">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-118">Create the project.</span></span>

   <span data-ttu-id="5ed73-119">Na linha de comando, digite [dotnet new console](../tools/dotnet-new.md) para criar um novo projeto de console em C# ou [dotnet new console -lang vb](../tools/dotnet-new.md) para criar um novo projeto de console do Visual Basic nesse diretório.</span><span class="sxs-lookup"><span data-stu-id="5ed73-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project or [dotnet new console -lang vb](../tools/dotnet-new.md) to create a new Visual Basic console project in that directory.</span></span>

1. <span data-ttu-id="5ed73-120">Adicione o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-120">Add the application's source code.</span></span>

   <span data-ttu-id="5ed73-121">Abra o arquivo *Program.cs* ou *Program.vb* no editor e substitua o código gerado automaticamente com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5ed73-121">Open the *Program.cs* or *Program.vb* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="5ed73-122">Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5ed73-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="5ed73-123">Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="5ed73-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="5ed73-124">Atualize as ferramentas e as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-124">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="5ed73-125">Execute o comando [dotnet restore](../tools/dotnet-restore.md) ([veja observação](#dotnet-restore-note)) para restaurar as dependências especificadas no projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="5ed73-126">Crie um build de depuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="5ed73-127">Use o comando [dotnet build](../tools/dotnet-build.md) para compilar o aplicativo ou o comando [dotnet run](../tools/dotnet-run.md) para compilá-lo e executá-lo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="5ed73-128">Implante seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-128">Deploy your app.</span></span>

   <span data-ttu-id="5ed73-129">Depois de ter depurado e testado o programa, crie a implantação usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5ed73-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   <span data-ttu-id="5ed73-130">Isso cria uma versão de Lançamento (em vez de Depuração) de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="5ed73-131">Os arquivos resultantes são colocados em um diretório chamado *publish*, que está em um subdiretório do diretório *bin* do projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="5ed73-132">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="5ed73-133">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="5ed73-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="5ed73-134">Você pode optar por não distribui-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="5ed73-135">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="5ed73-136">Você pode implantar o conjunto completo de arquivos de aplicativo da maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="5ed73-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="5ed73-137">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="5ed73-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="5ed73-138">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5ed73-138">Run your app</span></span>

   <span data-ttu-id="5ed73-139">Uma vez instalado, os usuários podem executar seu aplicativo usando o comando `dotnet` e fornecendo o nome de arquivo de aplicativo, como `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="5ed73-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="5ed73-140">Além dos binários do aplicativo, o instalador deverá também agrupar o instalador da estrutura compartilhada ou procurar por ele como um pré-requisito como parte da instalação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="5ed73-141">A instalação da estrutura compartilhada requer acesso de Administrador/raiz.</span><span class="sxs-lookup"><span data-stu-id="5ed73-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="5ed73-142">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="5ed73-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="5ed73-143">Implantar uma implantação dependente de estrutura com uma ou mais dependências de terceiros requer que as dependências estejam disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="5ed73-144">São necessárias duas etapas adicionais antes de executar o comando `dotnet restore` ([veja observação](#dotnet-restore-note)):</span><span class="sxs-lookup"><span data-stu-id="5ed73-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="5ed73-145">Adicione referências para as bibliotecas de terceiros necessárias à seção `<ItemGroup>` do arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="5ed73-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="5ed73-146">A seção `<ItemGroup>` a seguir contém uma dependência no [Json.NET](https://www.newtonsoft.com/json) como uma biblioteca de terceiros:</span><span class="sxs-lookup"><span data-stu-id="5ed73-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](https://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="5ed73-147">Se você ainda não o fez, baixe o pacote NuGet contendo a dependência de terceiros.</span><span class="sxs-lookup"><span data-stu-id="5ed73-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="5ed73-148">Para baixar o pacote, execute o comando `dotnet restore` ([veja observação](#dotnet-restore-note)) depois de adicionar a dependência.</span><span class="sxs-lookup"><span data-stu-id="5ed73-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="5ed73-149">Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="5ed73-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="5ed73-150">Observe que uma implantação dependente de estrutura com dependências de terceiros tem a mesma portabilidade que suas dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="5ed73-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="5ed73-151">Por exemplo, se uma biblioteca de terceiros der suporte apenas a macOS, o aplicativo não será portátil para sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="5ed73-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="5ed73-152">Isso acontecerá se a dependência de terceiros em si depender do código nativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="5ed73-153">Um bom exemplo disso é o [servidor Kestrel](/aspnet/core/fundamentals/servers/kestrel), que requer uma dependência nativa no [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="5ed73-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="5ed73-154">Quando uma FDD é criada para um aplicativo com esse tipo de dependência de terceiros, a saída publicada contém uma pasta para cada [RID (Identificador de Tempo de Execução)](../rid-catalog.md) que dá suporte a dependência nativa (e que existe em seu pacote NuGet).</span><span class="sxs-lookup"><span data-stu-id="5ed73-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="5ed73-155">Implantação autocontida sem dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="5ed73-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="5ed73-156">Implantar uma implantação autocontida sem dependências de terceiros inclui a criação do projeto, a modificação do arquivo *csproj*, a compilação, os testes e a publicação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="5ed73-157">Um exemplo simples criado em C# ilustra o processo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="5ed73-158">O exemplo mostra como criar uma implantação autocontida usando o [utilitário dotnet](../tools/dotnet.md) da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="5ed73-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="5ed73-159">Crie um diretório para o projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-159">Create a directory for the project.</span></span>

   <span data-ttu-id="5ed73-160">Crie um diretório para seu projeto e torne-o o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="5ed73-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="5ed73-161">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-161">Create the project.</span></span>

   <span data-ttu-id="5ed73-162">Na linha de comando, digite [dotnet new console](../tools/dotnet-new.md) para criar um novo projeto de console em C# naquele diretório.</span><span class="sxs-lookup"><span data-stu-id="5ed73-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="5ed73-163">Adicione o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-163">Add the application's source code.</span></span>

   <span data-ttu-id="5ed73-164">Abra o arquivo *Program.cs* no editor e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5ed73-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="5ed73-165">Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="5ed73-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="5ed73-166">Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="5ed73-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. <span data-ttu-id="5ed73-167">Defina as plataformas às quais seu aplicativo se destinará.</span><span class="sxs-lookup"><span data-stu-id="5ed73-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="5ed73-168">Crie uma marcação `<RuntimeIdentifiers>` na seção `<PropertyGroup>` de seu arquivo *csproj* que define as plataformas de destino do seu aplicativo e especifique o RID (identificador de tempo de execução) de cada plataforma que você selecionar.</span><span class="sxs-lookup"><span data-stu-id="5ed73-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="5ed73-169">Observe que você também precisa adicionar um ponto e vírgula para separar os RIDs.</span><span class="sxs-lookup"><span data-stu-id="5ed73-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="5ed73-170">Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5ed73-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="5ed73-171">Por exemplo, a seção `<PropertyGroup>` a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.11 de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5ed73-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="5ed73-172">Observe que o elemento `<RuntimeIdentifiers>` pode aparecer em qualquer `<PropertyGroup>` em seu arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="5ed73-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="5ed73-173">Um arquivo *csproj* de exemplo completo aparece mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="5ed73-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="5ed73-174">Atualize as ferramentas e as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="5ed73-175">Execute o comando [dotnet restore](../tools/dotnet-restore.md) ([veja observação](#dotnet-restore-note)) para restaurar as dependências especificadas no projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="5ed73-176">Determine se você deseja usar o modo de invariável de globalização.</span><span class="sxs-lookup"><span data-stu-id="5ed73-176">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="5ed73-177">Especialmente se seu aplicativo for destinado ao Linux, será possível reduzir o tamanho total da sua implantação usando o [modo invariável de globalização](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="5ed73-177">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="5ed73-178">O modo invariável de globalização é útil para aplicativos que não são conhecidos globalmente e que podem usar as convenções de formatação, de maiúsculas e minúsculas e a comparação de cadeia de caracteres e ordem de classificação da [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="5ed73-178">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="5ed73-179">Para habilitar o modo invariável, clique com o botão direito do mouse no seu projeto (não na solução) no **Gerenciador de Soluções** e selecione **Editar SCD.csproj** ou **Editar SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="5ed73-179">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="5ed73-180">Em seguida, adicione as seguintes linhas realçadas ao arquivo:</span><span class="sxs-lookup"><span data-stu-id="5ed73-180">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="5ed73-181">Crie um build de depuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-181">Create a Debug build of your app.</span></span>

   <span data-ttu-id="5ed73-182">Na linha de comando, use o comando [dotnet build](../tools/dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="5ed73-182">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="5ed73-183">Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.</span><span class="sxs-lookup"><span data-stu-id="5ed73-183">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="5ed73-184">Use o comando `dotnet publish` para as duas plataformas de destino da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5ed73-184">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="5ed73-185">Isso cria uma versão de Lançamento (em vez de Depuração) do seu aplicativo para cada plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="5ed73-185">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="5ed73-186">Os arquivos resultantes são colocados em um subdiretório chamado *publish* que está em um subdiretório de *.\bin\Release\netcoreapp2.1\<identificador_de_tempo_de_execução>* do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-186">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp2.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="5ed73-187">Observe que cada subdiretório contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-187">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="5ed73-188">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-188">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="5ed73-189">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="5ed73-189">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="5ed73-190">Você pode optar por não empacotá-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-190">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="5ed73-191">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-191">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="5ed73-192">Implante os arquivos publicados na maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="5ed73-192">Deploy the published files in any way you like.</span></span> <span data-ttu-id="5ed73-193">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="5ed73-193">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="5ed73-194">A seguir está o arquivo *csproj* completo para esse projeto.</span><span class="sxs-lookup"><span data-stu-id="5ed73-194">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="5ed73-195">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="5ed73-195">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="5ed73-196">Implantar uma implantação autocontida com uma ou mais dependências de terceiros envolve adicionar as dependências.</span><span class="sxs-lookup"><span data-stu-id="5ed73-196">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="5ed73-197">São necessárias duas etapas adicionais antes de executar o comando `dotnet restore` ([veja observação](#dotnet-restore-note)):</span><span class="sxs-lookup"><span data-stu-id="5ed73-197">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="5ed73-198">Adicione referências a quaisquer bibliotecas de terceiros à seção `<ItemGroup>` de seu arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="5ed73-198">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="5ed73-199">A seção `<ItemGroup>` a seguir usa Json.NET como uma biblioteca de terceiros.</span><span class="sxs-lookup"><span data-stu-id="5ed73-199">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="5ed73-200">Se você ainda não o fez, baixe o pacote NuGet que contém a dependência de terceiros para seu sistema.</span><span class="sxs-lookup"><span data-stu-id="5ed73-200">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="5ed73-201">Para disponibilizar a dependência para seu aplicativo, execute o comando `dotnet restore` ([veja observação](#dotnet-restore-note)) depois de adicionar a dependência.</span><span class="sxs-lookup"><span data-stu-id="5ed73-201">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="5ed73-202">Como a dependência é resolvida fora do cache local do NuGet no momento da publicação, ela deve estar disponível no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="5ed73-202">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="5ed73-203">A seguir está o arquivo *csproj* completo para esse projeto:</span><span class="sxs-lookup"><span data-stu-id="5ed73-203">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="5ed73-204">Quando você implanta seu aplicativo, todas as dependências de terceiros usadas em seu aplicativo também contém os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ed73-204">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="5ed73-205">As bibliotecas de terceiros não são necessárias no sistema em que o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="5ed73-205">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="5ed73-206">Observe que você só pode implantar uma implantação autocontida com uma biblioteca de terceiros para plataformas compatíveis com essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="5ed73-206">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="5ed73-207">Isso é semelhante a ter dependências de terceiros com dependências nativas em uma implantação dependente de estrutura, em que as dependências nativas devem ser compatíveis com a plataforma para a qual o aplicativo é implantado.</span><span class="sxs-lookup"><span data-stu-id="5ed73-207">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a><span data-ttu-id="5ed73-208">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ed73-208">See also</span></span>

* [<span data-ttu-id="5ed73-209">Implantação de um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="5ed73-209">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="5ed73-210">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5ed73-210">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
