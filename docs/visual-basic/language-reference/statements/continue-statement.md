---
title: Instrução Continue (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 5523be69f2901851c86f6c0263548e3577507ff9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835369"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="56515-102">Instrução Continue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56515-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="56515-103">Transfere o controle imediatamente para a próxima iteração de um loop.</span><span class="sxs-lookup"><span data-stu-id="56515-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56515-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56515-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="56515-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="56515-105">Remarks</span></span>  
 <span data-ttu-id="56515-106">Você pode transferir de dentro de um `Do`, `For`, ou `While` loop para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="56515-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="56515-107">Controle passa imediatamente para o teste de condição de loop, que é equivalente a transferir para o `For` ou `While` instrução, ou para o `Do` ou `Loop` instrução que contém o `Until` ou `While` cláusula.</span><span class="sxs-lookup"><span data-stu-id="56515-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="56515-108">Você pode usar `Continue` em qualquer local no loop que permite transferências.</span><span class="sxs-lookup"><span data-stu-id="56515-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="56515-109">As regras que permite a transferência de controle são o mesmo que o [instrução GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="56515-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="56515-110">Por exemplo, se um loop está totalmente contido dentro de um `Try` bloco, um `Catch` bloco, ou um `Finally` bloco, você pode usar `Continue` para transferir o loop.</span><span class="sxs-lookup"><span data-stu-id="56515-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="56515-111">Se, por outro lado, o `Try`... `End Try` estrutura está contida dentro do loop, você não pode usar `Continue` para transferir o controle da `Finally` bloco e você pode usá-lo para transferir de uma `Try` ou `Catch` bloquear somente se você transferir completamente fora do `Try`... `End Try` estrutura.</span><span class="sxs-lookup"><span data-stu-id="56515-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="56515-112">Se você tem loops aninhados do mesmo tipo, por exemplo uma `Do` loop dentro de outra `Do` loop, um `Continue Do` ignora a instrução para a próxima iteração de mais interna `Do` loop que o contém.</span><span class="sxs-lookup"><span data-stu-id="56515-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="56515-113">Não é possível usar `Continue` para ignorar a próxima iteração de um loop que contém o mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="56515-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="56515-114">Se você tem loops aninhados de diferentes tipos, por exemplo uma `Do` loop dentro de uma `For` loop, pule para a próxima iteração de qualquer um loop usando a `Continue Do` ou `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="56515-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56515-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56515-115">Example</span></span>  
 <span data-ttu-id="56515-116">O seguinte exemplo de código usa o `Continue While` instrução para ignorar a próxima coluna de uma matriz se o divisor é zero.</span><span class="sxs-lookup"><span data-stu-id="56515-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="56515-117">O `Continue While` está dentro de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="56515-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="56515-118">Ele transfere para o `While col < lastcol` instrução, que é a próxima iteração do mais interna `While` loop que contém o `For` loop.</span><span class="sxs-lookup"><span data-stu-id="56515-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="56515-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56515-119">See also</span></span>

- [<span data-ttu-id="56515-120">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="56515-120">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="56515-121">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="56515-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="56515-122">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="56515-122">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="56515-123">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="56515-123">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
