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
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046436"
---
# <a name="building-from-the-command-line-visual-basic"></a><span data-ttu-id="aa749-102">Compilando a partir da linha de comando (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa749-102">Building from the Command Line (Visual Basic)</span></span>

<span data-ttu-id="aa749-103">Um projeto Visual Basic é composto por um ou mais arquivos de origem separados.</span><span class="sxs-lookup"><span data-stu-id="aa749-103">A Visual Basic project is made up of one or more separate source files.</span></span> <span data-ttu-id="aa749-104">Durante o processo conhecido como compilação, esses arquivos são trazidos juntos em um pacote — um único arquivo executável que pode ser executado como um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa749-104">During the process known as compilation, these files are brought together into one package—a single executable file that can be run as an application.</span></span>

<span data-ttu-id="aa749-105">O Visual Basic fornece um compilador de linha de comando como uma alternativa à compilação de programas de dentro do IDE (ambiente de desenvolvimento integrado) do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa749-105">Visual Basic provides a command-line compiler as an alternative to compiling programs from within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="aa749-106">O compilador de linha de comando foi projetado para situações em que você não precisa do conjunto completo de recursos no IDE — por exemplo, ao usar ou gravar para computadores com memória limitada do sistema ou espaço de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="aa749-106">The command-line compiler is designed for situations in which you do not require the full set of features in the IDE—for example, when you are using or writing for computers with limited system memory or storage space.</span></span>

<span data-ttu-id="aa749-107">Para compilar arquivos de origem de dentro do IDE do Visual Studio, escolha o comando **Compilar** no menu **Compilar** .</span><span class="sxs-lookup"><span data-stu-id="aa749-107">To compile source files from within the Visual Studio IDE, choose the **Build** command from the **Build** menu.</span></span>

> [!TIP]
> <span data-ttu-id="aa749-108">Ao criar arquivos de projeto usando o IDE do Visual Studio, você pode exibir informações sobre o comando **Vbc** associado e suas opções na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="aa749-108">When you build project files by using the Visual Studio IDE, you can display information about the associated **vbc** command and its switches in the output window.</span></span> <span data-ttu-id="aa749-109">Para exibir essas informações, abra a [caixa de diálogo opções, projetos e soluções, compile e execute](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o detalhamento de **saída de compilação do projeto MSBuild** como **normal** ou um nível mais alto de detalhamento.</span><span class="sxs-lookup"><span data-stu-id="aa749-109">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="aa749-110">Para obter mais informações, confira [Como: Exibir, salvar e configurar arquivos](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)de log de compilação.</span><span class="sxs-lookup"><span data-stu-id="aa749-110">For more information, see [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files).</span></span>

<span data-ttu-id="aa749-111">Você pode compilar arquivos de projeto (. vbproj) em um prompt de comando usando o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="aa749-111">You can compile project (.vbproj) files at a command prompt by using MSBuild.</span></span> <span data-ttu-id="aa749-112">Para obter mais informações, consulte [referência de linha](/visualstudio/msbuild/msbuild-command-line-reference) de [comando e passo a passos: Usando o MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span><span class="sxs-lookup"><span data-stu-id="aa749-112">For more information, see [Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) and [Walkthrough: Using MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="aa749-113">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="aa749-113">In This Section</span></span>

<span data-ttu-id="aa749-114">[Como: Invocar o compilador de linha de comando](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span><span class="sxs-lookup"><span data-stu-id="aa749-114">[How to: Invoke the Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) </span></span>\
<span data-ttu-id="aa749-115">Descreve como invocar o compilador de linha de comando no prompt do MS-DOS ou em um subdiretório específico.</span><span class="sxs-lookup"><span data-stu-id="aa749-115">Describes how to invoke the command-line compiler at the MS-DOS prompt or from a specific subdirectory.</span></span>

<span data-ttu-id="aa749-116">[Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="aa749-116">[Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>\
<span data-ttu-id="aa749-117">Fornece uma lista de linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="aa749-117">Provides a list of sample command lines that you can modify for your own use.</span></span>

## <a name="related-sections"></a><span data-ttu-id="aa749-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="aa749-118">Related Sections</span></span>

<span data-ttu-id="aa749-119">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="aa749-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>\
<span data-ttu-id="aa749-120">Fornece listas de opções de compilador, organizadas em ordem alfabética ou por finalidade.</span><span class="sxs-lookup"><span data-stu-id="aa749-120">Provides lists of compiler options, organized alphabetically or by purpose.</span></span>

<span data-ttu-id="aa749-121">[Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="aa749-121">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>\
<span data-ttu-id="aa749-122">Descreve como compilar seções específicas de código.</span><span class="sxs-lookup"><span data-stu-id="aa749-122">Describes how to compile particular sections of code.</span></span>

<span data-ttu-id="aa749-123">[Compilando e limpando projetos e soluções no Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="aa749-123">[Building and Cleaning Projects and Solutions in Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) </span></span>\
<span data-ttu-id="aa749-124">Descreve como organizar o que será incluído em compilações diferentes, escolher Propriedades do projeto e garantir que os projetos sejam criados na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="aa749-124">Describes how to organize what will be included in different builds, choose project properties, and ensure that projects build in the correct order.</span></span>
