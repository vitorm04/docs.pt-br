---
title: Compilando uma biblioteca de classes do .NET Standard com C# e com o .NET Core no Visual Studio 2017
description: Saiba como criar uma biblioteca de classes do .NET Standard escrita em C# usando o Visual Studio 2017.
keywords: .NET Core, biblioteca de classes .NET Standard, Visual Studio 2017
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.openlocfilehash: 5806e3e71eabbc1d65ecffed72108ba548b57806
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a><span data-ttu-id="d4c4d-104">Criar uma biblioteca de classes com C# e .NET Core no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d4c4d-104">Building a class library with C# and .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="d4c4d-105">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="d4c4d-106">Uma biblioteca de classes que direciona o .NET Standard 2.0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte à versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-106">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="d4c4d-107">Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-107">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="d4c4d-108">Para obter uma lista das versões do .NET Standard e as plataformas às quais elas dão suporte, consulte [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="d4c4d-108">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="d4c4d-109">Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-109">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="d4c4d-110">Você implementará essa biblioteca como um [método de extensão](../../csharp/programming-guide/classes-and-structs/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-110">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="d4c4d-111">Criar uma solução de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d4c4d-111">Creating a class library solution</span></span>

<span data-ttu-id="d4c4d-112">Comece criando uma solução para seu projeto de biblioteca de classes e seus projetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-112">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="d4c4d-113">Uma solução do Visual Studio serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-113">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="d4c4d-114">Para criar a solução:</span><span class="sxs-lookup"><span data-stu-id="d4c4d-114">To create the solution:</span></span>

1. <span data-ttu-id="d4c4d-115">Na barra de menus do Visual Studio, escolha **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-115">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="d4c4d-116">Na caixa de diálogo **Novo Projeto**, expanda o nó **Outros Tipos de Projeto** e selecione **Soluções Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-116">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="d4c4d-117">Nomeie a solução "ClassLibraryProjects" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-117">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Caixa de diálogo Novo projeto](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="d4c4d-119">Criar o projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d4c4d-119">Creating the class library project</span></span>

<span data-ttu-id="d4c4d-120">Crie seu projeto de biblioteca de classes:</span><span class="sxs-lookup"><span data-stu-id="d4c4d-120">Create your class library project:</span></span>

1. <span data-ttu-id="d4c4d-121">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo da solução **ClassLibraryProjects** e, no menu de contexto, selecione **Adicionar** > **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-121">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="d4c4d-122">Na caixa de diálogo **Adicionar novo projeto**, expanda o nó **Visual C#** e selecione o nó **.NET Standard** seguido pelo modelo de projeto **Biblioteca de classes (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-122">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="d4c4d-123">Na caixa de texto **Nome**, digite "StringLibrary" como o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-123">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="d4c4d-124">Selecione **OK** para criar o projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-124">Select **OK** to create the class library project.</span></span>

   ![Caixa de diálogo Adicionar Novo Projeto](./media/library-with-visual-studio/libproject.png)

   <span data-ttu-id="d4c4d-126">Em seguida, a janela de código é aberta no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-126">The code window then opens in the Visual Studio development environment.</span></span>

   ![Janela do aplicativo do Visual Studio mostrando o código de modelo de biblioteca de classes padrão](./media/library-with-visual-studio/stringlibrary.png)

1. <span data-ttu-id="d4c4d-128">Certifique-se de que a nossa biblioteca direciona a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-128">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="d4c4d-129">Clique com o botão direito do mouse no projeto da biblioteca na janela **Gerenciador de Soluções** e, em seguida, selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-129">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="d4c4d-130">A caixa de texto **Estrutura de Destino** mostra que estamos direcionando o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-130">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/properties.png)

1. <span data-ttu-id="d4c4d-132">Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="d4c4d-132">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="d4c4d-133">A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`, que retorna um valor <xref:System.Boolean> indicando se a instância atual da cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-133">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="d4c4d-134">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-134">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="d4c4d-135">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-135">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="d4c4d-136">Na barra de menus, selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-136">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="d4c4d-137">O projeto deve ser compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-137">The project should compile without error.</span></span>

   ![Painel de saída mostrando que o build foi bem-sucedido](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a><span data-ttu-id="d4c4d-139">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d4c4d-139">Next step</span></span>

<span data-ttu-id="d4c4d-140">Você compilou com êxito a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-140">You've successfully built the library.</span></span> <span data-ttu-id="d4c4d-141">Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado.</span><span class="sxs-lookup"><span data-stu-id="d4c4d-141">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="d4c4d-142">A próxima etapa no desenvolvimento de sua biblioteca é testá-la usando um [Projeto de Teste de Unidade](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d4c4d-142">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>