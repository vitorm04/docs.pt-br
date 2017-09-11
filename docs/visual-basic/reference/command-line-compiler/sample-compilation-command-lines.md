---
title: "Exemplo de linhas de comando de compilação (Visual Basic) | Documentos do Microsoft"
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
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
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
ms.openlocfilehash: e58006c05f498ec1a9dbf5194fbc9bcdd281ab63
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a><span data-ttu-id="82a77-102">Linhas de comando de compilação de exemplo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82a77-102">Sample Compilation Command Lines (Visual Basic)</span></span>
<span data-ttu-id="82a77-103">Como uma alternativa para compilar [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programas no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], você pode compilar da linha de comando para produzir arquivos executáveis (.exe) ou arquivos de biblioteca de vínculo dinâmico (. dll).</span><span class="sxs-lookup"><span data-stu-id="82a77-103">As an alternative to compiling [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programs from within [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], you can compile from the command line to produce executable (.exe) files or dynamic-link library (.dll) files.</span></span>  
  
 <span data-ttu-id="82a77-104">O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador de linha de comando oferece suporte a um conjunto completo de opções que controlam arquivos de entrada e saídos, assemblies e depuração e pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="82a77-104">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] command-line compiler supports a complete set of options that control input and output files, assemblies, and debug and preprocessor options.</span></span> <span data-ttu-id="82a77-105">Cada opção está disponível em duas formas intercambiáveis: `-``option` e `/``option`.</span><span class="sxs-lookup"><span data-stu-id="82a77-105">Each option is available in two interchangeable forms: `-``option` and `/``option`.</span></span> <span data-ttu-id="82a77-106">Esta documentação mostra apenas o `/``option` formulário.</span><span class="sxs-lookup"><span data-stu-id="82a77-106">This documentation shows only the `/``option` form.</span></span>  
  
 <span data-ttu-id="82a77-107">A tabela a seguir lista algumas linhas de comando de exemplo que você pode modificar para seu próprio uso.</span><span class="sxs-lookup"><span data-stu-id="82a77-107">The following table lists some sample command lines you can modify for your own use.</span></span>  
  
|<span data-ttu-id="82a77-108">Para</span><span class="sxs-lookup"><span data-stu-id="82a77-108">To</span></span>|<span data-ttu-id="82a77-109">Uso</span><span class="sxs-lookup"><span data-stu-id="82a77-109">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="82a77-110">Compilar File. vb e criar File.exe</span><span class="sxs-lookup"><span data-stu-id="82a77-110">Compile File.vb and create File.exe</span></span>|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|<span data-ttu-id="82a77-111">Compilar File. vb e criar File. dll</span><span class="sxs-lookup"><span data-stu-id="82a77-111">Compile File.vb and create File.dll</span></span>|`vbc /target:library File.vb`|  
|<span data-ttu-id="82a77-112">Compilar File. vb e criar My.exe</span><span class="sxs-lookup"><span data-stu-id="82a77-112">Compile File.vb and create My.exe</span></span>|`vbc /out:My.exe File.vb`|  
|<span data-ttu-id="82a77-113">Compilar todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual, com otimizações e o `DEBUG` símbolo definido, produzindo File2.exe</span><span class="sxs-lookup"><span data-stu-id="82a77-113">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory, with optimizations on and the `DEBUG` symbol defined, producing File2.exe</span></span>|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|<span data-ttu-id="82a77-114">Compilar todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual, produzindo uma versão de depuração do arquivo File2. dll sem mostrar o logotipo ou avisos</span><span class="sxs-lookup"><span data-stu-id="82a77-114">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory, producing a debug version of File2.dll without displaying the logo or warnings</span></span>|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|<span data-ttu-id="82a77-115">Compilar todos os [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos no diretório atual para Something. dll</span><span class="sxs-lookup"><span data-stu-id="82a77-115">Compile all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory to Something.dll</span></span>|`vbc /target:library /out:Something.dll *.vb`|  
  
 <span data-ttu-id="82a77-116">Quando compilar da linha de comando, você deve explicitamente referenciar o Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] biblioteca de tempo de execução por meio de `/reference` opção de compilador.</span><span class="sxs-lookup"><span data-stu-id="82a77-116">When compiling from the command line, you must explicitly reference the Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] run-time library through the `/reference` compiler option.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="82a77-117">Quando você cria um projeto usando o IDE do Visual Studio, você pode exibir informações sobre associado **vbc** comando com suas opções de compilador na janela de saída.</span><span class="sxs-lookup"><span data-stu-id="82a77-117">When you build a project by using the Visual Studio IDE, you can display information about the associated **vbc** command with its compiler options in the output window.</span></span> <span data-ttu-id="82a77-118">Para exibir essas informações, abra o [caixa de diálogo Opções, projetos e soluções, compilação e execução](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)e defina o **detalhamento da saída de compilação de projeto MSBuild** para **Normal** ou um maior nível de detalhamento.</span><span class="sxs-lookup"><span data-stu-id="82a77-118">To display this information, open the [Options Dialog Box,  Projects and Solutions, Build and Run](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), and then set the **MSBuild project build output verbosity** to **Normal** or a higher level of verbosity.</span></span> <span data-ttu-id="82a77-119">Para obter mais informações, consulte [Como exibir, salvar e configurar arquivos de log de build](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span><span class="sxs-lookup"><span data-stu-id="82a77-119">For more information, see [How to: View, Save, and Configure Build Log Files](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82a77-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82a77-120">See Also</span></span>  
 <span data-ttu-id="82a77-121">[Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="82a77-121">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="82a77-122"> [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span><span class="sxs-lookup"><span data-stu-id="82a77-122"> [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)</span></span>
