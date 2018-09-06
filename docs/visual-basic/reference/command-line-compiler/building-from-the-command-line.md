---
title: Compilando a partir da linha de comando (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
ms.openlocfilehash: 89bcd6e0e7c1cc867bf853dc9bbe96628942ace2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866971"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="460f1-102">Compilando a partir da linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="460f1-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="460f1-103">Um projeto do Visual Basic é composto por um ou mais arquivos de origem separado.</span><span class="sxs-lookup"><span data-stu-id="460f1-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="460f1-104">Durante o processo conhecido como compilação, esses arquivos são reunidos em um pacote — um único arquivo executável que pode ser executado como um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="460f1-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 <span data-ttu-id="460f1-105">Visual Basic fornece um compilador de linha de comando como uma alternativa para compilar programas de dentro do ambiente de desenvolvimento integrado (IDE) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="460f1-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="460f1-106">O compilador de linha de comando foi projetado para situações em que você não exige o conjunto completo de recursos no IDE — por exemplo, quando você está usando ou escrever para computadores com espaço de memória ou armazenamento do sistema limitados.</span><span class="sxs-lookup"><span data-stu-id="460f1-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
  <span data-ttu-id="460f1-107">Para compilar arquivos de origem da IDE do Visual Studio, escolha o **construir** comando da **Build** menu.</span><span class="sxs-lookup"><span data-stu-id="460f1-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="460f1-108">Quando você compila arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando e suas opções na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="460f1-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="460f1-109">Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina as **detalhes da saída de build do projeto do MSBuild** para **Normal** ou um nível mais alto de detalhamento.</span><span class="sxs-lookup"><span data-stu-id="460f1-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="460f1-110">Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](https://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="460f1-110">For more information, see [How to: View, Save, and Configure Build Log Files](https://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="460f1-111">Você pode compilar arquivos de projeto (. vbproj) em um prompt de comando usando MSBuild.</span><span class="sxs-lookup"><span data-stu-id="460f1-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="460f1-112">Para obter mais informações, consulte [referência de linha de comando](/visualstudio/msbuild/msbuild-command-line-reference) e [passo a passo: usando o MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="460f1-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="460f1-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="460f1-113">In This Section</span></span>  
 [<span data-ttu-id="460f1-114">Como invocar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="460f1-114">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="460f1-115">Descreve como invocar o compilador de linha de comando no prompt do MS-DOS ou de um subdiretório específico.</span><span class="sxs-lookup"><span data-stu-id="460f1-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="460f1-116">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="460f1-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="460f1-117">Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="460f1-117">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="460f1-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="460f1-118">Related Sections</span></span>  
 [<span data-ttu-id="460f1-119">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="460f1-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="460f1-120">Fornece listas de opções do compilador, organizadas em ordem alfabética ou por finalidade.</span><span class="sxs-lookup"><span data-stu-id="460f1-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="460f1-121">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="460f1-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="460f1-122">Descreve como compilar determinadas seções de código.</span><span class="sxs-lookup"><span data-stu-id="460f1-122">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="460f1-123">Compilando e limpando projetos e soluções no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="460f1-123">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="460f1-124">Descreve como organizar o que será incluído em diferentes compilações, escolha as propriedades do projeto e certifique-se de que os projetos de build na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="460f1-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
