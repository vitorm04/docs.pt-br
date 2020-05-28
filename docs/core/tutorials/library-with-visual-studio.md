---
title: Criar uma biblioteca de classes de .NET Standard no Visual Studio
description: Saiba como criar uma biblioteca de classes de .NET Standard usando o Visual Studio.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005213"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="c3a2a-103">Tutorial: criar uma biblioteca de .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3a2a-103">Tutorial: Create a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="c3a2a-104">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="c3a2a-105">Uma biblioteca de classes que tem como alvo .NET Standard 2,0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte a essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="c3a2a-106">Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="c3a2a-107">Para obter uma lista de versões de .NET Standard e as plataformas às quais eles dão suporte, consulte [.net Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="c3a2a-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="c3a2a-108">Neste tutorial, você cria uma biblioteca de utilitário simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="c3a2a-109">Implemente-o como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md) para que você possa chamá-lo como se fosse um membro da <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3a2a-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c3a2a-110">Prerequisites</span></span>

- <span data-ttu-id="c3a2a-111">[Visual Studio 2019 versão 16,6 ou uma versão posterior](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) com a carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** instalada.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-111">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="c3a2a-112">O SDK do .NET Core 3,1 é instalado automaticamente quando você seleciona essa carga de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-112">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="c3a2a-113">Para obter mais informações, consulte a seção [instalar com o Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) no artigo [instalar o SDK do .NET Core](../install/sdk.md?pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="c3a2a-113">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="c3a2a-114">Criar uma solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3a2a-114">Create a Visual Studio solution</span></span>

<span data-ttu-id="c3a2a-115">Comece criando uma solução em branco para colocar o projeto de biblioteca de classes no.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="c3a2a-116">Uma solução do Visual Studio serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="c3a2a-117">Você adicionará mais projetos relacionados à mesma solução.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="c3a2a-118">Para criar a solução em branco:</span><span class="sxs-lookup"><span data-stu-id="c3a2a-118">To create the blank solution:</span></span>

1. <span data-ttu-id="c3a2a-119">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-119">Open Visual Studio.</span></span>

2. <span data-ttu-id="c3a2a-120">Na janela iniciar, escolha **criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="c3a2a-121">Na página **criar um novo projeto** , digite **solução** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="c3a2a-122">Escolha o modelo de **solução em branco** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modelo de solução em branco no Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="c3a2a-124">Na página **configurar seu novo projeto** , digite **ClassLibraryProjects** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="c3a2a-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="c3a2a-125">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="c3a2a-126">Criar um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c3a2a-126">Create a class library project</span></span>

1. <span data-ttu-id="c3a2a-127">Adicione um novo projeto de biblioteca de classe .NET Standard chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-127">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="c3a2a-128">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="c3a2a-129">Na página **Adicionar um novo projeto** , insira **biblioteca** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="c3a2a-130">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c3a2a-131">Escolha o modelo **biblioteca de classes (.net Standard)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-131">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c3a2a-132">Na página **configurar seu novo projeto** , digite **StringLibrary** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="c3a2a-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="c3a2a-133">Em seguida, escolha **criar**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-133">Then, choose **Create**.</span></span>

1. <span data-ttu-id="c3a2a-134">Verifique se a biblioteca tem como destino a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-134">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="c3a2a-135">Clique com o botão direito do mouse no projeto de biblioteca em **Gerenciador de soluções**e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="c3a2a-136">A caixa de texto **estrutura de destino** mostra que o projeto tem como destino .net Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-136">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="c3a2a-138">Se você estiver usando Visual Basic, desmarque o texto na caixa de texto **namespace raiz** .</span><span class="sxs-lookup"><span data-stu-id="c3a2a-138">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="c3a2a-140">Para cada projeto, Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-140">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="c3a2a-141">Neste tutorial, você define um namespace de nível superior usando a [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) palavra-chave no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-141">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="c3a2a-142">Substitua o código na janela de código para *Class1.cs* ou *Class1. vb* pelo código a seguir e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-142">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="c3a2a-143">Se o idioma que você deseja usar não for mostrado, altere o seletor de idioma na parte superior da página.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-143">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="c3a2a-144">A biblioteca de classes, `UtilityLibraries.StringLibrary` , contém um método chamado `StartsWithUpper` .</span><span class="sxs-lookup"><span data-stu-id="c3a2a-144">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="c3a2a-145">Esse método retorna um <xref:System.Boolean> valor que indica se a instância atual da cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-145">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="c3a2a-146">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-146">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="c3a2a-147">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-147">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="c3a2a-148">Na barra de menus, selecione **Compilar**compilar  >  **solução** para verificar se o projeto é compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-148">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="c3a2a-149">Adicionar um aplicativo de console à solução</span><span class="sxs-lookup"><span data-stu-id="c3a2a-149">Add a console app to the solution</span></span>

<span data-ttu-id="c3a2a-150">Use a biblioteca de classes em um aplicativo de console que solicita que o usuário insira uma cadeia de caracteres e relate se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-150">Use the class library in a console application that prompts the user to enter a string and reports whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="c3a2a-151">Adicione um novo aplicativo de console .NET Core chamado "ShowCase" à solução.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="c3a2a-152">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar**  >  **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="c3a2a-153">Na página **Adicionar um novo projeto** , insira **console** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c3a2a-154">Escolha **C#** ou **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="c3a2a-155">Escolha o modelo **aplicativo de console (.NET Core)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c3a2a-156">Na página **configurar seu novo projeto** , insira **Showcase** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="c3a2a-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="c3a2a-157">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="c3a2a-158">No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **ShowCase** e selecione **Definir como Projeto de Inicialização** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-158">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Menu de contexto do projeto do Visual Studio para definir o projeto de inicialização](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="c3a2a-160">Inicialmente, o novo projeto de aplicativo de console não tem acesso à biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-160">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="c3a2a-161">Para permitir que ele chame métodos na biblioteca de classes, crie uma referência de projeto para o projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-161">To allow it to call methods in the class library, create a project reference to the class library project.</span></span> <span data-ttu-id="c3a2a-162">Em **Gerenciador de soluções**, clique com o botão direito do mouse no `ShowCase` nó **dependências** do projeto e selecione **Adicionar referência de projeto**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-162">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Adicionar menu de contexto de referência no Visual Studio](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="c3a2a-164">Na caixa de diálogo **Gerenciador de referências** , selecione o projeto **StringLibrary** e selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-164">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![Caixa de diálogo Gerenciador de referências com StringLibrary selecionado](media/library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="c3a2a-166">Na janela de código do arquivo *Program.cs* ou *Program. vb* , substitua todo o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-166">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="c3a2a-167">O código usa a variável `row` ​​para manter uma contagem do número de linhas de dados gravadas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-167">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="c3a2a-168">Sempre que for maior ou igual a 25, o código limpará a janela do console e exibirá uma mensagem para o usuário.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-168">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="c3a2a-169">O programa solicita que o usuário insira uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-169">The program prompts the user to enter a string.</span></span> <span data-ttu-id="c3a2a-170">Ele indica se a cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-170">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="c3a2a-171">Se o usuário pressionar a tecla Enter sem inserir uma cadeia de caracteres, o aplicativo será encerrado e a janela do console será fechada.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-171">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="c3a2a-172">Se necessário, altere a barra de ferramentas para compilar a versão de **Depuração** do projeto `ShowCase`.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-172">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="c3a2a-173">Compile e execute o programa selecionando a seta verde no botão **ShowCase**.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-173">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Barra de ferramentas do projeto do Visual Studio mostrando botão de depuração](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="c3a2a-175">Experimente o programa digitando cadeias de caracteres e pressionando **Enter**e pressione **Enter** para sair.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-175">Try out the program by entering strings and pressing **Enter**, then press **Enter** to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="Janela do console com o ShowCase em execução":::

## <a name="next-steps"></a><span data-ttu-id="c3a2a-177">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c3a2a-177">Next steps</span></span>

<span data-ttu-id="c3a2a-178">Neste tutorial, você criou uma solução, adicionou um projeto de biblioteca e adicionou um projeto de aplicativo de console que usa a biblioteca do.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-178">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="c3a2a-179">No próximo tutorial, você adicionará um projeto de teste de unidade à solução.</span><span class="sxs-lookup"><span data-stu-id="c3a2a-179">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3a2a-180">Testar uma biblioteca de .NET Standard com o .NET Core no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3a2a-180">Test a .NET Standard library with .NET Core in Visual Studio</span></span>](testing-library-with-visual-studio.md)
