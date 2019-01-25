---
title: Instrução Call (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: e706650ac6da84d9b4e77fc549811e731be61b92
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594155"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="d57a8-102">Instrução Call (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d57a8-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="d57a8-103">Transfere o controle para um `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="d57a8-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d57a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d57a8-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d57a8-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d57a8-105">Parts</span></span>  
|||
|---|---|
|`procedureName`|<span data-ttu-id="d57a8-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d57a8-106">Required.</span></span> <span data-ttu-id="d57a8-107">Nome do procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="d57a8-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="d57a8-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d57a8-108">Optional.</span></span> <span data-ttu-id="d57a8-109">Lista de variáveis ou expressões que representam os argumentos são passados para o procedimento quando ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="d57a8-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="d57a8-110">Vários argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d57a8-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="d57a8-111">Se você incluir `argumentList`, você deve colocá-la entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d57a8-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="d57a8-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d57a8-112">Remarks</span></span>  
 <span data-ttu-id="d57a8-113">Você pode usar o `Call` palavra-chave quando você chama um procedimento.</span><span class="sxs-lookup"><span data-stu-id="d57a8-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="d57a8-114">Para a maioria das chamadas de procedimento, não é necessário usar essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d57a8-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="d57a8-115">Normalmente, você usa o `Call` palavra-chave quando a expressão de chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="d57a8-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="d57a8-116">Usar o `Call` palavra-chave para outros usos não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="d57a8-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="d57a8-117">Se o procedimento retorna um valor, o `Call` instrução descarta-lo.</span><span class="sxs-lookup"><span data-stu-id="d57a8-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d57a8-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d57a8-118">Example</span></span>  
 <span data-ttu-id="d57a8-119">O código a seguir mostra dois exemplos em que o `Call` palavra-chave é necessária para chamar um procedimento.</span><span class="sxs-lookup"><span data-stu-id="d57a8-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="d57a8-120">Nos dois exemplos, a expressão de chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="d57a8-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d57a8-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d57a8-121">See also</span></span>
- [<span data-ttu-id="d57a8-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="d57a8-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d57a8-123">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d57a8-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d57a8-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="d57a8-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="d57a8-125">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="d57a8-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
