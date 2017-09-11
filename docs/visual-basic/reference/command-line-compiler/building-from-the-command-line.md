---
title: Compilando na linha de comando (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e7550a4a54637ea5ef425a1cb7ae02abd07808a8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="0781e-102">Compilando a partir da linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0781e-102">Building from the Command Line (Visual Basic)</span></span>
<span data-ttu-id="0781e-103">Um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projeto é composto de um ou mais arquivos de origem separado.</span><span class="sxs-lookup"><span data-stu-id="0781e-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project is made up of one or more separate source files.</span></span> <span data-ttu-id="0781e-104">Durante o processo conhecido como compilação, esses arquivos são reunidos em um único pacote — um único arquivo executável que pode ser executado como um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0781e-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="0781e-105">Fornece um compilador de linha de comando como uma alternativa para compilar programas de dentro do [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE).</span><span class="sxs-lookup"><span data-stu-id="0781e-105"> provides a command-line compiler as an alternative to compiling programs from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] integrated development environment (IDE).</span></span> <span data-ttu-id="0781e-106">O compilador de linha de comando destina-se a situações em que não exigem que o conjunto completo de recursos no IDE — por exemplo, quando você estiver usando ou escrevendo para computadores com sistema limitados memória ou espaço de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0781e-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>  
  
 <span data-ttu-id="0781e-107">Quando compilar da linha de comando, você deve explicitamente referenciar o Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] biblioteca de tempo de execução por meio de `/reference` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="0781e-107">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
 <span data-ttu-id="0781e-108">Para compilar os arquivos de origem de dentro de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, escolha o **criar** comando do **criar** menu.</span><span class="sxs-lookup"><span data-stu-id="0781e-108">To compile source files from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE, choose the **Build** command from the **Build** menu.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="0781e-109">Quando você cria arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando e suas opções na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="0781e-109">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="0781e-110">Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um maior nível de detalhamento.</span><span class="sxs-lookup"><span data-stu-id="0781e-110">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="0781e-111">Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="0781e-111">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
 <span data-ttu-id="0781e-112">Você pode compilar os arquivos de projeto (. vbproj) em um prompt de comando usando o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0781e-112">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="0781e-113">Para obter mais informações, consulte [referência de linha de comando](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) e [passo a passo: usando MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).</span><span class="sxs-lookup"><span data-stu-id="0781e-113">For more information, see [Command-Line Reference](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0781e-114">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0781e-114">In This Section</span></span>  
 [<span data-ttu-id="0781e-115">Como invocar o compilador de linha de comando</span><span class="sxs-lookup"><span data-stu-id="0781e-115">How to: Invoke the Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 <span data-ttu-id="0781e-116">Descreve como invocar o compilador de linha de comando no prompt do MS-DOS ou de um subdiretório específico.</span><span class="sxs-lookup"><span data-stu-id="0781e-116">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>  
  
 [<span data-ttu-id="0781e-117">Linhas de Comando de Compilação de Exemplo</span><span class="sxs-lookup"><span data-stu-id="0781e-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="0781e-118">Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="0781e-118">Provides a list of sample command lines that you can modify for your own use.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0781e-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="0781e-119">Related Sections</span></span>  
 [<span data-ttu-id="0781e-120">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0781e-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="0781e-121">Fornece listas de opções do compilador, organizadas em ordem alfabética ou por finalidade.</span><span class="sxs-lookup"><span data-stu-id="0781e-121">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>  
  
 [<span data-ttu-id="0781e-122">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="0781e-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="0781e-123">Descreve como compilar determinadas seções de código.</span><span class="sxs-lookup"><span data-stu-id="0781e-123">Describes how to compile particular sections of code.</span></span>  
  
 [<span data-ttu-id="0781e-124">Compilando e limpando projetos e soluções no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0781e-124">Building and Cleaning Projects and Solutions in Visual Studio</span></span>](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="0781e-125">Descreve como organizar o que será incluído em diferentes compilações, escolha Propriedades do projeto e certifique-se de que projetos são compilados na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="0781e-125">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
