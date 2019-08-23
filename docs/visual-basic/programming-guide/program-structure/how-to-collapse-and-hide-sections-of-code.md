---
title: 'Como: Recolher e ocultar seções de código (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: db396adf24c12542f720d3b235068aea2329288d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949725"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="d9b35-102">Como: Recolher e ocultar seções de código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9b35-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="d9b35-103">A `#Region` diretiva permite que você recolha e oculte seções de código em arquivos Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9b35-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="d9b35-104">A `#Region` diretiva permite especificar um bloco de código que você pode expandir ou recolher ao usar o editor de código do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9b35-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="d9b35-105">A capacidade de ocultar o código seletivamente torna os arquivos mais gerenciáveis e fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="d9b35-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="d9b35-106">Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="d9b35-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="d9b35-107">`#Region`as diretivas dão suporte à semântica de bloco `#If...#End If`de código, como.</span><span class="sxs-lookup"><span data-stu-id="d9b35-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="d9b35-108">Isso significa que eles não podem começar em um bloco e terminar em outro; o início e o fim devem estar no mesmo bloco.</span><span class="sxs-lookup"><span data-stu-id="d9b35-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="d9b35-109">`#Region`Não há suporte para diretivas em funções.</span><span class="sxs-lookup"><span data-stu-id="d9b35-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="d9b35-110">Para recolher e ocultar uma seção de código</span><span class="sxs-lookup"><span data-stu-id="d9b35-110">To collapse and hide a section of code</span></span>  
  
- <span data-ttu-id="d9b35-111">Coloque a seção de código entre as `#Region` instruções `#End Region` e, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d9b35-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     <span data-ttu-id="d9b35-112">O `#Region` bloco pode ser usado várias vezes em um arquivo de código; assim, os usuários podem definir seus próprios blocos de procedimentos e classes que podem, por sua vez, ser recolhidos.</span><span class="sxs-lookup"><span data-stu-id="d9b35-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="d9b35-113">`#Region`os blocos também podem ser aninhados `#Region` dentro de outros blocos.</span><span class="sxs-lookup"><span data-stu-id="d9b35-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d9b35-114">Ocultar o código não impede que ele seja compilado e não afeta `#If...#End If` as instruções.</span><span class="sxs-lookup"><span data-stu-id="d9b35-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b35-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9b35-115">See also</span></span>

- [<span data-ttu-id="d9b35-116">Compilação Condicional</span><span class="sxs-lookup"><span data-stu-id="d9b35-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="d9b35-117">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="d9b35-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="d9b35-118">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="d9b35-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="d9b35-119">Estrutura de tópicos</span><span class="sxs-lookup"><span data-stu-id="d9b35-119">Outlining</span></span>](/visualstudio/ide/outlining)
