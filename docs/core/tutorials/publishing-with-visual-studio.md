---
title: Publicar um aplicativo de console do .NET Core usando o Visual Studio
description: A publicação cria o conjunto de arquivos necessários para executar um aplicativo .NET Core.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: afbffa5dc8a620836ec1433a095face46c32df90
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811309"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="f2384-103">Tutorial: publicar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f2384-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="f2384-104">Este tutorial mostra como publicar um aplicativo de console para que outros usuários possam executá-lo.</span><span class="sxs-lookup"><span data-stu-id="f2384-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="f2384-105">A publicação cria o conjunto de arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="f2384-106">Para implantar os arquivos, copie-os para o computador de destino.</span><span class="sxs-lookup"><span data-stu-id="f2384-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2384-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f2384-107">Prerequisites</span></span>

- <span data-ttu-id="f2384-108">Este tutorial funciona com o aplicativo de console que você cria em [criar um aplicativo de console do .NET Core no Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f2384-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="f2384-109">Publicar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f2384-109">Publish the app</span></span>

1. <span data-ttu-id="f2384-110">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f2384-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="f2384-111">Abra o projeto *HelloWorld* que você criou em [criar um aplicativo de console .NET Core no Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="f2384-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="f2384-112">Verifique se o Visual Studio está usando a configuração de Build de versão.</span><span class="sxs-lookup"><span data-stu-id="f2384-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="f2384-113">Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="f2384-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Barra de ferramentas do Visual Studio com build de versão selecionado](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="f2384-115">Clique com o botão direito do mouse no projeto **HelloWorld** (não na solução HelloWorld) e selecione **publicar** no menu.</span><span class="sxs-lookup"><span data-stu-id="f2384-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Menu de contexto Publicar do Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="f2384-117">Na guia **destino** da página **publicar** , selecione **pasta**e, em seguida, selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="f2384-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Escolher um destino de publicação no Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="f2384-119">Na guia **local** da página **publicar** , selecione **concluir**.</span><span class="sxs-lookup"><span data-stu-id="f2384-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Guia local da página de publicação do Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="f2384-121">Na guia **publicar** da janela **publicar** , selecione **publicar**.</span><span class="sxs-lookup"><span data-stu-id="f2384-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Janela Publicar do Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="f2384-123">Inspecionar os arquivos</span><span class="sxs-lookup"><span data-stu-id="f2384-123">Inspect the files</span></span>

<span data-ttu-id="f2384-124">Por padrão, o processo de publicação cria uma implantação dependente de estrutura, que é um tipo de implantação em que o aplicativo publicado é executado no computador que tem o tempo de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="f2384-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="f2384-125">Os usuários podem executar o aplicativo publicado clicando duas vezes no executável ou emitindo o `dotnet HelloWorld.dll` comando de um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f2384-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="f2384-126">Nas etapas a seguir, você examinará os arquivos criados pelo processo de publicação.</span><span class="sxs-lookup"><span data-stu-id="f2384-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="f2384-127">Em **Gerenciador de soluções**, selecione **Mostrar todos os arquivos**.</span><span class="sxs-lookup"><span data-stu-id="f2384-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="f2384-128">Na pasta do projeto, expanda *bin/Release/netcoreapp 3.1/publicar*.</span><span class="sxs-lookup"><span data-stu-id="f2384-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Gerenciador de Soluções mostrando os arquivos publicados":::

   <span data-ttu-id="f2384-130">Como mostra a imagem, a saída publicada inclui os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="f2384-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="f2384-131">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="f2384-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="f2384-132">Este é o arquivo de dependências de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="f2384-133">Ele define os componentes do .NET Core e as bibliotecas (incluindo a biblioteca de vínculo dinâmico que contém seu aplicativo) necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="f2384-134">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="f2384-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="f2384-135">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="f2384-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="f2384-136">Esta é a versão de [implantação dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-deployment) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="f2384-137">Para executar essa biblioteca de vínculo dinâmico, digite `dotnet HelloWorld.dll` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f2384-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="f2384-138">Esse método de execução do aplicativo funciona em qualquer plataforma que tenha o tempo de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="f2384-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="f2384-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="f2384-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="f2384-140">Esta é a versão [executável dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-executable) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="f2384-141">Para executá-lo, insira `HelloWorld.exe` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="f2384-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="f2384-142">O arquivo é específico do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f2384-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="f2384-143">*HelloWorld.pdb* (opcional para implantação)</span><span class="sxs-lookup"><span data-stu-id="f2384-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="f2384-144">Este é o arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="f2384-144">This is the debug symbols file.</span></span> <span data-ttu-id="f2384-145">Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="f2384-146">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="f2384-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="f2384-147">Este é o arquivo de configuração de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f2384-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="f2384-148">Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado.</span><span class="sxs-lookup"><span data-stu-id="f2384-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="f2384-149">Você também pode adicionar opções de configuração a ela.</span><span class="sxs-lookup"><span data-stu-id="f2384-149">You can also add configuration options to it.</span></span> <span data-ttu-id="f2384-150">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f2384-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="f2384-151">Executar o aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="f2384-151">Run the published app</span></span>

1. <span data-ttu-id="f2384-152">Em **Gerenciador de soluções**, clique com o botão direito do mouse na pasta de *publicação* e selecione **Copiar caminho completo**.</span><span class="sxs-lookup"><span data-stu-id="f2384-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="f2384-153">Abra um prompt de comando e navegue até a pasta de *publicação* .</span><span class="sxs-lookup"><span data-stu-id="f2384-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="f2384-154">Para fazer isso, insira `cd` e cole o caminho completo.</span><span class="sxs-lookup"><span data-stu-id="f2384-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="f2384-155">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f2384-155">For example:</span></span>

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="f2384-156">Execute o aplicativo usando o executável:</span><span class="sxs-lookup"><span data-stu-id="f2384-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="f2384-157">Insira `HelloWorld.exe` e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f2384-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f2384-158">Insira um nome em resposta ao prompt e pressione qualquer tecla para sair.</span><span class="sxs-lookup"><span data-stu-id="f2384-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="f2384-159">Execute o aplicativo usando o `dotnet` comando:</span><span class="sxs-lookup"><span data-stu-id="f2384-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="f2384-160">Insira `dotnet HelloWorld.dll` e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f2384-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="f2384-161">Insira um nome em resposta ao prompt e pressione qualquer tecla para sair.</span><span class="sxs-lookup"><span data-stu-id="f2384-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f2384-162">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="f2384-162">Additional resources</span></span>

- [<span data-ttu-id="f2384-163">Implantação de aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="f2384-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="f2384-164">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f2384-164">Next steps</span></span>

<span data-ttu-id="f2384-165">Neste tutorial, você publicou um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="f2384-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="f2384-166">No próximo tutorial, você criará uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="f2384-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2384-167">Criar uma biblioteca .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f2384-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
