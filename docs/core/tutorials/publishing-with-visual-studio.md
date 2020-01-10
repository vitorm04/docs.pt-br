---
title: Publicar seu aplicativo .NET Core Olá, Mundo com o Visual Studio
description: A publicação cria o conjunto de arquivos necessários para executar seu aplicativo .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 485d62ce67f284fe1bbe931dcaa00671be154f35
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715364"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="cdde4-103">Publicar seu aplicativo .NET Core Olá, Mundo com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cdde4-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="cdde4-104">Em [criar um aplicativo Olá, mundo com o .NET Core no Visual Studio](with-visual-studio.md), você criou um aplicativo de console Olá, mundo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="cdde4-105">Em [depurar seu aplicativo Olá, mundo com o Visual Studio](debugging-with-visual-studio.md), você o testou usando o depurador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cdde4-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="cdde4-106">Agora que você tem certeza de que ele funciona conforme o esperado, publique-o para que outros usuários possam executá-lo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="cdde4-107">A publicação cria o conjunto de arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="cdde4-108">Para implantar os arquivos, copie-os para o computador de destino.</span><span class="sxs-lookup"><span data-stu-id="cdde4-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="cdde4-109">Publique o aplicativo</span><span class="sxs-lookup"><span data-stu-id="cdde4-109">Publish the app</span></span>

1. <span data-ttu-id="cdde4-110">Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="cdde4-111">Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="cdde4-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barra de ferramentas do Visual Studio com build de versão selecionado](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="cdde4-113">Clique com o botão direito do mouse no projeto **HelloWorld** (e não na solução HelloWorld) e selecione **Publicar** no menu.</span><span class="sxs-lookup"><span data-stu-id="cdde4-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="cdde4-114">(Você também pode selecionar **publicar HelloWorld** no menu principal do **Build** .)</span><span class="sxs-lookup"><span data-stu-id="cdde4-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Menu de contexto Publicar do Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. <span data-ttu-id="cdde4-116">Na página **escolha um destino de publicação** , selecione **pasta**e, em seguida, selecione **Criar perfil**.</span><span class="sxs-lookup"><span data-stu-id="cdde4-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Escolher um destino de publicação no Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. <span data-ttu-id="cdde4-118">Na página **publicar** , selecione **publicar**.</span><span class="sxs-lookup"><span data-stu-id="cdde4-118">On the **Publish** page, select **Publish**.</span></span>

   ![Janela Publicar do Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a><span data-ttu-id="cdde4-120">Inspecionar os arquivos</span><span class="sxs-lookup"><span data-stu-id="cdde4-120">Inspect the files</span></span>

<span data-ttu-id="cdde4-121">O processo de publicação cria uma implantação dependente de estrutura, que é um tipo de implantação em que o aplicativo publicado é executado em qualquer plataforma com suporte do .NET Core com o .NET Core instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="cdde4-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="cdde4-122">Os usuários podem executar o aplicativo publicado clicando duas vezes no executável ou emitindo o comando `dotnet HelloWorld.dll` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="cdde4-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="cdde4-123">Nas etapas a seguir, você examinará os arquivos criados pelo processo de publicação.</span><span class="sxs-lookup"><span data-stu-id="cdde4-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="cdde4-124">Abra um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="cdde4-124">Open a command prompt.</span></span>

   <span data-ttu-id="cdde4-125">Uma maneira de abrir um prompt de comando é inserir o **prompt de comando** (ou **cmd** por curto) na caixa de pesquisa na barra de tarefas do Windows.</span><span class="sxs-lookup"><span data-stu-id="cdde4-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="cdde4-126">Selecione o **prompt de comando** aplicativo da área de trabalho ou pressione **Enter** se ele já estiver selecionado nos resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="cdde4-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="cdde4-127">Navegue até o aplicativo publicado no subdiretório *bin\Release\netcoreapp3.1\publish* do diretório do projeto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Janela de console mostrando arquivos publicados](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="cdde4-129">Como mostra a imagem, a saída publicada inclui os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="cdde4-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="cdde4-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="cdde4-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="cdde4-131">Este é o arquivo de dependências de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="cdde4-132">Ele define os componentes do .NET Core e as bibliotecas (incluindo a biblioteca de vínculo dinâmico que contém seu aplicativo) necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="cdde4-133">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="cdde4-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="cdde4-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="cdde4-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="cdde4-135">Esta é a versão de [implantação dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-deployment) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="cdde4-136">Para executar essa biblioteca de vínculo dinâmico, insira `dotnet HelloWorld.dll` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="cdde4-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="cdde4-137">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="cdde4-137">*HelloWorld.exe*</span></span>
      
         <span data-ttu-id="cdde4-138">Esta é a versão [executável dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-executable) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="cdde4-139">Para executá-lo, insira `HelloWorld.exe` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="cdde4-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="cdde4-140">*HelloWorld.pdb* (opcional para implantação)</span><span class="sxs-lookup"><span data-stu-id="cdde4-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="cdde4-141">Este é o arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="cdde4-141">This is the debug symbols file.</span></span> <span data-ttu-id="cdde4-142">Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="cdde4-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="cdde4-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="cdde4-144">Este é o arquivo de configuração de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cdde4-144">This is the application's runtime configuration file.</span></span> <span data-ttu-id="cdde4-145">Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado.</span><span class="sxs-lookup"><span data-stu-id="cdde4-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="cdde4-146">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="cdde4-146">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cdde4-147">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="cdde4-147">Additional resources</span></span>

- [<span data-ttu-id="cdde4-148">Implantação de aplicativos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cdde4-148">.NET Core application deployment</span></span>](../deploying/index.md)
