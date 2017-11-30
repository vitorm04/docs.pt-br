---
title: "Linhas de comando de compilação de exemplo (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e168d40a22ca3737bee18f966df95988a2736a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="1267d-102">Linhas de comando de compilação de exemplo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1267d-102">Sample Compilation Command Lines (Visual Basic)</span></span>
<span data-ttu-id="1267d-103">Como uma alternativa para compilar [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programas no [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).</span><span class="sxs-lookup"><span data-stu-id="1267d-103">As an alternative to compiling [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs from within [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="1267d-104">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador de linha de comando dá suporte a um conjunto completo de opções que controlam os arquivos de entrada e saídos, assemblies e de depuração e opções de pré-processador.</span><span class="sxs-lookup"><span data-stu-id="1267d-104">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="1267d-105">Cada opção está disponível em duas formas intercambiáveis: `-``option` e `/``option`.</span><span class="sxs-lookup"><span data-stu-id="1267d-105">Each option is available in two interchangeable forms: `-``option` and `/``option`.</span></span> <span data-ttu-id="1267d-106">Esta documentação mostra apenas o `/``option` formulário.</span><span class="sxs-lookup"><span data-stu-id="1267d-106">This documentation shows only the `/``option` form.</span></span>  
  
 <span data-ttu-id="1267d-107">A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="1267d-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="1267d-108">Para</span><span class="sxs-lookup"><span data-stu-id="1267d-108">To</span></span>|<span data-ttu-id="1267d-109">Use</span><span class="sxs-lookup"><span data-stu-id="1267d-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="1267d-110">Compilar File. vb e criar File.exe</span><span class="sxs-lookup"><span data-stu-id="1267d-110">Compile File.vb and create File.exe</span></span>|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="1267d-111">Compilar File. vb e criar File. dll</span><span class="sxs-lookup"><span data-stu-id="1267d-111">Compile File.vb and create File.dll</span></span>|`vbc /target:library File.vb`|  
|<span data-ttu-id="1267d-112">Compilar File. vb e criar My.exe</span><span class="sxs-lookup"><span data-stu-id="1267d-112">Compile File.vb and create My.exe</span></span>|`vbc /out:My.exe File.vb`|  
|<span data-ttu-id="1267d-113">Compilar todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual, com otimizações em e `DEBUG` símbolo definido, produzindo File2.exe</span><span class="sxs-lookup"><span data-stu-id="1267d-113">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|<span data-ttu-id="1267d-114">Compilar todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual, produzindo uma versão de depuração do arquivo File2. dll sem mostrar o logotipo ou avisos</span><span class="sxs-lookup"><span data-stu-id="1267d-114">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|<span data-ttu-id="1267d-115">Compilar todos os [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] arquivos no diretório atual para Something. dll</span><span class="sxs-lookup"><span data-stu-id="1267d-115">Compile all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory to Something.dll</span></span>|`vbc /target:library /out:Something.dll *.vb`|  
  
 <span data-ttu-id="1267d-116">Ao compilar na linha de comando, você deve referenciar explicitamente o Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteca de tempo de execução por meio de `/reference` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="1267d-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="1267d-117">Quando você cria um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** com suas opções de compilador na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="1267d-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="1267d-118">Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e, em seguida, defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um nível mais alto de detalhes.</span><span class="sxs-lookup"><span data-stu-id="1267d-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="1267d-119">Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="1267d-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1267d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1267d-120">See Also</span></span>  
 [<span data-ttu-id="1267d-121">Compilador de linha de comando do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1267d-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1267d-122">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="1267d-122">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
