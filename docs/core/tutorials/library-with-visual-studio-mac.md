---
title: Criar uma biblioteca de classes de .NET Standard usando Visual Studio para Mac
description: Saiba como criar uma biblioteca de classes de .NET Standard usando Visual Studio para Mac.
ms.date: 06/08/2020
ms.openlocfilehash: a78cc68d29095e4fefcaf1d3b2158d673b8892ec
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400559"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="3a57d-103">Tutorial: criar uma biblioteca de .NET Standard usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="3a57d-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="3a57d-104">Neste tutorial, você cria uma biblioteca de classes que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3a57d-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span> <span data-ttu-id="3a57d-105">Implemente-o como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md) para que você possa chamá-lo como se fosse um membro da <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="3a57d-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="3a57d-106">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3a57d-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="3a57d-107">Uma biblioteca de classes que tem como alvo .NET Standard 2,1 pode ser usada por um aplicativo que se destina a qualquer implementação .NET que ofereça suporte à versão 2,1 do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3a57d-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="3a57d-108">Ao concluir a biblioteca de classes, você pode distribuí-la como um componente de terceiros ou como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3a57d-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="3a57d-109">Seus comentários são muito importantes.</span><span class="sxs-lookup"><span data-stu-id="3a57d-109">Your feedback is highly valued.</span></span> <span data-ttu-id="3a57d-110">Há duas maneiras de enviar comentários à equipe de desenvolvimento no Visual Studio para Mac:</span><span class="sxs-lookup"><span data-stu-id="3a57d-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="3a57d-111">Em Visual Studio para Mac, selecione **ajuda**  >  **relatar um problema** no menu ou **relatar um problema** na tela de boas-vindas, que abre uma janela para o arquivamento de um relatório de bug.</span><span class="sxs-lookup"><span data-stu-id="3a57d-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="3a57d-112">Você pode acompanhar seus comentários no portal [Developer Community (Comunidade do Desenvolvedor)](https://aka.ms/feedback/report?space=41).</span><span class="sxs-lookup"><span data-stu-id="3a57d-112">You can track your feedback in the [Developer Community](https://aka.ms/feedback/report?space=41) portal.</span></span>
> - <span data-ttu-id="3a57d-113">Para fazer uma sugestão, selecione **ajuda**  >  **fornecer uma sugestão** no menu ou **forneça uma sugestão** na tela de boas-vindas, que leva você para a [página da Web do Visual Studio para Mac Developer Community](https://aka.ms/feedback/suggest?space=41).</span><span class="sxs-lookup"><span data-stu-id="3a57d-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://aka.ms/feedback/suggest?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a57d-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3a57d-114">Prerequisites</span></span>

* <span data-ttu-id="3a57d-115">[Instale Visual Studio para Mac versão 8,6 ou posterior](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="3a57d-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="3a57d-116">Selecione a opção para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a57d-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="3a57d-117">A instalação do Xamarin é opcional para o desenvolvimento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a57d-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="3a57d-118">Para obter mais informações, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="3a57d-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="3a57d-119">[Tutorial: instalar o Visual Studio para Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="3a57d-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="3a57d-120">[Versões do MacOS com suporte](../install/macos.md).</span><span class="sxs-lookup"><span data-stu-id="3a57d-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="3a57d-121">[Versões do .NET Core com suporte pelo Visual Studio para Mac](/visualstudio/mac/net-core-support).</span><span class="sxs-lookup"><span data-stu-id="3a57d-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="3a57d-122">Criar uma solução com um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="3a57d-122">Create a solution with a class library project</span></span>

<span data-ttu-id="3a57d-123">Uma solução do Visual Studio serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="3a57d-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="3a57d-124">Crie uma solução e um projeto de biblioteca de classes na solução.</span><span class="sxs-lookup"><span data-stu-id="3a57d-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="3a57d-125">Você adicionará mais projetos relacionados à mesma solução posteriormente.</span><span class="sxs-lookup"><span data-stu-id="3a57d-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="3a57d-126">Iniciar Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="3a57d-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="3a57d-127">Na janela iniciar, selecione **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="3a57d-128">Na caixa de diálogo **novo projeto** no nó **várias plataformas** , selecione **biblioteca** , em seguida, selecione o modelo de **biblioteca de .net Standard** e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library** , then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Caixa de diálogo Novo Projeto":::

1. <span data-ttu-id="3a57d-130">Na caixa de diálogo **configurar sua nova biblioteca de .net Standard** , escolha ".net Standard 2,1" e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="Escolha .NET Standard 2,1":::

1. <span data-ttu-id="3a57d-132">Nomeie o projeto "StringLibrary" e a solução "ClassLibraryProjects".</span><span class="sxs-lookup"><span data-stu-id="3a57d-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="3a57d-133">Deixe **criar um diretório de projeto dentro do diretório de solução** selecionado.</span><span class="sxs-lookup"><span data-stu-id="3a57d-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="3a57d-134">Selecione **Criar**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Opções da caixa de diálogo Novo projeto do Visual Studio para Mac":::

1. <span data-ttu-id="3a57d-136">No menu principal, selecione **Exibir**  >  **painéis**  >  **solução** e selecione o ícone de encaixe para manter o pad aberto.</span><span class="sxs-lookup"><span data-stu-id="3a57d-136">From the main menu, select **View** > **Pads** > **Solution** , and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Ícone de encaixe para o painel de solução":::

1. <span data-ttu-id="3a57d-138">No painel de **solução** , expanda o `StringLibrary` nó para revelar o arquivo de classe fornecido pelo modelo, *Class1.cs*.</span><span class="sxs-lookup"><span data-stu-id="3a57d-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="3a57d-139"><kbd>Ctrl</kbd>-clique no arquivo, selecione **renomear** no menu de contexto e renomeie o arquivo para *StringLibrary.cs*.</span><span class="sxs-lookup"><span data-stu-id="3a57d-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="3a57d-140">Abra o arquivo e substitua o conteúdo pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3a57d-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="3a57d-141">Pressione <kbd>⌘</kbd><kbd>S</kbd> (<kbd>Command</kbd> + <kbd>s</kbd>) para salvar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="3a57d-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="3a57d-142">Selecione **Erros** na margem da parte inferior da janela do IDE para abrir o painel **Erros**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="3a57d-143">Selecione o botão **Compilar Saída**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Margem inferior do IDE do Visual Studio para Mac mostrando o botão Erros":::

1. <span data-ttu-id="3a57d-145">Selecione **Compilar**  >  **compilar tudo** no menu.</span><span class="sxs-lookup"><span data-stu-id="3a57d-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="3a57d-146">A solução é compilada.</span><span class="sxs-lookup"><span data-stu-id="3a57d-146">The solution builds.</span></span> <span data-ttu-id="3a57d-147">O painel de saída da compilação mostra que a compilação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3a57d-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Painel de saída do Build do Visual Studio do painel Erros com a mensagem Build bem-sucedido":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="3a57d-149">Adicionar um aplicativo de console à solução</span><span class="sxs-lookup"><span data-stu-id="3a57d-149">Add a console app to the solution</span></span>

<span data-ttu-id="3a57d-150">Adicione um aplicativo de console que usa a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="3a57d-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="3a57d-151">O aplicativo solicitará que o usuário insira uma cadeia de caracteres e relate se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="3a57d-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="3a57d-152">No painel de **solução** , <kbd>pressione CTRL +</kbd>clique na `ClassLibraryProjects` solução.</span><span class="sxs-lookup"><span data-stu-id="3a57d-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="3a57d-153">Adicione um novo projeto de **aplicativo de console** selecionando o modelo nos modelos de aplicativo **Web e de console**  >  **App** e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="3a57d-154">Selecione **.NET Core 3,1** como a **estrutura de destino** e selecione **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="3a57d-155">Nomeie a **demonstração** do projeto.</span><span class="sxs-lookup"><span data-stu-id="3a57d-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="3a57d-156">Selecione **Criar** para criar o projeto na solução.</span><span class="sxs-lookup"><span data-stu-id="3a57d-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Adicionar projeto de demonstração":::

1. <span data-ttu-id="3a57d-158">Abra o arquivo *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="3a57d-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="3a57d-159">Substitua o código pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3a57d-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="3a57d-160">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3a57d-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="3a57d-161">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="3a57d-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="3a57d-162">Se o usuário pressionar a tecla <kbd>Enter</kbd> sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="3a57d-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="3a57d-163">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="3a57d-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="3a57d-164">Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="3a57d-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="3a57d-165">Adicionar uma referência ao projeto</span><span class="sxs-lookup"><span data-stu-id="3a57d-165">Add a project reference</span></span>

<span data-ttu-id="3a57d-166">Inicialmente, o novo projeto de aplicativo de console não tem acesso à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="3a57d-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="3a57d-167">Para permitir que ele chame métodos na biblioteca de classes, crie uma referência de projeto para o projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="3a57d-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="3a57d-168">No painel **soluções** , <kbd>pressione CTRL</kbd>e clique no nó **dependências** do novo projeto de **demonstração** .</span><span class="sxs-lookup"><span data-stu-id="3a57d-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="3a57d-169">No menu de contexto, selecione **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="3a57d-170">Na caixa de diálogo **referências** , selecione **StringLibrary** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="3a57d-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="3a57d-171">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3a57d-171">Run the app</span></span>

1. <span data-ttu-id="3a57d-172"><kbd>Ctrl</kbd>-clique no projeto de demonstração e selecione **Executar projeto** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="3a57d-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="3a57d-173">Experimente o programa digitando cadeias de caracteres e pressionando <kbd>Enter</kbd>e pressione <kbd>Enter</kbd> para sair.</span><span class="sxs-lookup"><span data-stu-id="3a57d-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Janela do console do Visual Studio para Mac mostrando o aplicativo em execução":::

## <a name="additional-resources"></a><span data-ttu-id="3a57d-175">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="3a57d-175">Additional resources</span></span>

* [<span data-ttu-id="3a57d-176">Desenvolver bibliotecas com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a57d-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="3a57d-177">[.Net Standard versões e plataformas às quais eles dão suporte](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="3a57d-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="3a57d-178">Notas sobre a versão do Visual Studio 2019 para Mac</span><span class="sxs-lookup"><span data-stu-id="3a57d-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="3a57d-179">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3a57d-179">Next steps</span></span>

<span data-ttu-id="3a57d-180">Neste tutorial, você criou uma solução e um projeto de biblioteca e adicionou um projeto de aplicativo de console que usa a biblioteca do.</span><span class="sxs-lookup"><span data-stu-id="3a57d-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="3a57d-181">No próximo tutorial, você adicionará um projeto de teste de unidade à solução.</span><span class="sxs-lookup"><span data-stu-id="3a57d-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3a57d-182">Testar uma biblioteca de .NET Standard com o .NET Core usando Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="3a57d-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
