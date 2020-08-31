---
title: Criar uma biblioteca de classes de .NET Standard usando o Visual Studio
description: Saiba como criar uma biblioteca de classes de .NET Standard usando o Visual Studio.
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 45a44dcd73e1abcc8dfd75cd54da5a2310f027c4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118254"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="b2c6b-103">Tutorial: criar uma biblioteca de .NET Standard usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2c6b-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="b2c6b-104">Neste tutorial, você cria uma biblioteca de classes simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="b2c6b-105">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="b2c6b-106">Uma biblioteca de classes que tem como alvo .NET Standard 2,0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte a essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-106">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="b2c6b-107">Ao concluir a biblioteca de classes, você pode distribuí-la como um pacote NuGet ou como um componente agrupado com o aplicativo que a utiliza.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-107">When you finish your class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b2c6b-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="b2c6b-108">Prerequisites</span></span>

- <span data-ttu-id="b2c6b-109">[Visual Studio 2019 versão 16,6 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-109">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="b2c6b-110">O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="b2c6b-111">Criar uma solução</span><span class="sxs-lookup"><span data-stu-id="b2c6b-111">Create a solution</span></span>

<span data-ttu-id="b2c6b-112">Comece criando uma solução em branco para colocar o projeto de biblioteca de classes no.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-112">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="b2c6b-113">Uma solução do Visual Studio serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-113">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="b2c6b-114">Você adicionará mais projetos relacionados à mesma solução.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-114">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="b2c6b-115">Para criar a solução em branco:</span><span class="sxs-lookup"><span data-stu-id="b2c6b-115">To create the blank solution:</span></span>

1. <span data-ttu-id="b2c6b-116">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="b2c6b-117">Na janela iniciar, escolha **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-117">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="b2c6b-118">Na página **criar um novo projeto** , digite **solução** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-118">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="b2c6b-119">Escolha o modelo de **solução em branco** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-119">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modelo de solução em branco no Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="b2c6b-121">Na página **configurar seu novo projeto** , digite **ClassLibraryProjects** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="b2c6b-121">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="b2c6b-122">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-122">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="b2c6b-123">Criar um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="b2c6b-123">Create a class library project</span></span>

1. <span data-ttu-id="b2c6b-124">Adicione um novo projeto de biblioteca de classe .NET Standard chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-124">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="b2c6b-125">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-125">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="b2c6b-126">Na página **Adicionar um novo projeto** , insira **biblioteca** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-126">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="b2c6b-127">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-127">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="b2c6b-128">Escolha o modelo **biblioteca de classes (.net Standard)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-128">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="b2c6b-129">Na página **configurar seu novo projeto** , digite **StringLibrary** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="b2c6b-129">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="b2c6b-130">Em seguida, escolha **criar**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-130">Then, choose **Create**.</span></span>

1. <span data-ttu-id="b2c6b-131">Verifique se a biblioteca tem como destino a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="b2c6b-132">Clique com o botão direito do mouse no projeto de biblioteca em **Gerenciador de soluções**e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-132">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="b2c6b-133">A caixa de texto **estrutura de destino** mostra que o projeto tem como destino .net Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-133">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="b2c6b-135">Se você estiver usando Visual Basic, desmarque o texto na caixa de texto **namespace raiz** .</span><span class="sxs-lookup"><span data-stu-id="b2c6b-135">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="b2c6b-137">Para cada projeto, Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-137">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="b2c6b-138">Neste tutorial, você define um namespace de nível superior usando a [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) palavra-chave no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-138">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="b2c6b-139">Substitua o código na janela de código para *Class1.cs*  ou *Class1. vb* pelo código a seguir e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-139">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="b2c6b-140">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-140">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="b2c6b-141">A biblioteca de classes, `UtilityLibraries.StringLibrary` , contém um método chamado `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="b2c6b-141">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="b2c6b-142">Esse método retorna um <xref:System.Boolean> valor que indica se a instância atual da cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-142">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="b2c6b-143">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-143">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="b2c6b-144">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-144">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="b2c6b-145">`StartsWithUpper` é implementado como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md) para que você possa chamá-lo como se fosse um membro da <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-145">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="b2c6b-146">Na barra de menus, selecione **criar**  >  **solução de compilação** ou pressione <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> para verificar se o projeto é compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-146">On the menu bar, select **Build** > **Build Solution** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="b2c6b-147">Adicionar um aplicativo de console à solução</span><span class="sxs-lookup"><span data-stu-id="b2c6b-147">Add a console app to the solution</span></span>

<span data-ttu-id="b2c6b-148">Adicione um aplicativo de console que usa a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-148">Add a console application that uses the class library.</span></span> <span data-ttu-id="b2c6b-149">O aplicativo solicitará que o usuário insira uma cadeia de caracteres e relate se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-149">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="b2c6b-150">Adicione um novo aplicativo de console .NET Core chamado "ShowCase" à solução.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-150">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="b2c6b-151">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-151">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="b2c6b-152">Na página **Adicionar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-152">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="b2c6b-153">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-153">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="b2c6b-154">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-154">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="b2c6b-155">Na página **configurar seu novo projeto** , insira **Showcase** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="b2c6b-155">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="b2c6b-156">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-156">Then choose **Create**.</span></span>

1. <span data-ttu-id="b2c6b-157">Na janela de código do arquivo *Program.cs* ou *Program. vb* , substitua todo o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-157">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="b2c6b-158">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-158">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="b2c6b-159">Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-159">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="b2c6b-160">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="b2c6b-161">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="b2c6b-162">Se o usuário pressionar a tecla <kbd>Enter</kbd> sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-162">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="b2c6b-163">Adicionar uma referência ao projeto</span><span class="sxs-lookup"><span data-stu-id="b2c6b-163">Add a project reference</span></span>

<span data-ttu-id="b2c6b-164">Inicialmente, o novo projeto de aplicativo de console não tem acesso à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-164">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="b2c6b-165">Para permitir que ele chame métodos na biblioteca de classes, crie uma referência de projeto para o projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-165">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="b2c6b-166">Em **Gerenciador de soluções**, clique com o botão direito do mouse no `ShowCase` nó **dependências** do projeto e selecione **Adicionar referência de projeto**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-166">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Adicionar menu de contexto de referência no Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="b2c6b-168">Na caixa de diálogo **Gerenciador de referências** , selecione o projeto **StringLibrary** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-168">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Caixa de diálogo Gerenciador de referências com StringLibrary selecionado](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="b2c6b-170">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="b2c6b-170">Run the app</span></span>

1. <span data-ttu-id="b2c6b-171">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-171">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu de contexto do projeto do Visual Studio para definir o projeto de inicialização](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="b2c6b-173">Pressione <kbd>Ctrl</kbd> + <kbd>F5</kbd> para compilar e executar o programa sem depuração.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-173">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Barra de ferramentas do projeto do Visual Studio mostrando botão de depuração](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="b2c6b-175">Experimente o programa digitando cadeias de caracteres e pressionando <kbd>Enter</kbd>e pressione <kbd>Enter</kbd> para sair.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-175">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Janela do console com o ShowCase em execução":::

## <a name="additional-resources"></a><span data-ttu-id="b2c6b-177">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="b2c6b-177">Additional resources</span></span>

* [<span data-ttu-id="b2c6b-178">Desenvolver bibliotecas com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2c6b-178">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="b2c6b-179">[.Net Standard versões e plataformas às quais eles dão suporte](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="b2c6b-179">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b2c6b-180">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b2c6b-180">Next steps</span></span>

<span data-ttu-id="b2c6b-181">Neste tutorial, você criou uma biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-181">In this tutorial, you created a class library.</span></span> <span data-ttu-id="b2c6b-182">No próximo tutorial, você aprenderá a testar unidade a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-182">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2c6b-183">Teste de unidade de uma biblioteca de .NET Standard usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2c6b-183">Unit test a .NET Standard library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="b2c6b-184">Ou você pode ignorar o teste de unidade automatizado e aprender a compartilhar a biblioteca criando um pacote NuGet:</span><span class="sxs-lookup"><span data-stu-id="b2c6b-184">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2c6b-185">Criar e publicar um pacote usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2c6b-185">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="b2c6b-186">Ou saiba como publicar um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="b2c6b-186">Or learn how to publish a console app.</span></span> <span data-ttu-id="b2c6b-187">Se você publicar o aplicativo de console da solução criada neste tutorial, a biblioteca de classes o passará como um arquivo *. dll* .</span><span class="sxs-lookup"><span data-stu-id="b2c6b-187">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b2c6b-188">Publicar um aplicativo de console do .NET Core usando o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2c6b-188">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
