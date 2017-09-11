---
title: "Instrução Call (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Call
dev_langs:
- VB
helpviewer_keywords:
- procedures, Call statement
- Call statement
- procedures, calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
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
ms.openlocfilehash: 9dfd22d5475a668eb619a17fddbf43ff6757bfa2
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="b32d0-102">Instrução Call (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b32d0-102">Call Statement (Visual Basic)</span></span>
<span data-ttu-id="b32d0-103">Transfere o controle para uma `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico (DLL).</span><span class="sxs-lookup"><span data-stu-id="b32d0-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b32d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b32d0-104">Syntax</span></span>  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b32d0-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b32d0-105">Parts</span></span>  
 `procedureName`  
 <span data-ttu-id="b32d0-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b32d0-106">Required.</span></span> <span data-ttu-id="b32d0-107">Nome do procedimento a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="b32d0-107">Name of the procedure to call.</span></span>  
  
 `argumentList`  
 <span data-ttu-id="b32d0-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b32d0-108">Optional.</span></span> <span data-ttu-id="b32d0-109">Lista de variáveis ou expressões que representa os argumentos que são passados para o procedimento quando é chamado.</span><span class="sxs-lookup"><span data-stu-id="b32d0-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="b32d0-110">Vários argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="b32d0-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="b32d0-111">Se você incluir `argumentList`, você deve colocá-la entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="b32d0-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b32d0-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b32d0-112">Remarks</span></span>  
 <span data-ttu-id="b32d0-113">Você pode usar o `Call` palavra-chave quando você chama um procedimento.</span><span class="sxs-lookup"><span data-stu-id="b32d0-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="b32d0-114">Para a maioria das chamadas de procedimento, não é necessário usar essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b32d0-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>  
  
 <span data-ttu-id="b32d0-115">Você normalmente usa o `Call` palavra-chave quando a expressão de chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="b32d0-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="b32d0-116">Usar o `Call` palavra-chave para outros usos não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="b32d0-116">Use of the `Call` keyword for other uses isn’t recommended.</span></span>  
  
 <span data-ttu-id="b32d0-117">Se o procedimento retorna um valor, o `Call` instrução descarta.</span><span class="sxs-lookup"><span data-stu-id="b32d0-117">If the procedure returns a value, the `Call` statement discards it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b32d0-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b32d0-118">Example</span></span>  
 <span data-ttu-id="b32d0-119">O código a seguir mostra dois exemplos onde a `Call` palavra-chave é necessária chamar um procedimento.</span><span class="sxs-lookup"><span data-stu-id="b32d0-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="b32d0-120">Nos dois exemplos, a expressão de chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="b32d0-120">In both examples, the called expression doesn't start with an identifier.</span></span>  
  
 <span data-ttu-id="b32d0-121">[!code-vb[VbVbalrStatements&#97;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b32d0-121">[!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/call-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b32d0-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b32d0-122">See Also</span></span>  
 <span data-ttu-id="b32d0-123">[Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b32d0-123">[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="b32d0-124"> [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b32d0-124"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="b32d0-125"> [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b32d0-125"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="b32d0-126"> [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="b32d0-126"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)</span></span>

