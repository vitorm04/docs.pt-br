---
title: "Instrução Continue (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.continue
dev_langs:
- VB
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: 21
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
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 6d310f0180ad3ece69d7286aff0bdd60f548c9b1
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="ce47c-102">Instrução Continue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce47c-102">Continue Statement (Visual Basic)</span></span>
<span data-ttu-id="ce47c-103">Transfere o controle imediatamente para a próxima iteração de um loop.</span><span class="sxs-lookup"><span data-stu-id="ce47c-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce47c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce47c-104">Syntax</span></span>  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce47c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="ce47c-105">Remarks</span></span>  
 <span data-ttu-id="ce47c-106">Você pode transferir de dentro de um `Do`, `For`, ou `While` loop para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="ce47c-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="ce47c-107">Controle passa imediatamente para o teste de condição do loop, que é equivalente a transferir para a `For` ou `While` instrução, ou o `Do` ou `Loop` instrução que contém o `Until` ou `While` cláusula.</span><span class="sxs-lookup"><span data-stu-id="ce47c-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="ce47c-108">Você pode usar `Continue` em qualquer posição no loop que permite transferências.</span><span class="sxs-lookup"><span data-stu-id="ce47c-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="ce47c-109">As regras permitindo transferência de controle são o mesmo que o [instrução GoTo](../../../visual-basic/language-reference/statements/goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce47c-109">The rules allowing transfer of control are the same as with the [GoTo Statement](../../../visual-basic/language-reference/statements/goto-statement.md).</span></span>  
  
 <span data-ttu-id="ce47c-110">Por exemplo, se um loop está totalmente contido dentro de uma `Try` bloco, uma `Catch` bloco, ou um `Finally` bloco, você pode usar `Continue` para transferir para fora do loop.</span><span class="sxs-lookup"><span data-stu-id="ce47c-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="ce47c-111">Se, por outro lado, o `Try`... `End Try` estrutura está contida dentro do loop, você não pode usar `Continue` para transferir o controle do `Finally` bloco e você pode usá-lo para transferir fora de um `Try` ou `Catch` bloquear somente se você transferir completamente do `Try`... `End Try` estrutura.</span><span class="sxs-lookup"><span data-stu-id="ce47c-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="ce47c-112">Se você tem loops aninhados do mesmo tipo, por exemplo um `Do` loop dentro de outro `Do` loop, uma `Continue Do` ignora a instrução para a próxima iteração de mais interno `Do` loop que o contém.</span><span class="sxs-lookup"><span data-stu-id="ce47c-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="ce47c-113">Você não pode usar `Continue` para ignorar a próxima iteração de um loop continente do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="ce47c-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="ce47c-114">Se você tem loops aninhados de diferentes tipos, por exemplo um `Do` um loop dentro de um `For` loop, você poderá pular para a próxima iteração de qualquer um loop usando `Continue Do` ou `Continue For`.</span><span class="sxs-lookup"><span data-stu-id="ce47c-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce47c-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ce47c-115">Example</span></span>  
 <span data-ttu-id="ce47c-116">O seguinte exemplo de código usa o `Continue While` instrução para ignorar a próxima coluna de uma matriz se o divisor é zero.</span><span class="sxs-lookup"><span data-stu-id="ce47c-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="ce47c-117">O `Continue While` está dentro de um `For` loop.</span><span class="sxs-lookup"><span data-stu-id="ce47c-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="ce47c-118">Transfere para o `While col < lastcol` instrução, que é a próxima iteração de mais interno `While` loop que contém o `For` loop.</span><span class="sxs-lookup"><span data-stu-id="ce47c-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 <span data-ttu-id="ce47c-119">[!code-vb[VbVbalrStatements&#14;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ce47c-119">[!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce47c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce47c-120">See Also</span></span>  
 <span data-ttu-id="ce47c-121">[Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ce47c-121">[Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span></span>  
<span data-ttu-id="ce47c-122"> [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ce47c-122"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="ce47c-123"> [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ce47c-123"> [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) </span></span>  
<span data-ttu-id="ce47c-124"> [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ce47c-124"> [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)</span></span>

