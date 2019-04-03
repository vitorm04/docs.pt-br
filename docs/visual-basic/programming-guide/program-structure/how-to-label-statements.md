---
title: 'Como: Rótulo de instruções (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 69ec8c7625410f140c59ba8dd492dca76857eb96
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828635"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="70b9f-102">Como: Rótulo de instruções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70b9f-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="70b9f-103">Blocos de instrução são compostos de linhas de código delimitado por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="70b9f-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="70b9f-104">Linhas de código precedida por um inteiro ou cadeia de caracteres de identificação são consideradas *rotulado*.</span><span class="sxs-lookup"><span data-stu-id="70b9f-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="70b9f-105">Rótulos de instrução são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="70b9f-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="70b9f-106">Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic — como aquelas que identificam os elementos de programação — ou literais inteiros.</span><span class="sxs-lookup"><span data-stu-id="70b9f-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="70b9f-107">Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="70b9f-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="70b9f-108">O compilador identifica rótulos, verificando se o início da linha corresponde a qualquer identificador já definido.</span><span class="sxs-lookup"><span data-stu-id="70b9f-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="70b9f-109">Se não existir, o compilador pressupõe que ele é um rótulo.</span><span class="sxs-lookup"><span data-stu-id="70b9f-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="70b9f-110">Rótulos tenham seu próprio espaço de declaração e não interfiram com outros identificadores.</span><span class="sxs-lookup"><span data-stu-id="70b9f-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="70b9f-111">Escopo de um rótulo é o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="70b9f-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="70b9f-112">Declaração de rótulo tem precedência em qualquer situação ambígua.</span><span class="sxs-lookup"><span data-stu-id="70b9f-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70b9f-113">Rótulos podem ser usados somente em declarações executáveis dentro de métodos.</span><span class="sxs-lookup"><span data-stu-id="70b9f-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="70b9f-114">Para rotular uma linha de código</span><span class="sxs-lookup"><span data-stu-id="70b9f-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="70b9f-115">Coloque um identificador, seguido por dois-pontos, no início da linha de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="70b9f-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="70b9f-116">Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="70b9f-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="70b9f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70b9f-117">See also</span></span>

- [<span data-ttu-id="70b9f-118">Instruções</span><span class="sxs-lookup"><span data-stu-id="70b9f-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="70b9f-119">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="70b9f-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="70b9f-120">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="70b9f-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
