---
title: Como recolher e ocultar seções do código (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4497c9586182cca9e2be97dc39e5ccb242725d25
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="39146-102">Como recolher e ocultar seções do código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39146-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="39146-103">O `#Region` diretiva permite que você recolher e ocultar seções de código em arquivos do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="39146-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="39146-104">O `#Region` diretiva permite especificar um bloco de código que você pode expandir ou recolher ao usar o editor de códigos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39146-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="39146-105">A capacidade de ocultar código seletivamente torna os arquivos mais gerenciáveis e mais fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="39146-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="39146-106">Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="39146-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="39146-107">`#Region` diretivas de suportam a semântica do bloco de código como `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="39146-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="39146-108">Isso significa que eles não podem começar em um bloco e terminar em outra; o início e término devem estar no mesmo bloco.</span><span class="sxs-lookup"><span data-stu-id="39146-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="39146-109">`#Region` Não há suporte para diretivas dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="39146-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="39146-110">Para recolher e ocultar uma seção de código</span><span class="sxs-lookup"><span data-stu-id="39146-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="39146-111">Coloque a seção de código entre as `#Region` e `#End Region` instruções, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="39146-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="39146-112">O `#Region` bloco pode ser usado várias vezes em um arquivo de código; portanto, os usuários podem definir seus próprios blocos de procedimentos e classes que por sua vez, podem ser recolhidos.</span><span class="sxs-lookup"><span data-stu-id="39146-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="39146-113">`#Region` blocos também podem ser aninhados em outros `#Region` blocos.</span><span class="sxs-lookup"><span data-stu-id="39146-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="39146-114">Ocultando código não impede que ele está sendo compilada e não afeta `#If...#End If` instruções.</span><span class="sxs-lookup"><span data-stu-id="39146-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39146-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39146-115">See Also</span></span>  
 [<span data-ttu-id="39146-116">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="39146-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="39146-117">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="39146-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="39146-118">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="39146-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="39146-119">Estrutura de tópicos</span><span class="sxs-lookup"><span data-stu-id="39146-119">Outlining</span></span>](/visualstudio/ide/outlining)
