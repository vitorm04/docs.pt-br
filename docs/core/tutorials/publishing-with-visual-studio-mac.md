---
title: Publicar um aplicativo de console do .NET Core usando Visual Studio para Mac
description: A publicação cria o conjunto de arquivos necessários para executar um aplicativo .NET Core.
ms.date: 06/08/2020
ms.openlocfilehash: 38b656ac919dfb8b710a97c5d7fc63479e3fa367
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811399"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="af938-103">Tutorial: publicar um aplicativo de console do .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="af938-103">Tutorial: Publish a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="af938-104">Este tutorial mostra como publicar um aplicativo de console para que outros usuários possam executá-lo.</span><span class="sxs-lookup"><span data-stu-id="af938-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="af938-105">A publicação cria o conjunto de arquivos necessários para executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="af938-106">Para implantar os arquivos, copie-os para o computador de destino.</span><span class="sxs-lookup"><span data-stu-id="af938-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af938-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="af938-107">Prerequisites</span></span>

- <span data-ttu-id="af938-108">Este tutorial funciona com o aplicativo de console que você cria em [criar um aplicativo de console do .NET Core no Visual Studio para Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="af938-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="af938-109">Publicar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="af938-109">Publish the app</span></span>

1. <span data-ttu-id="af938-110">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="af938-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="af938-111">Abra o projeto HelloWorld que você criou em [criar um aplicativo de console do .NET Core no Visual Studio para Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="af938-111">Open the HelloWorld project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="af938-112">Certifique-se de que o Visual Studio esteja compilando a versão de lançamento de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="af938-113">Se necessário, altere a configuração de build na barra de ferramentas de **Depuração** para **Lançamento**.</span><span class="sxs-lookup"><span data-stu-id="af938-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Barra de ferramentas do Visual Studio com build de versão selecionado":::

1. <span data-ttu-id="af938-115">No menu principal, escolha **criar**  >  **publicar na pasta...**.</span><span class="sxs-lookup"><span data-stu-id="af938-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Menu de contexto Publicar do Visual Studio":::

1. <span data-ttu-id="af938-117">Na caixa de diálogo **publicar na pasta** , selecione **publicar**.</span><span class="sxs-lookup"><span data-stu-id="af938-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Caixa de diálogo Publicar na pasta do Visual Studio":::

   <span data-ttu-id="af938-119">A pasta de publicação é aberta, mostrando os arquivos que foram criados.</span><span class="sxs-lookup"><span data-stu-id="af938-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="Publicar pasta":::

1. <span data-ttu-id="af938-121">Selecione o ícone de engrenagem e selecione **Copiar "publicar" como nome de caminho** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="af938-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Copiar caminho para a pasta de publicação":::

## <a name="inspect-the-files"></a><span data-ttu-id="af938-123">Inspecionar os arquivos</span><span class="sxs-lookup"><span data-stu-id="af938-123">Inspect the files</span></span>

<span data-ttu-id="af938-124">O processo de publicação cria uma implantação dependente de estrutura, que é um tipo de implantação em que o aplicativo publicado é executado em um computador que tem o tempo de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="af938-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="af938-125">Os usuários podem executar o aplicativo publicado executando o `dotnet HelloWorld.dll` comando em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="af938-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="af938-126">Como mostra a imagem anterior, a saída publicada inclui os seguintes arquivos:</span><span class="sxs-lookup"><span data-stu-id="af938-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="af938-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="af938-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="af938-128">Este é o arquivo de dependências de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="af938-129">Ele define os componentes do .NET Core e as bibliotecas (incluindo a biblioteca de vínculo dinâmico que contém seu aplicativo) necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="af938-130">Para obter mais informações, consulte [arquivos de configuração de tempo de execução](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="af938-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="af938-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="af938-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="af938-132">Esta é a versão de [implantação dependente de estrutura](../deploying/deploy-with-cli.md#framework-dependent-deployment) do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="af938-133">Para executar essa biblioteca de vínculo dinâmico, digite `dotnet HelloWorld.dll` em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="af938-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="af938-134">Esse método de execução do aplicativo funciona em qualquer plataforma que tenha o tempo de execução do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="af938-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

* <span data-ttu-id="af938-135">*HelloWorld.pdb* (opcional para implantação)</span><span class="sxs-lookup"><span data-stu-id="af938-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="af938-136">Este é o arquivo de símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="af938-136">This is the debug symbols file.</span></span> <span data-ttu-id="af938-137">Não é necessário implantar esse arquivo juntamente com seu aplicativo, embora você deva salvá-lo caso precise depurar a versão publicada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="af938-138">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="af938-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="af938-139">Este é o arquivo de configuração de tempo de execução do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="af938-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="af938-140">Identifica a versão do .NET Core com base na qual o aplicativo foi criado para ser executado.</span><span class="sxs-lookup"><span data-stu-id="af938-140">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="af938-141">Você também pode adicionar opções de configuração a ela.</span><span class="sxs-lookup"><span data-stu-id="af938-141">You can also add configuration options to it.</span></span> <span data-ttu-id="af938-142">Para obter mais informações, consulte [definições de configuração de tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="af938-142">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="af938-143">Executar o aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="af938-143">Run the published app</span></span>

1. <span data-ttu-id="af938-144">Abra um terminal e navegue até a pasta de *publicação* .</span><span class="sxs-lookup"><span data-stu-id="af938-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="af938-145">Para fazer isso, insira `cd` e cole o caminho que você copiou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="af938-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="af938-146">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="af938-146">For example:</span></span>

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. <span data-ttu-id="af938-147">Execute o aplicativo usando o `dotnet` comando:</span><span class="sxs-lookup"><span data-stu-id="af938-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="af938-148">Insira `dotnet HelloWorld.dll` e pressione <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="af938-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="af938-149">Insira um nome em resposta ao prompt e pressione qualquer tecla para sair.</span><span class="sxs-lookup"><span data-stu-id="af938-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="af938-150">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="af938-150">Additional resources</span></span>

- [<span data-ttu-id="af938-151">Implantação de aplicativo .NET Core</span><span class="sxs-lookup"><span data-stu-id="af938-151">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="af938-152">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="af938-152">Next steps</span></span>

<span data-ttu-id="af938-153">Neste tutorial, você publicou um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="af938-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="af938-154">No próximo tutorial, você criará uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="af938-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af938-155">Criar uma biblioteca de .NET Standard no Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="af938-155">Create a .NET Standard library in Visual Studio for mac</span></span>](library-with-visual-studio-mac.md)
