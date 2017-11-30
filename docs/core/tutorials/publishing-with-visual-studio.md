---
title: "Publicar um aplicativo Olá, Mundo com o Visual Studio 2017"
description: "A publicação cria o conjunto de arquivos necessários para executar seu aplicativo."
keywords: ".NET, .NET Core, aplicativo do console, publicação, implantação"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.openlocfilehash: a3e5bda5c99144c9ab5bbaf5e2f5566261af4813
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="fb535-104">Publicar um aplicativo Olá, Mundo com o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fb535-104">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="fb535-105">Em [Build a C# Hello World Application with .NET Core in Visual Studio 2017](with-visual-studio.md) (Compilar um aplicativo Olá, Mundo em C# com o .NET Core no Visual Studio 2017) ou [Build a Visual Basic Hello World Application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md) (Compilar um aplicativo Olá, Mundo em Visual Basic com o .NET Core no Visual Studio 2017), você compilou um aplicativo de console Olá, Mundo.</span><span class="sxs-lookup"><span data-stu-id="fb535-105">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="fb535-106">Em [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) (Depurar um aplicativo Olá, Mundo em C# com o Visual Studio 2017), você o testou usando o depurador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb535-106">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="fb535-107">Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo.</span><span class="sxs-lookup"><span data-stu-id="fb535-107">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="fb535-108">A publicação cria o conjunto de arquivos necessários para executar seu aplicativo e você pode implantá-los copiando-os para um computador de destino.</span><span class="sxs-lookup"><span data-stu-id="fb535-108">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="fb535-109">Para publicar e executar seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="fb535-109">To publish and run your application:</span></span> 

1. <span data-ttu-id="fb535-110">Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="fb535-111">Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="fb535-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="fb535-113">Clique com o botão direito do mouse no projeto **HelloWorld** (e não na solução HelloWorld) e selecione **Publicar** no menu.</span><span class="sxs-lookup"><span data-stu-id="fb535-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="fb535-114">Também é possível selecionar **Publicar Hello World** no menu principal **Compilação** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fb535-114">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/publish1.png)


   ![Barra de ferramentas do Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="fb535-117">Abra uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="fb535-117">Open a console window.</span></span> <span data-ttu-id="fb535-118">Por exemplo, na caixa de texto **Digite aqui para pesquisar** na barra de tarefas do Windows, insira `Command Prompt` (ou apenas `cmd`) e abra uma janela do console selecionando o aplicativo da área de trabalho **Prompt de Comando** ou pressionando Enter se ele estiver selecionado nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="fb535-118">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="fb535-119">Navegue até o aplicativo publicado no subdiretório `bin\release\PublishOutput` do diretório de projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-119">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="fb535-120">Como mostra a figura a seguir, a saída publicada inclui os seguintes quatro arquivos:</span><span class="sxs-lookup"><span data-stu-id="fb535-120">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="fb535-121">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="fb535-121">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="fb535-122">Arquivo de dependências de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-122">The application's runtime dependencies file.</span></span> <span data-ttu-id="fb535-123">Define os componentes principais do .NET e as bibliotecas (incluindo a biblioteca de vínculo dinâmico que contém seu aplicativo) necessária para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-123">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="fb535-124">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="fb535-124">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="fb535-125">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="fb535-125">*HelloWorld.dll*</span></span>

         <span data-ttu-id="fb535-126">O arquivo que contém seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-126">The file that contains your application.</span></span> <span data-ttu-id="fb535-127">É uma biblioteca de vínculo dinâmico que pode ser executada digitando o `dotnet HelloWorld.dll` comando na janela do console.</span><span class="sxs-lookup"><span data-stu-id="fb535-127">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="fb535-128">*HelloWorld.pdb* (opcional para implantação)</span><span class="sxs-lookup"><span data-stu-id="fb535-128">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="fb535-129">Um arquivo que contém os símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="fb535-129">A file that contains debug symbols.</span></span> <span data-ttu-id="fb535-130">Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-130">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="fb535-131">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="fb535-131">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="fb535-132">Arquivo de configuração de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb535-132">The application's runtime configuration file.</span></span> <span data-ttu-id="fb535-133">Identifica a versão do que seu aplicativo foi criado para ser executado .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fb535-133">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="fb535-134">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="fb535-134">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Janela de console mostrando arquivos publicados](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="fb535-136">O processo de publicação cria uma implantação dependente da estrutura, que é um tipo de implantação em que o aplicativo publicado será executado em qualquer plataforma com suporte pelo .NET Core com o .NET Core instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="fb535-136">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="fb535-137">Os usuários podem executar o aplicativo emitindo o comando `dotnet HelloWorld.dll` de uma janela de console.</span><span class="sxs-lookup"><span data-stu-id="fb535-137">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="fb535-138">Para saber mais sobre a publicação e implantação de aplicativos .NET Core, consulte [Implantação de aplicativos .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb535-138">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
