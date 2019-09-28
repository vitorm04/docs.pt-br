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
ms.openlocfilehash: af0b62d6cfacbcf94f527e049e07e51bf496a6cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392753"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="13c03-102">Instrução Call (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13c03-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="13c03-103">Transfere o controle para um procedimento `Function`, `Sub` ou DLL (biblioteca de vínculo dinâmico).</span><span class="sxs-lookup"><span data-stu-id="13c03-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="13c03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13c03-104">Syntax</span></span>

```vb
[ Call ] procedureName [ (argumentList) ]
```

## <a name="parts"></a><span data-ttu-id="13c03-105">Partes</span><span class="sxs-lookup"><span data-stu-id="13c03-105">Parts</span></span>

|||
|---|---|
|`procedureName`|<span data-ttu-id="13c03-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="13c03-106">Required.</span></span> <span data-ttu-id="13c03-107">Nome do procedimento a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="13c03-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="13c03-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="13c03-108">Optional.</span></span> <span data-ttu-id="13c03-109">Lista de variáveis ou expressões que representam argumentos que são passados para o procedimento quando ele é chamado.</span><span class="sxs-lookup"><span data-stu-id="13c03-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="13c03-110">Vários argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="13c03-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="13c03-111">Se você incluir `argumentList`, deverá colocá-lo entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="13c03-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="13c03-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="13c03-112">Remarks</span></span>

 <span data-ttu-id="13c03-113">Você pode usar a palavra-chave `Call` ao chamar um procedimento.</span><span class="sxs-lookup"><span data-stu-id="13c03-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="13c03-114">Para a maioria das chamadas de procedimento, você não precisa usar essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="13c03-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="13c03-115">Normalmente, você usa a palavra-chave `Call` quando a expressão chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="13c03-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="13c03-116">O uso da palavra-chave `Call` para outros usos não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="13c03-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="13c03-117">Se o procedimento retornar um valor, a instrução `Call` o descartará.</span><span class="sxs-lookup"><span data-stu-id="13c03-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="13c03-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13c03-118">Example</span></span>

 <span data-ttu-id="13c03-119">O código a seguir mostra dois exemplos em que a palavra-chave `Call` é necessária para chamar um procedimento.</span><span class="sxs-lookup"><span data-stu-id="13c03-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="13c03-120">Em ambos os exemplos, a expressão chamada não começa com um identificador.</span><span class="sxs-lookup"><span data-stu-id="13c03-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="13c03-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13c03-121">See also</span></span>

- [<span data-ttu-id="13c03-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="13c03-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="13c03-123">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="13c03-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="13c03-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="13c03-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="13c03-125">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="13c03-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
