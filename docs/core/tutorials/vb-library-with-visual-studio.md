---
title: Criar uma biblioteca de classes .NET Standard em Visual Basic no Visual Studio 2017
description: Saiba como criar uma biblioteca de classes .NET Standard escrita em Visual Basic usando o Visual Studio 2017
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f14e4ffbebfe0d7e01d548a6d4f2dc8924633682
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157294"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="56e6b-103">Criar uma biblioteca .NET Standard com o Visual Basic e o SDK do .NET Core no Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="56e6b-103">Build a .NET Standard library with Visual Basic and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="56e6b-104">Uma *biblioteca de classes* define tipos e métodos que são chamados por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="56e6b-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="56e6b-105">Uma biblioteca de classes que direciona o .NET Standard 2.0 permite que sua biblioteca seja chamada por qualquer implementação do .NET que dê suporte à versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="56e6b-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="56e6b-106">Quando você finaliza sua biblioteca de classes, pode decidir se deseja distribuí-la como um componente de terceiros ou se quer incluí-la como um componente agrupado com um ou mais aplicativos.</span><span class="sxs-lookup"><span data-stu-id="56e6b-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="56e6b-107">Para obter uma lista das versões do .NET Standard e as plataformas às quais elas dão suporte, consulte [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="56e6b-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="56e6b-108">Neste tópico, você criará uma biblioteca de utilitários simples que contém um único método de manipulação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="56e6b-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="56e6b-109">Você implementará essa biblioteca como um [método de extensão](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md), para que você possa chamá-la como se fosse membro da classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="56e6b-109">You'll implement it as an [extension method](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="56e6b-110">Criar uma solução de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="56e6b-110">Creating a class library solution</span></span>

<span data-ttu-id="56e6b-111">Comece criando uma solução para seu projeto de biblioteca de classes e seus projetos relacionados.</span><span class="sxs-lookup"><span data-stu-id="56e6b-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="56e6b-112">Uma solução do Visual Studio serve como um contêiner para um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="56e6b-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="56e6b-113">Para criar a solução:</span><span class="sxs-lookup"><span data-stu-id="56e6b-113">To create the solution:</span></span>

1. <span data-ttu-id="56e6b-114">Na barra de menus do Visual Studio, escolha **Arquivo** > **Novo** > **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="56e6b-115">Na caixa de diálogo **Novo Projeto**, expanda o nó **Outros Tipos de Projeto** e selecione **Soluções Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="56e6b-116">Nomeie a solução "ClassLibraryProjects" e selecione o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![Caixa de diálogo Criar projeto de teste do Visual Studio](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="56e6b-118">Criar o projeto de biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="56e6b-118">Creating the class library project</span></span>

<span data-ttu-id="56e6b-119">Crie seu projeto de biblioteca de classes:</span><span class="sxs-lookup"><span data-stu-id="56e6b-119">Create your class library project:</span></span>

1. <span data-ttu-id="56e6b-120">No **Gerenciador de Soluções**, clique com o botão direito do mouse no arquivo da solução **ClassLibraryProjects** e, no menu de contexto, selecione **Adicionar** > **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="56e6b-121">Na caixa de diálogo **Adicionar novo projeto**, expanda o nó **Visual Basic** e selecione o nó **.NET Standard** seguido pelo modelo de projeto **Biblioteca de classes (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-121">In the **Add New Project** dialog, expand the **Visual Basic** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="56e6b-122">Na caixa de texto **Nome**, digite "StringLibrary" como o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="56e6b-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="56e6b-123">Selecione **OK** para criar o projeto de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="56e6b-123">Select **OK** to create the class library project.</span></span>

   ![Caixa de diálogo Adicionar novo projeto de biblioteca do Visual Studio](./media/vb-library-with-visual-studio/create-new-library-project.png)

   <span data-ttu-id="56e6b-125">Em seguida, a janela de código é aberta no ambiente de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="56e6b-125">The code window then opens in the Visual Studio development environment.</span></span> 
 
   ![Janela do aplicativo do Visual Studio mostrando o código de modelo de biblioteca de classes padrão](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. <span data-ttu-id="56e6b-127">Certifique-se de que a biblioteca direciona a versão correta do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="56e6b-127">Check to make sure that the library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="56e6b-128">Clique com o botão direito do mouse no projeto da biblioteca na janela **Gerenciador de Soluções** e, em seguida, selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="56e6b-129">A caixa de texto **Estrutura de Destino** mostra que estamos direcionando o .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="56e6b-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![Propriedades do projeto da biblioteca de classes](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="56e6b-131">Ainda na caixa de diálogo **Propriedades**, apague o texto na caixa de texto **Namespace raiz**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-131">Also in the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="56e6b-132">Para cada projeto, o Visual Basic cria automaticamente um namespace que corresponde ao nome do projeto e quaisquer namespaces definidos nos arquivos do código-fonte são pais desse namespace.</span><span class="sxs-lookup"><span data-stu-id="56e6b-132">For each project, Visual Basic automatically creates a namespace that corresponds to the project name, and any namespaces defined in source code files are parents of that namespace.</span></span> <span data-ttu-id="56e6b-133">Queremos definir um namespace de nível superior usando a palavra-chave [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="56e6b-133">We want to define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword.</span></span>
  
1. <span data-ttu-id="56e6b-134">Substitua o código na janela de código pelo mostrado a seguir e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="56e6b-134">Replace the code in the code window with the following code and save the file:</span></span>

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="56e6b-135">A biblioteca de classes, `UtilityLibraries.StringLibrary`, contém um método chamado `StartsWithUpper`, que retorna um valor <xref:System.Boolean> indicando se a instância atual da cadeia de caracteres começa com um caractere maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="56e6b-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="56e6b-136">O padrão Unicode distingue caracteres maiúsculos de caracteres minúsculos.</span><span class="sxs-lookup"><span data-stu-id="56e6b-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="56e6b-137">O método <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> retornará `true` se um caractere for maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="56e6b-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="56e6b-138">Na barra de menus, selecione **Compilar** > **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="56e6b-138">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="56e6b-139">O projeto deve ser compilado sem erros.</span><span class="sxs-lookup"><span data-stu-id="56e6b-139">The project should compile without error.</span></span>

   ![Painel de saída mostrando que o build foi bem-sucedido](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="56e6b-141">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="56e6b-141">Next step</span></span>

<span data-ttu-id="56e6b-142">Você compilou com êxito a biblioteca.</span><span class="sxs-lookup"><span data-stu-id="56e6b-142">You've successfully built the library.</span></span> <span data-ttu-id="56e6b-143">Mas como você ainda não chamou nenhum de seus métodos, não sabe se ele funciona como esperado.</span><span class="sxs-lookup"><span data-stu-id="56e6b-143">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="56e6b-144">A próxima etapa no desenvolvimento de sua biblioteca é testá-la usando um [Projeto de Teste de Unidade](testing-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="56e6b-144">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>
