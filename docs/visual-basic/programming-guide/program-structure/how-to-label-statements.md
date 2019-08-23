---
title: 'Como: Instruções Label (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 6b442b5a0ad731cfc490a7387c78ac9279dddaf0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961329"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="43310-102">Como: Instruções Label (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43310-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="43310-103">Os blocos de instrução são compostos por linhas de código delimitadas por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="43310-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="43310-104">As linhas de código precedidas por uma cadeia de caracteres de identificação ouum número inteiro são consideradas rotuladas.</span><span class="sxs-lookup"><span data-stu-id="43310-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="43310-105">Os `On Error Goto`rótulos de instrução são usados para marcar uma linha de código para identificá-lo para uso com instruções como.</span><span class="sxs-lookup"><span data-stu-id="43310-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="43310-106">Os rótulos podem ser identificadores de Visual Basic válidos — como aqueles que identificam elementos de programação — ou literais inteiros.</span><span class="sxs-lookup"><span data-stu-id="43310-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="43310-107">Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente de ser seguido por uma instrução na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="43310-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="43310-108">O compilador identifica os rótulos verificando se o início da linha corresponde a qualquer identificador já definido.</span><span class="sxs-lookup"><span data-stu-id="43310-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="43310-109">Caso contrário, o compilador pressupõe que ele é um rótulo.</span><span class="sxs-lookup"><span data-stu-id="43310-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="43310-110">Os rótulos têm seu próprio espaço de declaração e não interferem em outros identificadores.</span><span class="sxs-lookup"><span data-stu-id="43310-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="43310-111">O escopo de um rótulo é o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="43310-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="43310-112">A declaração de rótulo tem precedência em qualquer situação ambígua.</span><span class="sxs-lookup"><span data-stu-id="43310-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43310-113">Os rótulos só podem ser usados em instruções Executáveis dentro de métodos.</span><span class="sxs-lookup"><span data-stu-id="43310-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="43310-114">Para rotular uma linha de código</span><span class="sxs-lookup"><span data-stu-id="43310-114">To label a line of code</span></span>  
  
- <span data-ttu-id="43310-115">Coloque um identificador, seguido por dois-pontos, no início da linha de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="43310-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="43310-116">Por exemplo, as linhas de código a seguir são rotuladas `Jump` com `120`e, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="43310-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="43310-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43310-117">See also</span></span>

- [<span data-ttu-id="43310-118">Instruções</span><span class="sxs-lookup"><span data-stu-id="43310-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="43310-119">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="43310-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="43310-120">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="43310-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
