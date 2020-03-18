---
title: Construa uma biblioteca de classe .NET Standard no Visual Studio
description: Aprenda a construir uma biblioteca de classe .NET Standard escrita em C# ou Visual Basic usando o Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714016"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="2c701-103">Construa uma biblioteca .NET Standard no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c701-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="2c701-104">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c701-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2c701-105">Uma biblioteca de classes que tem como alvo o .NET Standard 2.0 permite que sua biblioteca seja chamada por qualquer implementação .NET que suporte essa versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2c701-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="2c701-106">Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="2c701-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2c701-107">Para obter uma lista de versões .NET Standard e as plataformas que eles suportam, consulte [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="2c701-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="2c701-108">Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="2c701-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2c701-109">Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="2c701-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="2c701-110">Crie uma solução visual studio</span><span class="sxs-lookup"><span data-stu-id="2c701-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="2c701-111">Comece criando uma solução em branco para colocar o projeto da biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="2c701-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="2c701-112">Uma solução visual studio serve como um recipiente para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="2c701-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="2c701-113">Você adicionará projetos adicionais relacionados à mesma solução se continuar com a série tutorial.</span><span class="sxs-lookup"><span data-stu-id="2c701-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="2c701-114">Para criar a solução em branco:</span><span class="sxs-lookup"><span data-stu-id="2c701-114">To create the blank solution:</span></span>

1. <span data-ttu-id="2c701-115">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c701-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="2c701-116">Na janela inicial, escolha **Criar um novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="2c701-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="2c701-117">Na **página Criar uma nova** página de projeto, digite **solução** na caixa de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2c701-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="2c701-118">Escolha o **modelo solução em branco** e escolha **Next**.</span><span class="sxs-lookup"><span data-stu-id="2c701-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Modelo de solução em branco no Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="2c701-120">Na **página Configurar sua nova** página de projeto, digite **ClassLibraryProjects** na caixa **nome do Projeto.**</span><span class="sxs-lookup"><span data-stu-id="2c701-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="2c701-121">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2c701-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="2c701-122">Você também pode pular essa etapa e deixar o Visual Studio criar a solução para você quando criar o projeto na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="2c701-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="2c701-123">Procure as opções de solução na página Configurar sua nova página **de projeto.**</span><span class="sxs-lookup"><span data-stu-id="2c701-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="2c701-124">Criar um projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="2c701-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="2c701-125">C #</span><span class="sxs-lookup"><span data-stu-id="2c701-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="2c701-126">Adicione um novo projeto de biblioteca de classe C# .NET standard chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="2c701-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2c701-127">Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="2c701-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2c701-128">Na **página Adicionar uma nova** página de projeto, digite biblioteca na caixa de pesquisa. **library**</span><span class="sxs-lookup"><span data-stu-id="2c701-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2c701-129">Escolha **C#** na lista De idiomas e escolha **Todas as plataformas** da lista Plataforma.</span><span class="sxs-lookup"><span data-stu-id="2c701-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2c701-130">Escolha o modelo **Biblioteca de classe (.NET Padrão)** e escolha **Next**.</span><span class="sxs-lookup"><span data-stu-id="2c701-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2c701-131">Na **página Configurar sua nova** página de projeto, digite **StringLibrary** na caixa **nome do Projeto.**</span><span class="sxs-lookup"><span data-stu-id="2c701-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="2c701-132">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2c701-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="2c701-133">Verifique se a biblioteca tem como alvo a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2c701-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2c701-134">Clique com o botão direito do mouse no projeto da biblioteca no **Solution Explorer**e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2c701-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2c701-135">A caixa de texto **Target Framework** mostra que o projeto tem como alvo o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2c701-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="2c701-137">Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="2c701-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="2c701-138">A biblioteca `UtilityLibraries.StringLibrary`de classes contém `StartsWithUpper`um método chamado .</span><span class="sxs-lookup"><span data-stu-id="2c701-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2c701-139">Este método <xref:System.Boolean> retorna um valor que indica se a instância atual da seqüência de string começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="2c701-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2c701-140">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="2c701-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2c701-141">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="2c701-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2c701-142">Na barra de menu, selecione **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="2c701-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="2c701-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2c701-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="2c701-144">Adicione um novo projeto de biblioteca de classe visual básico .NET padrão chamado "StringLibrary" à solução.</span><span class="sxs-lookup"><span data-stu-id="2c701-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2c701-145">Clique com o botão direito do mouse na solução no **Solution Explorer** e selecione **Adicionar** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="2c701-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2c701-146">Na **página Adicionar uma nova** página de projeto, digite biblioteca na caixa de pesquisa. **library**</span><span class="sxs-lookup"><span data-stu-id="2c701-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2c701-147">Escolha **visual básico** na lista de idiomas e escolha Todas as **plataformas** da lista Plataforma.</span><span class="sxs-lookup"><span data-stu-id="2c701-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2c701-148">Escolha o modelo **Biblioteca de classe (.NET Padrão)** e escolha **Next**.</span><span class="sxs-lookup"><span data-stu-id="2c701-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2c701-149">Na **página Configurar sua nova** página de projeto, digite **StringLibrary** na caixa **nome do Projeto.**</span><span class="sxs-lookup"><span data-stu-id="2c701-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="2c701-150">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="2c701-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="2c701-151">Verifique se a biblioteca tem como alvo a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2c701-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2c701-152">Clique com o botão direito do mouse no projeto da biblioteca no **Solution Explorer**e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="2c701-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2c701-153">A caixa de texto **Target Framework** mostra que o projeto tem como alvo o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2c701-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="2c701-155">Na **caixa de** diálogo Propriedades, limpe o texto na caixa de texto **'Namespace'** Root.</span><span class="sxs-lookup"><span data-stu-id="2c701-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="2c701-156">Para cada projeto, o Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="2c701-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="2c701-157">Neste tutorial, você define um namespace de [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) nível superior usando a palavra-chave no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="2c701-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="2c701-158">Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="2c701-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="2c701-159">A biblioteca `UtilityLibraries.StringLibrary`de classes contém `StartsWithUpper`um método chamado .</span><span class="sxs-lookup"><span data-stu-id="2c701-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2c701-160">Este método <xref:System.Boolean> retorna um valor que indica se a instância atual da seqüência de string começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="2c701-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2c701-161">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="2c701-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2c701-162">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="2c701-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2c701-163">Na barra de menu, selecione **Build** > **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="2c701-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="2c701-164">O projeto deve ser compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="2c701-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c701-165">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2c701-165">Next steps</span></span>

<span data-ttu-id="2c701-166">Você compilou com êxito a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="2c701-166">You've successfully built the library.</span></span> <span data-ttu-id="2c701-167">Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado.</span><span class="sxs-lookup"><span data-stu-id="2c701-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="2c701-168">O próximo passo no desenvolvimento de sua biblioteca é testá-la.</span><span class="sxs-lookup"><span data-stu-id="2c701-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2c701-169">Crie um projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="2c701-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
