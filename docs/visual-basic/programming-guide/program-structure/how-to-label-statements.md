---
title: Como rotular instruções (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="5d7a9-102">Como rotular instruções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d7a9-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="5d7a9-103">Blocos de instrução são compostos de linhas de código delimitado por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="5d7a9-104">Linhas de código precedido por uma cadeia de caracteres ou inteiro de identificação são consideradas *rotulada*.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="5d7a9-105">Rótulos de instruções são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="5d7a9-106">Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic, como aquelas que identificam os elementos de programação — ou literais inteiro.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="5d7a9-107">Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="5d7a9-108">O compilador identifica rótulos, verificando se o início da linha corresponde a qualquer identificador já definido.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="5d7a9-109">Se não existir, o compilador assumirá que seja um rótulo.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="5d7a9-110">Rótulos tem seu próprio espaço de declaração e não interferem em outros identificadores.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="5d7a9-111">Escopo do rótulo é o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="5d7a9-112">Declaração de rótulo terá precedência em qualquer situação ambígua.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d7a9-113">Rótulos podem ser usados somente em declarações executáveis dentro dos métodos.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="5d7a9-114">Para identificar uma linha de código</span><span class="sxs-lookup"><span data-stu-id="5d7a9-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="5d7a9-115">Coloque um identificador, seguido por dois-pontos, no início da linha do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="5d7a9-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="5d7a9-116">Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="5d7a9-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5d7a9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d7a9-117">See Also</span></span>  
 [<span data-ttu-id="5d7a9-118">Instruções</span><span class="sxs-lookup"><span data-stu-id="5d7a9-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="5d7a9-119">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="5d7a9-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="5d7a9-120">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="5d7a9-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
