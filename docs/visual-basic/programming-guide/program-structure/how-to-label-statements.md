---
title: 'Como: Rótulo de instruções (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 00a08bd3bd1f866cec883b6591b03ebd9d858b90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552249"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="a431b-102">Como: Rótulo de instruções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a431b-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="a431b-103">Blocos de instrução são compostos de linhas de código delimitado por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="a431b-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="a431b-104">Linhas de código precedida por um inteiro ou cadeia de caracteres de identificação são consideradas *rotulado*.</span><span class="sxs-lookup"><span data-stu-id="a431b-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="a431b-105">Rótulos de instrução são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="a431b-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="a431b-106">Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic — como aquelas que identificam os elementos de programação — ou literais inteiros.</span><span class="sxs-lookup"><span data-stu-id="a431b-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="a431b-107">Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="a431b-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="a431b-108">O compilador identifica rótulos, verificando se o início da linha corresponde a qualquer identificador já definido.</span><span class="sxs-lookup"><span data-stu-id="a431b-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="a431b-109">Se não existir, o compilador pressupõe que ele é um rótulo.</span><span class="sxs-lookup"><span data-stu-id="a431b-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="a431b-110">Rótulos tenham seu próprio espaço de declaração e não interfiram com outros identificadores.</span><span class="sxs-lookup"><span data-stu-id="a431b-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="a431b-111">Escopo de um rótulo é o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="a431b-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="a431b-112">Declaração de rótulo tem precedência em qualquer situação ambígua.</span><span class="sxs-lookup"><span data-stu-id="a431b-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a431b-113">Rótulos podem ser usados somente em declarações executáveis dentro de métodos.</span><span class="sxs-lookup"><span data-stu-id="a431b-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="a431b-114">Para rotular uma linha de código</span><span class="sxs-lookup"><span data-stu-id="a431b-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="a431b-115">Coloque um identificador, seguido por dois-pontos, no início da linha de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="a431b-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="a431b-116">Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="a431b-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a431b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a431b-117">See also</span></span>
- [<span data-ttu-id="a431b-118">Instruções</span><span class="sxs-lookup"><span data-stu-id="a431b-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="a431b-119">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="a431b-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="a431b-120">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="a431b-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
