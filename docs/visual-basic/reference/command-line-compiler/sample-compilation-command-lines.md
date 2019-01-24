---
title: Linhas de comando de compilação de exemplo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: 601f8f3a5ea86da060b2d26796b2299d87946443
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547794"
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="dedb0-102">Exemplos de linhas de comando de compilação (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dedb0-102">Sample compilation command lines (Visual Basic)</span></span>
<span data-ttu-id="dedb0-103">Como uma alternativa para compilar programas do Visual Basic de dentro do Visual Studio, você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).</span><span class="sxs-lookup"><span data-stu-id="dedb0-103">As an alternative to compiling Visual Basic programs from within Visual Studio, you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="dedb0-104">O compilador de linha de comando do Visual Basic dá suporte a um conjunto completo de opções que controlam a entrada e saída de arquivos, assemblies e opções de depuração e pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="dedb0-104">The Visual Basic command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="dedb0-105">Cada opção está disponível em duas formas intercambiáveis: `-option` e `/option`.</span><span class="sxs-lookup"><span data-stu-id="dedb0-105">Each option is available in two interchangeable forms: `-option` and `/option`.</span></span> <span data-ttu-id="dedb0-106">Esta documentação mostra apenas o `-option` formulário.</span><span class="sxs-lookup"><span data-stu-id="dedb0-106">This documentation shows only the `-option` form.</span></span>  
  
 <span data-ttu-id="dedb0-107">A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="dedb0-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="dedb0-108">Para</span><span class="sxs-lookup"><span data-stu-id="dedb0-108">To</span></span>|<span data-ttu-id="dedb0-109">Use</span><span class="sxs-lookup"><span data-stu-id="dedb0-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="dedb0-110">Compilar File. vb e criar File.exe</span><span class="sxs-lookup"><span data-stu-id="dedb0-110">Compile File.vb and create File.exe</span></span>|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="dedb0-111">Compilar File. vb e criar File. dll</span><span class="sxs-lookup"><span data-stu-id="dedb0-111">Compile File.vb and create File.dll</span></span>|`vbc -target:library File.vb`|  
|<span data-ttu-id="dedb0-112">Compilar File. vb e criar My.exe</span><span class="sxs-lookup"><span data-stu-id="dedb0-112">Compile File.vb and create My.exe</span></span>|`vbc -out:My.exe File.vb`|  
|<span data-ttu-id="dedb0-113">Compilar File. vb e criar uma biblioteca e um assembly de referência chamado File. dll</span><span class="sxs-lookup"><span data-stu-id="dedb0-113">Compile File.vb and create both a library and a reference assembly named File.dll</span></span>|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|<span data-ttu-id="dedb0-114">Compilar todos os arquivos do Visual Basic no diretório atual, com otimizações em e o `DEBUG` símbolo definido, produzindo File2.exe</span><span class="sxs-lookup"><span data-stu-id="dedb0-114">Compile all Visual Basic files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|  
|<span data-ttu-id="dedb0-115">Compilar todos os arquivos do Visual Basic no diretório atual, produzindo uma versão de depuração de File2.dll sem exibir o logotipo ou avisos</span><span class="sxs-lookup"><span data-stu-id="dedb0-115">Compile all Visual Basic files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|  
|<span data-ttu-id="dedb0-116">Compilar todos os arquivos do Visual Basic no diretório atual para Something. dll</span><span class="sxs-lookup"><span data-stu-id="dedb0-116">Compile all Visual Basic files in the current directory to Something.dll</span></span>|`vbc -target:library -out:Something.dll *.vb`|  
  
> [!TIP]
>  <span data-ttu-id="dedb0-117">Quando você compila um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** com suas opções de compilador na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="dedb0-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="dedb0-118">Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina as **detalhes da saída de build do projeto do MSBuild** para **Normal** ou um nível mais alto de detalhamento.</span><span class="sxs-lookup"><span data-stu-id="dedb0-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="dedb0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dedb0-119">See also</span></span>
- [<span data-ttu-id="dedb0-120">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dedb0-120">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="dedb0-121">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="dedb0-121">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
