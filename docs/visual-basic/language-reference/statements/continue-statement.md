---
title: Instrução Continue
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: fd604b281a590073a5e76398788d7648cadd145c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382088"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="e2fe2-102">Instrução Continue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2fe2-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="e2fe2-103">Transfere o controle imediatamente para a próxima iteração de um loop.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2fe2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2fe2-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="e2fe2-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2fe2-105">Remarks</span></span>  
 <span data-ttu-id="e2fe2-106">Você pode transferir de dentro de `Do` um `For` loop, ou `While` para a próxima iteração desse loop.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="e2fe2-107">O controle passa imediatamente para o teste de condição de loop, que é equivalente a transferir para a `For` `While` instrução or, ou para a `Do` `Loop` instrução or que contém a `Until` `While` cláusula or.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="e2fe2-108">Você pode usar `Continue` em qualquer local no loop que permita transferências.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="e2fe2-109">As regras que permitem a transferência de controle são as mesmas que a [instrução goto](goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e2fe2-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="e2fe2-110">Por exemplo, se um loop estiver totalmente contido em um `Try` bloco, um `Catch` bloco ou um `Finally` bloco, você poderá usar `Continue` para transferir para fora do loop.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="e2fe2-111">Se, por outro lado, a `Try` estrutura... `End Try` estiver contida no loop, você não poderá usar o `Continue` para transferir o controle para fora do `Finally` bloco e poderá usá-lo para transferir para fora de `Try` um `Catch` bloco ou somente se você transferir completamente da `Try` estrutura... `End Try` .</span><span class="sxs-lookup"><span data-stu-id="e2fe2-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="e2fe2-112">Se você tiver loops aninhados do mesmo tipo, por exemplo um `Do` loop dentro de outro `Do` loop, uma `Continue Do` instrução passará para a próxima iteração do `Do` loop mais interno que o contém.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="e2fe2-113">Você não pode usar `Continue` para pular para a próxima iteração de um loop de contenção do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="e2fe2-114">Se você tiver loops aninhados de tipos diferentes, por exemplo um `Do` loop dentro de um `For` loop, poderá pular para a próxima iteração de qualquer um dos loops usando o `Continue Do` ou o `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="e2fe2-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2fe2-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2fe2-115">Example</span></span>  
 <span data-ttu-id="e2fe2-116">O exemplo de código a seguir usa a `Continue While` instrução para pular para a próxima coluna de uma matriz se um divisor for zero.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="e2fe2-117">O `Continue While` está dentro de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="e2fe2-118">Ele transfere para a `While col < lastcol` instrução, que é a próxima iteração do `While` loop mais interno que contém o `For` loop.</span><span class="sxs-lookup"><span data-stu-id="e2fe2-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="e2fe2-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="e2fe2-119">See also</span></span>

- [<span data-ttu-id="e2fe2-120">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="e2fe2-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="e2fe2-121">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="e2fe2-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="e2fe2-122">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="e2fe2-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="e2fe2-123">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="e2fe2-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
