---
title: Implantação de aplicativos .NET Core com o Visual Studio
description: Aprenda a implantação de aplicativos .NET Core com o Visual Studio
author: rpetrusha
ms.author: ronpet
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7a9410ca99f621ee6d0e8b263354ebc536f71a4a
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705793"
---
# <a name="deploying-net-core-apps-with-visual-studio"></a><span data-ttu-id="1ad72-103">Implantando aplicativos .NET Core com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ad72-103">Deploying .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="1ad72-104">Você pode implantar um aplicativo .NET Core como uma *implantação dependente de estrutura*, que inclui os binários do seu aplicativo, mas depende da presença do .NET Core no sistema de destino, ou como uma *implantação autocontida*, que inclui os binários do seu aplicativo e do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1ad72-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="1ad72-105">Para obter uma visão geral da implantação de aplicativos .NET Core, consulte [Implantação de aplicativos .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="1ad72-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="1ad72-106">As seções a seguir mostram como usar o Microsoft Visual Studio para criar os seguintes tipos de implantações:</span><span class="sxs-lookup"><span data-stu-id="1ad72-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="1ad72-107">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="1ad72-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="1ad72-108">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1ad72-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="1ad72-109">Implantação autocontida</span><span class="sxs-lookup"><span data-stu-id="1ad72-109">Self-contained deployment</span></span>
- <span data-ttu-id="1ad72-110">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1ad72-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="1ad72-111">Para obter informações sobre como usar o Visual Studio para desenvolver aplicativos .NET Core, consulte [Pré-requisitos para .NET Core no Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span><span class="sxs-lookup"><span data-stu-id="1ad72-111">For information on using Visual Studio to develop .NET Core applications, see [Prerequisites for .NET Core on Windows](../windows-prerequisites.md#prerequisites-with-visual-studio-2017).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="1ad72-112">Implantação dependente de estrutura</span><span class="sxs-lookup"><span data-stu-id="1ad72-112">Framework-dependent deployment</span></span>

<span data-ttu-id="1ad72-113">Implantar uma implantação dependente de estrutura sem dependências de terceiros significa simplesmente compilar, testar e publicar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="1ad72-114">Um exemplo simples criado em C# ilustra o processo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-114">A simple example written in C# illustrates the process.</span></span>  

1. <span data-ttu-id="1ad72-115">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="1ad72-115">Create the project.</span></span>

   <span data-ttu-id="1ad72-116">Selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="1ad72-117">Na caixa de diálogo **Novo projeto**, expanda as categorias de projeto (C# ou Visual Basic) de sua linguagem no painel de tipos de projeto **Instalados**, escolha **.NET Core** e, em seguida, selecione o modelo **Aplicativo de console (.NET Core)** no painel central.</span><span class="sxs-lookup"><span data-stu-id="1ad72-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="1ad72-118">Insira um nome de projeto, como "FDD" na caixa de texto **Nome**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="1ad72-119">Selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="1ad72-120">Adicione o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-120">Add the application's source code.</span></span>

   <span data-ttu-id="1ad72-121">Abra o arquivo *Program.cs* ou *Program.vb* no editor e substitua o código gerado automaticamente com o seguinte código.</span><span class="sxs-lookup"><span data-stu-id="1ad72-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="1ad72-122">Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1ad72-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="1ad72-123">Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="1ad72-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="1ad72-124">Crie um build de depuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="1ad72-125">Selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="1ad72-126">Você também pode compilar e executar o build de Depuração do aplicativo selecionando **Depurar** > **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="1ad72-127">Implante seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-127">Deploy your app.</span></span>

   <span data-ttu-id="1ad72-128">Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="1ad72-129">Para publicar do Visual Studio, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1ad72-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="1ad72-130">Altere a configuração da solução de **Depuração** para **Lançamento** na barra de ferramentas para compilar uma versão de lançamento (em vez de uma de depuração) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="1ad72-131">Clique com o botão direito do mouse no projeto (e não na solução) no **Gerenciador de Soluções** e selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="1ad72-132">Na guia **Publicar**, selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="1ad72-133">O Visual Studio grava os arquivos que compõem seu aplicativo no sistema de arquivos local.</span><span class="sxs-lookup"><span data-stu-id="1ad72-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="1ad72-134">A guia **Publicar** agora mostra um único perfil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="1ad72-135">As configurações do perfil são mostradas na seção **Resumo** da guia.</span><span class="sxs-lookup"><span data-stu-id="1ad72-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="1ad72-136">Os arquivos resultantes são colocados em um diretório nomeado `Publish` no Windows e `publish` em sistemas Unix que está em um subdiretório do subdiretório *.\bin\release\netcoreapp2.1* do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1ad72-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="1ad72-137">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1ad72-138">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="1ad72-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1ad72-139">Você pode optar por não empacotá-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="1ad72-140">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="1ad72-141">Implante o conjunto completo de arquivos de aplicativo da maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="1ad72-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="1ad72-142">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1ad72-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="1ad72-143">Uma vez instalado, os usuários podem executar seu aplicativo usando o comando `dotnet` e fornecendo o nome de arquivo de aplicativo, como `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="1ad72-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="1ad72-144">Além dos binários do aplicativo, o instalador deverá também agrupar o instalador da estrutura compartilhada ou procurar por ele como um pré-requisito como parte da instalação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="1ad72-145">A instalação da estrutura compartilhada requer acesso de Administrador/raiz, pois se trata de todo o computador.</span><span class="sxs-lookup"><span data-stu-id="1ad72-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="1ad72-146">Implantação dependente de estrutura com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1ad72-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="1ad72-147">Implantar uma implantação dependente de estrutura com uma ou mais dependências de terceiros requer que todas as dependências estejam disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1ad72-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="1ad72-148">As etapas adicionais a seguir são necessárias antes de ser possível compilar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1ad72-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="1ad72-149">Use o **Gerenciador de Pacotes NuGet** para adicionar uma referência a um pacote NuGet ao projeto e se o pacote ainda não estiver disponível no sistema, instale-o.</span><span class="sxs-lookup"><span data-stu-id="1ad72-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="1ad72-150">Para abrir o gerenciador de pacotes, selecione **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Gerenciar Pacotes NuGet para a Solução**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="1ad72-151">Confirme se `Newtonsoft.Json` está instalado em seu sistema e, se não estiver, instale-o.</span><span class="sxs-lookup"><span data-stu-id="1ad72-151">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="1ad72-152">A guia **Instalados** lista os pacotes NuGet instalados no sistema.</span><span class="sxs-lookup"><span data-stu-id="1ad72-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="1ad72-153">Se `Newtonsoft.Json` não estiver listado, selecione a guia **Procurar** e insira "Newtonsoft.Json" na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1ad72-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="1ad72-154">Selecione `Newtonsoft.Json` e, no painel direito, selecione seu projeto antes de selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="1ad72-155">Se `Newtonsoft.Json` já estiver instalado no sistema, adicione-o ao projeto selecionando o projeto no painel direito da guia **Gerenciar Pacotes para a Solução**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="1ad72-156">Observe que uma implantação dependente de estrutura com dependências de terceiros tem a mesma portabilidade que suas dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="1ad72-156">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="1ad72-157">Por exemplo, se uma biblioteca de terceiros der suporte apenas a macOS, o aplicativo não será portátil para sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="1ad72-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="1ad72-158">Isso acontecerá se a dependência de terceiros em si depender do código nativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="1ad72-159">Um bom exemplo disso é o [servidor Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), que requer uma dependência nativa no [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="1ad72-159">A good example of this is [Kestrel server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="1ad72-160">Quando uma FDD é criada para um aplicativo com esse tipo de dependência de terceiros, a saída publicada contém uma pasta para cada [RID (Identificador de Tempo de Execução)](../rid-catalog.md) que dá suporte a dependência nativa (e que existe em seu pacote NuGet).</span><span class="sxs-lookup"><span data-stu-id="1ad72-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="1ad72-161">Implantação autocontida sem dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1ad72-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="1ad72-162">Implantar uma implantação autocontida sem dependências de terceiros inclui a criação do projeto, a modificação do arquivo *csproj*, a compilação, os testes e a publicação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="1ad72-163">Um exemplo simples criado em C# ilustra o processo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="1ad72-164">Comece criando, codificando e testando seu projeto como você faria com uma implantação que depende da estrutura:</span><span class="sxs-lookup"><span data-stu-id="1ad72-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="1ad72-165">Crie o projeto.</span><span class="sxs-lookup"><span data-stu-id="1ad72-165">Create the project.</span></span>

   <span data-ttu-id="1ad72-166">Selecione **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="1ad72-167">Na caixa de diálogo **Novo projeto**, expanda as categorias de projeto (C# ou Visual Basic) de sua linguagem no painel de tipos de projeto **Instalados**, escolha **.NET Core** e, em seguida, selecione o modelo **Aplicativo de console (.NET Core)** no painel central.</span><span class="sxs-lookup"><span data-stu-id="1ad72-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="1ad72-168">Insira um nome de projeto, como "SCD" na caixa de texto **Nome** e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="1ad72-169">Adicione o código-fonte do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-169">Add the application's source code.</span></span>

   <span data-ttu-id="1ad72-170">Abra o *Program.cs* ou o arquivo no editor e substitua o código gerado automaticamente pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="1ad72-170">Open the *Program.cs* or file in your editor, and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="1ad72-171">Ele solicitará que o usuário insira texto e exibirá as palavras individuais inseridas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="1ad72-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="1ad72-172">Ele usa a expressão regular `\w+` para separar as palavras no texto de entrada.</span><span class="sxs-lookup"><span data-stu-id="1ad72-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="1ad72-173">Determine se você deseja usar o modo de invariável de globalização.</span><span class="sxs-lookup"><span data-stu-id="1ad72-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="1ad72-174">Especialmente se seu aplicativo for destinado ao Linux, será possível reduzir o tamanho total da sua implantação usando o [modo invariável de globalização](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="1ad72-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="1ad72-175">O modo invariável de globalização é útil para aplicativos que não são conhecidos globalmente e que podem usar as convenções de formatação, de maiúsculas e minúsculas e a comparação de cadeia de caracteres e ordem de classificação da [cultura invariável](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="1ad72-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="1ad72-176">Para habilitar o modo invariável, clique com o botão direito do mouse no seu projeto (não na solução) no **Gerenciador de Soluções** e selecione **Editar SCD.csproj** ou **Editar SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="1ad72-177">Em seguida, adicione as seguintes linhas realçadas ao arquivo:</span><span class="sxs-lookup"><span data-stu-id="1ad72-177">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="1ad72-178">Crie um build de depuração do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="1ad72-179">Selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="1ad72-180">Você também pode compilar e executar o build de Depuração do aplicativo selecionando **Depurar** > **Iniciar Depuração**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="1ad72-181">Essa etapa de depuração permite identificar problemas com seu aplicativo quando ele está em execução em sua plataforma de host.</span><span class="sxs-lookup"><span data-stu-id="1ad72-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="1ad72-182">Ainda será necessário testá-lo em cada uma de suas plataformas de destino.</span><span class="sxs-lookup"><span data-stu-id="1ad72-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="1ad72-183">Se você tiver habilitado o modo invariável de globalização, certifique-se principalmente de testar se a ausência de dados que levam em conta a cultura é adequada para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="1ad72-184">Após concluir a depuração, será possível publicar sua implantação independente:</span><span class="sxs-lookup"><span data-stu-id="1ad72-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="1ad72-185">Visual Studio 15.6 e versões anteriores</span><span class="sxs-lookup"><span data-stu-id="1ad72-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="1ad72-186">Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.</span><span class="sxs-lookup"><span data-stu-id="1ad72-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="1ad72-187">Para publicar seu aplicativo do Visual Studio, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1ad72-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="1ad72-188">Defina as plataformas às quais seu aplicativo se destinará.</span><span class="sxs-lookup"><span data-stu-id="1ad72-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="1ad72-189">Clique com o botão direito do mouse no projeto (e não na solução) no **Gerenciador de Soluções** e selecione **Editar SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="1ad72-190">Crie uma marcação `<RuntimeIdentifiers>` na seção `<PropertyGroup>` de seu arquivo *csproj* que define as plataformas de destino do seu aplicativo e especifique o RID (identificador de tempo de execução) de cada plataforma que você selecionar.</span><span class="sxs-lookup"><span data-stu-id="1ad72-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="1ad72-191">Observe que você também precisa adicionar um ponto e vírgula para separar os RIDs.</span><span class="sxs-lookup"><span data-stu-id="1ad72-191">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="1ad72-192">Consulte o [Catálogo de Identificador de Tempo de Execução](../rid-catalog.md) para obter uma lista de identificadores de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1ad72-192">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="1ad72-193">Por exemplo, o exemplo a seguir indica que o aplicativo é executado em sistemas operacionais Windows 10 de 64 bits e no sistema de operacional OS X Versão 10.11 de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1ad72-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="1ad72-194">Observe que o elemento `<RuntimeIdentifiers>` pode entrar em qualquer `<PropertyGroup>` que você tenha em seu arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="1ad72-194">Note that the `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="1ad72-195">Um arquivo *csproj* de exemplo completo aparece mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="1ad72-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="1ad72-196">Publique seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-196">Publish your app.</span></span>

   <span data-ttu-id="1ad72-197">Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.</span><span class="sxs-lookup"><span data-stu-id="1ad72-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="1ad72-198">Para publicar seu aplicativo do Visual Studio, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1ad72-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="1ad72-199">Altere a configuração da solução de **Depuração** para **Lançamento** na barra de ferramentas para compilar uma versão de lançamento (em vez de uma de depuração) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="1ad72-200">Clique com o botão direito do mouse no projeto (e não na solução) no **Gerenciador de Soluções** e selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="1ad72-201">Na guia **Publicar**, selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="1ad72-202">O Visual Studio grava os arquivos que compõem seu aplicativo no sistema de arquivos local.</span><span class="sxs-lookup"><span data-stu-id="1ad72-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="1ad72-203">A guia **Publicar** agora mostra um único perfil **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="1ad72-204">As configurações do perfil são mostradas na seção **Resumo** da guia. **Tempo de Execução de Destino** identifica qual tempo de execução foi publicado e **Local de Destino** identifica o local em que os arquivos da implantação autocontida foram gravados.</span><span class="sxs-lookup"><span data-stu-id="1ad72-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="1ad72-205">Por padrão, o Visual Studio grava todos os arquivos publicados em um único diretório.</span><span class="sxs-lookup"><span data-stu-id="1ad72-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="1ad72-206">Para sua conveniência, é melhor criar perfis separados para cada tempo de execução de destino e colocar os arquivos publicados em um diretório específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="1ad72-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="1ad72-207">Isso envolve a criação de um perfil de publicação separado para cada plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="1ad72-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="1ad72-208">Agora recompile o aplicativo para cada plataforma fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1ad72-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="1ad72-209">Selecione **Criar novo perfil** na caixa de diálogo **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="1ad72-210">Na caixa de diálogo **Escolher um destino de publicação**, altere o local de **Escolher uma pasta** para *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="1ad72-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="1ad72-211">Selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-211">Select **OK**.</span></span>

         1. <span data-ttu-id="1ad72-212">Selecione o novo perfil (**FolderProfile1**) na lista de perfis e certifique-se de que o **Tempo de Execução de Destino** é `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="1ad72-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="1ad72-213">Se não for, selecione **Configurações**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="1ad72-214">Na caixa de diálogo **Configurações de Perfil**, altere o **Tempo de Execução de Destino** para `win10-x64` e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="1ad72-215">Caso contrário, selecione **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="1ad72-216">Selecione **Publicar** para publicar seu aplicativo para plataformas Windows 10 de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1ad72-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="1ad72-217">Siga as etapas anteriores novamente para criar um perfil para a plataforma `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="1ad72-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="1ad72-218">O **Local de Destino** é *bin\Release\PublishOutput\osx.10.11-x64* e o **Tempo de Execução de Destino** é `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="1ad72-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="1ad72-219">O nome que o Visual Studio atribui a este perfil é **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="1ad72-220">Observe que cada local de destino contém o conjunto completo de arquivos (arquivos do seu aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-220">Note that each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="1ad72-221">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1ad72-222">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="1ad72-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1ad72-223">Você pode optar por não empacotá-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="1ad72-224">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="1ad72-225">Implante os arquivos publicados na maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="1ad72-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="1ad72-226">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1ad72-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="1ad72-227">A seguir está o arquivo *csproj* completo para esse projeto.</span><span class="sxs-lookup"><span data-stu-id="1ad72-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="1ad72-228">Visual Studio 15.7 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="1ad72-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="1ad72-229">Depois de ter depurado e testado o programa, crie os arquivos a serem implantados com seu aplicativo para cada plataforma à qual ele se destina.</span><span class="sxs-lookup"><span data-stu-id="1ad72-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="1ad72-230">Isso envolve a criação de um perfil separado para cada plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="1ad72-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="1ad72-231">Para cada plataforma que seu aplicativo direciona, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1ad72-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="1ad72-232">Crie um perfil para sua plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="1ad72-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="1ad72-233">Se este for o primeiro perfil que você criou, clique com o botão direito do mouse no projeto (não na solução) no **Gerenciador de Soluções** e selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="1ad72-234">Se você já criou um perfil, clique com o botão direito do mouse no projeto para abrir a caixa de diálogo **Publicar** se ela ainda não estiver aberta.</span><span class="sxs-lookup"><span data-stu-id="1ad72-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="1ad72-235">Em seguida, selecione **Novo perfil**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="1ad72-236">A caixa de diálogo **Escolher um destino de publicação** é aberta.</span><span class="sxs-lookup"><span data-stu-id="1ad72-236">The **Pick a Publish Target** dialog box opens.</span></span>
  
1. <span data-ttu-id="1ad72-237">Selecione o local em que o Visual Studio publica seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="1ad72-238">Se você apenas estiver publicando em uma única plataforma, será possível aceitar o valor padrão na caixa de texto **Escolher uma pasta**; isso publicará a implantação dependente de estrutura do seu aplicativo no diretório \*\<diretório-do-projeto>\bin\Release\netcoreapp2.1\publish\*.</span><span class="sxs-lookup"><span data-stu-id="1ad72-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework dependent deployment of your application to the \*\<project-directory>\bin\Release\netcoreapp2.1\publish\* directory.</span></span>

   <span data-ttu-id="1ad72-239">Se você estiver publicando em mais de uma plataforma, acrescente uma cadeia de caracteres que identifique a plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="1ad72-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="1ad72-240">Por exemplo, se você acrescentar a cadeia de caracteres "linux" ao caminho do arquivo, o Visual Studio publicará a implantação dependente da estrutura do seu aplicativo no diretório *\<diretório-do-projeto>\bin\Release\netcoreapp2.1\publish\linux*.</span><span class="sxs-lookup"><span data-stu-id="1ad72-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="1ad72-241">Crie o perfil selecionando o ícone de lista suspensa ao lado do botão **Publicar** e selecionando **Criar perfil**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="1ad72-242">Em seguida, selecione o botão **Criar perfil** para criar o perfil.</span><span class="sxs-lookup"><span data-stu-id="1ad72-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="1ad72-243">Indique que você está publicando uma implantação independente e defina uma plataforma que seu aplicativo direcionará.</span><span class="sxs-lookup"><span data-stu-id="1ad72-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="1ad72-244">Na caixa de diálogo **Publicar**, selecione o link **Configurar** para abrir a caixa de diálogo **Configurações de perfil**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="1ad72-245">Selecione **Independente** na caixa de listagem **Modo de implantação**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="1ad72-246">Na caixa de listagem **Tempo de execução de destino**, selecione uma das plataformas que seu aplicativo direciona.</span><span class="sxs-lookup"><span data-stu-id="1ad72-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="1ad72-247">Selecione **Salvar** para aceitar suas alterações e fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="1ad72-248">Nomeie seu perfil.</span><span class="sxs-lookup"><span data-stu-id="1ad72-248">Name your profile.</span></span>

   1. <span data-ttu-id="1ad72-249">Selecione **Ações** > **Renomear perfil** para nomear seu perfil.</span><span class="sxs-lookup"><span data-stu-id="1ad72-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="1ad72-250">Atribua um nome ao seu perfil que identifique a plataforma de destino e, em seguida, selecione \**Salvar*.</span><span class="sxs-lookup"><span data-stu-id="1ad72-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="1ad72-251">Repita essas etapas para definir quaisquer plataformas de destino adicionais que seu aplicativo direciona.</span><span class="sxs-lookup"><span data-stu-id="1ad72-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="1ad72-252">Você configurou seus perfis e agora está pronto para publicar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="1ad72-253">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="1ad72-253">To do this:</span></span>

   1. <span data-ttu-id="1ad72-254">Se a janela **Publicar** não estiver aberta no momento, clique com o botão direito do mouse no projeto (não na solução) no **Gerenciador de Soluções** e selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="1ad72-255">Selecione o perfil que você deseja publicar e, em seguida, selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="1ad72-256">Faça isso para cada perfil a ser publicado.</span><span class="sxs-lookup"><span data-stu-id="1ad72-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="1ad72-257">Observe que cada local de destino (no caso de nosso exemplo, bin\release\netcoreapp2.1\publish\\*profile-name* contém o conjunto completo de arquivos (seus arquivos de aplicativo e todos os arquivos do .NET Core) necessários para iniciar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-257">Note that each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="1ad72-258">Junto com os arquivos do aplicativo, o processo de publicação emite um arquivo de banco de dados do programa (.pdb) que contém informações de depuração sobre seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1ad72-259">O arquivo é útil principalmente para exceções de depuração.</span><span class="sxs-lookup"><span data-stu-id="1ad72-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1ad72-260">Você pode optar por não empacotá-lo com os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="1ad72-261">No entanto, você deve salvá-lo no caso de desejar depurar o build de lançamento para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="1ad72-262">Implante os arquivos publicados na maneira que desejar.</span><span class="sxs-lookup"><span data-stu-id="1ad72-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="1ad72-263">Por exemplo, você pode empacotá-los em um arquivo zip, usar um simples comando `copy` ou implantá-los com qualquer pacote de instalação de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="1ad72-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="1ad72-264">A seguir está o arquivo *csproj* completo para esse projeto.</span><span class="sxs-lookup"><span data-stu-id="1ad72-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1ad72-265">Além disso, o Visual Studio cria um perfil de publicação separado (\*.pubxml) para cada plataforma que você direciona.</span><span class="sxs-lookup"><span data-stu-id="1ad72-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="1ad72-266">Por exemplo, o arquivo para nosso perfil do linux (linux.pubxml) aparece da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1ad72-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121. 
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="1ad72-267">Implantação autocontida com dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="1ad72-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="1ad72-268">Implantar uma implantação autocontida com uma ou mais dependências de terceiros envolve adicionar as dependências.</span><span class="sxs-lookup"><span data-stu-id="1ad72-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="1ad72-269">As etapas adicionais a seguir são necessárias antes de ser possível compilar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1ad72-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="1ad72-270">Use o **Gerenciador de Pacotes NuGet** para adicionar uma referência a um pacote NuGet ao projeto e se o pacote ainda não estiver disponível no sistema, instale-o.</span><span class="sxs-lookup"><span data-stu-id="1ad72-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="1ad72-271">Para abrir o gerenciador de pacotes, selecione **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Gerenciar Pacotes NuGet para a Solução**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="1ad72-272">Confirme se `Newtonsoft.Json` está instalado em seu sistema e, se não estiver, instale-o.</span><span class="sxs-lookup"><span data-stu-id="1ad72-272">Confirm that `Newtonsoft.Json` is installed on your system and, if it is not, install it.</span></span> <span data-ttu-id="1ad72-273">A guia **Instalados** lista os pacotes NuGet instalados no sistema.</span><span class="sxs-lookup"><span data-stu-id="1ad72-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="1ad72-274">Se `Newtonsoft.Json` não estiver listado, selecione a guia **Procurar** e insira "Newtonsoft.Json" na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1ad72-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="1ad72-275">Selecione `Newtonsoft.Json` e, no painel direito, selecione seu projeto antes de selecionar **Instalar**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="1ad72-276">Se `Newtonsoft.Json` já estiver instalado no sistema, adicione-o ao projeto selecionando o projeto no painel direito da guia **Gerenciar Pacotes para a Solução**.</span><span class="sxs-lookup"><span data-stu-id="1ad72-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="1ad72-277">A seguir está o arquivo *csproj* completo para esse projeto:</span><span class="sxs-lookup"><span data-stu-id="1ad72-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earliertabvs156"></a>[<span data-ttu-id="1ad72-278">Visual Studio 15.6 e versões anteriores</span><span class="sxs-lookup"><span data-stu-id="1ad72-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

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

# <a name="visual-studio-157-and-latertabvs157"></a>[<span data-ttu-id="1ad72-279">Visual Studio 15.7 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="1ad72-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="1ad72-280">Quando você implanta seu aplicativo, todas as dependências de terceiros usadas em seu aplicativo também contém os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ad72-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="1ad72-281">As bibliotecas de terceiros não são necessárias no sistema em que o aplicativo está em execução.</span><span class="sxs-lookup"><span data-stu-id="1ad72-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="1ad72-282">Observe que você só pode implantar uma implantação autocontida com uma biblioteca de terceiros para plataformas compatíveis com essa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="1ad72-282">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="1ad72-283">Isso é semelhante a ter dependências de terceiros com dependências nativas em sua implantação dependente de estrutura, em que as dependências nativas não existem na plataforma de destino a menos que elas tenham sido instaladas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1ad72-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ad72-284">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ad72-284">See also</span></span>

* [<span data-ttu-id="1ad72-285">Implantação de um aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="1ad72-285">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="1ad72-286">Catálogo do Identificador de Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1ad72-286">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
