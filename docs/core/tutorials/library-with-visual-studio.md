---
title: Criar uma biblioteca de classes de .NET Standard no Visual Studio
description: Saiba como criar uma biblioteca de classes .NET Standard escrita C# ou Visual Basic usando o Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714016"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="e5a0d-103">Criar uma biblioteca de .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5a0d-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="e5a0d-104">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="e5a0d-105">Uma biblioteca de classes que tem como alvo .NET Standard 2,0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte a essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="e5a0d-106">Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="e5a0d-107">Para obter uma lista de versões de .NET Standard e as plataformas às quais eles dão suporte, consulte [.net Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="e5a0d-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="e5a0d-108">Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="e5a0d-109">Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="e5a0d-110">Criar uma solução do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5a0d-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="e5a0d-111">Comece criando uma solução em branco para colocar o projeto de biblioteca de classes no.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="e5a0d-112">Uma solução do Visual Studio serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="e5a0d-113">Você adicionará mais projetos relacionados à mesma solução se continuar com a série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="e5a0d-114">Para criar a solução em branco:</span><span class="sxs-lookup"><span data-stu-id="e5a0d-114">To create the blank solution:</span></span>

1. <span data-ttu-id="e5a0d-115">{1&gt;Abra o Visual Studio.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e5a0d-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="e5a0d-116">Na tela Iniciar, selecione **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="e5a0d-117">Na página **criar um novo projeto** , digite **solução** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="e5a0d-118">Escolha o modelo de **solução em branco** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modelo de solução em branco no Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="e5a0d-120">Na página **configurar seu novo projeto** , digite **ClassLibraryProjects** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="e5a0d-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="e5a0d-121">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="e5a0d-122">Você também pode ignorar esta etapa e deixar que o Visual Studio crie a solução para você ao criar o projeto na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="e5a0d-123">Procure as opções de solução na página **configurar seu novo projeto** .</span><span class="sxs-lookup"><span data-stu-id="e5a0d-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="e5a0d-124">Criar um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="e5a0d-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="e5a0d-125">C#</span><span class="sxs-lookup"><span data-stu-id="e5a0d-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="e5a0d-126">Adicione um novo C# projeto de biblioteca de classe .net Standard chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="e5a0d-127">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="e5a0d-128">Na página **Adicionar um novo projeto** , insira **biblioteca** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="e5a0d-129">Escolha **C#** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e5a0d-130">Escolha o modelo **biblioteca de classes (.net Standard)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="e5a0d-131">Na página **configurar seu novo projeto** , digite **StringLibrary** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="e5a0d-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="e5a0d-132">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="e5a0d-133">Verifique se a biblioteca tem como destino a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="e5a0d-134">Clique com o botão direito do mouse no projeto de biblioteca em **Gerenciador de soluções**e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="e5a0d-135">A caixa de texto **estrutura de destino** mostra que o projeto tem como destino .net Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="e5a0d-137">Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="e5a0d-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="e5a0d-138">A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="e5a0d-139">Esse método retorna um valor <xref:System.Boolean> que indica se a instância da cadeia de caracteres atual começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="e5a0d-140">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="e5a0d-141">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="e5a0d-142">Na barra de menus, selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="e5a0d-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5a0d-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="e5a0d-144">Adicione um novo Visual Basic .NET Standard projeto de biblioteca de classes chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="e5a0d-145">Clique com o botão direito do mouse na solução em **Gerenciador de soluções** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="e5a0d-146">Na página **Adicionar um novo projeto** , insira **biblioteca** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="e5a0d-147">Escolha **Visual Basic** na lista idioma e, em seguida, escolha **todas as plataformas** na lista plataforma.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="e5a0d-148">Escolha o modelo **biblioteca de classes (.net Standard)** e, em seguida, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="e5a0d-149">Na página **configurar seu novo projeto** , digite **StringLibrary** na caixa **nome do projeto** .</span><span class="sxs-lookup"><span data-stu-id="e5a0d-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="e5a0d-150">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="e5a0d-151">Verifique se a biblioteca tem como destino a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="e5a0d-152">Clique com o botão direito do mouse no projeto de biblioteca em **Gerenciador de soluções**e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="e5a0d-153">A caixa de texto **estrutura de destino** mostra que o projeto tem como destino .net Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="e5a0d-155">No diálogo **Propriedades** , desmarque o texto na caixa de texto **namespace raiz** .</span><span class="sxs-lookup"><span data-stu-id="e5a0d-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="e5a0d-156">Para cada projeto, Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="e5a0d-157">Neste tutorial, você define um namespace de nível superior usando a palavra-chave [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="e5a0d-158">Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="e5a0d-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="e5a0d-159">A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="e5a0d-160">Esse método retorna um valor <xref:System.Boolean> que indica se a instância da cadeia de caracteres atual começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="e5a0d-161">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="e5a0d-162">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="e5a0d-163">Na barra de menus, selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="e5a0d-164">O projeto deve ser compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e5a0d-165">{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e5a0d-165">Next steps</span></span>

<span data-ttu-id="e5a0d-166">Você compilou com êxito a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-166">You've successfully built the library.</span></span> <span data-ttu-id="e5a0d-167">Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="e5a0d-168">A próxima etapa no desenvolvimento da biblioteca é testá-la.</span><span class="sxs-lookup"><span data-stu-id="e5a0d-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e5a0d-169">Criar um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="e5a0d-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
