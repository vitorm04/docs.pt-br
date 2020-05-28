---
title: Publicar seu aplicativo .NET Core Olá, Mundo com o Visual Studio
description: A publicação cria o conjunto de arquivos necessários para executar seu aplicativo .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e4ef8c12f3e52faa7cf09058a98abae65b0dcfce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005071"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a><span data-ttu-id="7c10b-103">Tutorial: publicar um aplicativo de console do .NET Core com o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7c10b-103">Tutorial: Publish a .NET Core console application with Visual Studio</span></span>

<span data-ttu-id="7c10b-104">Este tutorial mostra como publicar um aplicativo de console para que outros usuários possam executá-lo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="7c10b-105">A publicação cria o conjunto de arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="7c10b-106">Para implantar os arquivos, copie-os para o computador de destino.</span><span class="sxs-lookup"><span data-stu-id="7c10b-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c10b-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7c10b-107">Prerequisites</span></span>

- <span data-ttu-id="7c10b-108">Este tutorial funciona com o aplicativo de console que você cria em [criar um aplicativo de console do .NET Core no Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="7c10b-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="7c10b-109">Publicar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="7c10b-109">Publish the app</span></span>

1. <span data-ttu-id="7c10b-110">Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="7c10b-111">Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="7c10b-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barra de ferramentas do Visual Studio com build de versão selecionado](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="7c10b-113">Clique com o botão direito do mouse no projeto **HelloWorld** (não na solução HelloWorld) e selecione **publicar** no menu.</span><span class="sxs-lookup"><span data-stu-id="7c10b-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Menu de contexto Publicar do Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="7c10b-115">Na guia **destino** da página **publicar** , selecione **pasta**e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="7c10b-115">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Escolher um destino de publicação no Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="7c10b-117">Na guia **local** da página **publicar** , selecione **concluir**.</span><span class="sxs-lookup"><span data-stu-id="7c10b-117">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Guia local da página de publicação do Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="7c10b-119">Na guia **publicar** da janela **publicar** , selecione **publicar**.</span><span class="sxs-lookup"><span data-stu-id="7c10b-119">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Janela Publicar do Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="7c10b-121">Inspecionar os arquivos</span><span class="sxs-lookup"><span data-stu-id="7c10b-121">Inspect the files</span></span>

<span data-ttu-id="7c10b-122">O processo de publicação cria uma implantação dependente de estrutura, que é um tipo de implantação em que o aplicativo publicado é executado no computador que tem o tempo de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="7c10b-122">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="7c10b-123">Os usuários podem executar o aplicativo publicado clicando duas vezes no executável ou emitindo o `dotnet HelloWorld.dll` comando de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7c10b-123">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="7c10b-124">Nas etapas a seguir, você examinará os arquivos criados pelo processo de publicação.</span><span class="sxs-lookup"><span data-stu-id="7c10b-124">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="7c10b-125">Em **Gerenciador de soluções**, selecione **Mostrar todos os arquivos**.</span><span class="sxs-lookup"><span data-stu-id="7c10b-125">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="7c10b-126">Na pasta do projeto, expanda *bin/Release/netcoreapp 3.1/publicar*.</span><span class="sxs-lookup"><span data-stu-id="7c10b-126">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Gerenciador de Soluções mostrando os arquivos publicados":::

   <span data-ttu-id="7c10b-128">Como mostra a imagem, a saída publicada inclui os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="7c10b-128">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="7c10b-129">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="7c10b-129">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="7c10b-130">Este é o arquivo de dependências de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-130">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="7c10b-131">Ele define os componentes do .NET Core e as bibliotecas (incluindo a biblioteca de vínculo dinâmico que contém seu aplicativo) necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-131">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="7c10b-132">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="7c10b-132">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="7c10b-133">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="7c10b-133">*HelloWorld.dll*</span></span>

         <span data-ttu-id="7c10b-134">Esta é a versão de [implantação dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-deployment) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-134">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="7c10b-135">Para executar essa biblioteca de vínculo dinâmico, digite `dotnet HelloWorld.dll` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7c10b-135">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="7c10b-136">*HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="7c10b-136">*HelloWorld.exe*</span></span>

         <span data-ttu-id="7c10b-137">Esta é a versão [executável dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-executable) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-137">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="7c10b-138">Para executá-lo, insira `HelloWorld.exe` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="7c10b-138">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="7c10b-139">*HelloWorld.pdb* (opcional para implantação)</span><span class="sxs-lookup"><span data-stu-id="7c10b-139">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="7c10b-140">Este é o arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="7c10b-140">This is the debug symbols file.</span></span> <span data-ttu-id="7c10b-141">Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-141">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="7c10b-142">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="7c10b-142">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="7c10b-143">Este é o arquivo de configuração de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-143">This is the application's run-time configuration file.</span></span> <span data-ttu-id="7c10b-144">Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado.</span><span class="sxs-lookup"><span data-stu-id="7c10b-144">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="7c10b-145">Você também pode adicionar opções de configuração a ela.</span><span class="sxs-lookup"><span data-stu-id="7c10b-145">You can also add configuration options to it.</span></span> <span data-ttu-id="7c10b-146">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="7c10b-146">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="7c10b-147">Executar o aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="7c10b-147">Run the published app</span></span>

1. <span data-ttu-id="7c10b-148">Em **Gerenciador de soluções**, clique com o botão direito do mouse na pasta de *publicação* e selecione **Copiar caminho completo**.</span><span class="sxs-lookup"><span data-stu-id="7c10b-148">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="7c10b-149">Abra um prompt de comando e navegue até a pasta de *publicação* .</span><span class="sxs-lookup"><span data-stu-id="7c10b-149">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="7c10b-150">Insira `cd` e cole o caminho completo.</span><span class="sxs-lookup"><span data-stu-id="7c10b-150">Enter `cd` and then paste the full path.</span></span> <span data-ttu-id="7c10b-151">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="7c10b-151">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="7c10b-152">Execute o aplicativo usando o executável:</span><span class="sxs-lookup"><span data-stu-id="7c10b-152">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="7c10b-153">Insira `HelloWorld.exe` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="7c10b-153">Enter `HelloWorld.exe` and press Enter.</span></span>

   1. <span data-ttu-id="7c10b-154">Insira um nome em resposta ao prompt e pressione qualquer tecla para sair.</span><span class="sxs-lookup"><span data-stu-id="7c10b-154">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="7c10b-155">Execute o aplicativo usando o `dotnet` comando:</span><span class="sxs-lookup"><span data-stu-id="7c10b-155">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="7c10b-156">Insira `dotnet HelloWorld.dll` e pressione Enter.</span><span class="sxs-lookup"><span data-stu-id="7c10b-156">Enter `dotnet HelloWorld.dll` and press Enter.</span></span>

   1. <span data-ttu-id="7c10b-157">Insira um nome em resposta ao prompt e pressione qualquer tecla para sair.</span><span class="sxs-lookup"><span data-stu-id="7c10b-157">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7c10b-158">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="7c10b-158">Additional resources</span></span>

- [<span data-ttu-id="7c10b-159">Implantação de aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="7c10b-159">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="7c10b-160">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7c10b-160">Next steps</span></span>

<span data-ttu-id="7c10b-161">Neste tutorial, você publicou um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="7c10b-161">In this tutorial, you published a console app.</span></span> <span data-ttu-id="7c10b-162">No próximo tutorial, você criará uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="7c10b-162">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c10b-163">Criar uma biblioteca .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7c10b-163">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
