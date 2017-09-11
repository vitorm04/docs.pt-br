---
title: "Como: Recolher e ocultar seções de código (Visual Basic) | Documentos do Microsoft"
ms.custom: 
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
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4dcd5cd5d79629fd008534112cb72d5bcfec476e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="7f53b-102">Como recolher e ocultar seções do código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f53b-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="7f53b-103">O `#Region` diretiva permite que você recolher e ocultar seções de código em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] arquivos.</span><span class="sxs-lookup"><span data-stu-id="7f53b-103">The `#Region` directive enables you to collapse and hide sections of code in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files.</span></span> <span data-ttu-id="7f53b-104">O `#Region` diretiva permite que você especifique um bloco de código que você pode expandir ou recolher ao usar o [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7f53b-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] code editor.</span></span> <span data-ttu-id="7f53b-105">A capacidade de ocultar código seletivamente torna os arquivos mais gerenciável e mais fácil de ler.</span><span class="sxs-lookup"><span data-stu-id="7f53b-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="7f53b-106">Para obter mais informações, consulte [Estrutura de tópicos](https://docs.microsoft.com/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="7f53b-106">For more information, see [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="7f53b-107">`#Region`diretivas de suportam a semântica do bloco de código como `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="7f53b-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="7f53b-108">Isso significa que eles não podem começar em um bloco e terminam em outra; o início e fim devem ser no mesmo bloco.</span><span class="sxs-lookup"><span data-stu-id="7f53b-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="7f53b-109">`#Region`Não há suporte para diretivas dentro de funções.</span><span class="sxs-lookup"><span data-stu-id="7f53b-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="7f53b-110">Para recolher e ocultar uma seção de código</span><span class="sxs-lookup"><span data-stu-id="7f53b-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="7f53b-111">Coloque a seção de código entre o `#Region` e `#End Region` instruções, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7f53b-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     <span data-ttu-id="7f53b-112">[!code-vb[VbVbalrConditionalComp n º&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7f53b-112">[!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]</span></span>  
  
     <span data-ttu-id="7f53b-113">O `#Region` bloco pode ser usado várias vezes em um arquivo de código; assim, os usuários podem definir seus próprios blocos de procedimentos e as classes que podem, por sua vez, ser recolhidos.</span><span class="sxs-lookup"><span data-stu-id="7f53b-113">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="7f53b-114">`#Region`blocos também podem ser aninhados em outros `#Region` blocos.</span><span class="sxs-lookup"><span data-stu-id="7f53b-114">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7f53b-115">Ocultar o código não impede que ele seja compilado e não afeta `#If...#End If` instruções.</span><span class="sxs-lookup"><span data-stu-id="7f53b-115">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f53b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f53b-116">See Also</span></span>  
 <span data-ttu-id="7f53b-117">[Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span><span class="sxs-lookup"><span data-stu-id="7f53b-117">[Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) </span></span>  
<span data-ttu-id="7f53b-118"> [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md) </span><span class="sxs-lookup"><span data-stu-id="7f53b-118"> [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) </span></span>  
<span data-ttu-id="7f53b-119"> [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="7f53b-119"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="7f53b-120"> [Estrutura de tópicos](https://docs.microsoft.com/visualstudio/ide/outlining)</span><span class="sxs-lookup"><span data-stu-id="7f53b-120"> [Outlining](https://docs.microsoft.com/visualstudio/ide/outlining)</span></span>
