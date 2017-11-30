---
title: "Instrução Call (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c72450fd6f931f36f640d3e384a6fd38d57a7a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="e0699-102">Instrução Call (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0699-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="e0699-103">Transfere o controle para um `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="e0699-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0699-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0699-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e0699-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e0699-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="e0699-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e0699-106">Required.</span></span> <span data-ttu-id="e0699-107">Nome do procedimento a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="e0699-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="e0699-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e0699-108">Optional.</span></span> <span data-ttu-id="e0699-109">Lista de variáveis ou expressões representando os argumentos que são passados ao procedimento quando ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="e0699-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="e0699-110">Vários argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="e0699-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="e0699-111">Se você incluir `argumentList`, coloque-o entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="e0699-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0699-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0699-112">Remarks</span></span>  
 <span data-ttu-id="e0699-113">Você pode usar o `Call` palavra-chave quando você chama um procedimento.</span><span class="sxs-lookup"><span data-stu-id="e0699-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="e0699-114">Para a maioria das chamadas de procedimento, não é necessário usar a palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e0699-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="e0699-115">Você normalmente usa o `Call` palavra-chave quando a expressão de chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="e0699-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="e0699-116">Usar o `Call` palavra-chave para outros usos não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="e0699-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="e0699-117">Se o procedimento retorna um valor, o `Call` instrução descarta.</span><span class="sxs-lookup"><span data-stu-id="e0699-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0699-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e0699-118">Example</span></span>  
 <span data-ttu-id="e0699-119">O código a seguir mostra dois exemplos em que o `Call` palavra-chave é necessária chamar um procedimento.</span><span class="sxs-lookup"><span data-stu-id="e0699-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="e0699-120">Nos dois exemplos, a expressão de chamada não foi iniciada com um identificador.</span><span class="sxs-lookup"><span data-stu-id="e0699-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e0699-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0699-121">See Also</span></span>  
 [<span data-ttu-id="e0699-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="e0699-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="e0699-123">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="e0699-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e0699-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="e0699-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="e0699-125">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="e0699-125">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
