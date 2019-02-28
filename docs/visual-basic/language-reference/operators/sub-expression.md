---
title: Subexpressão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 5e8c66f4f2b21a890b8c61e6fc642ce276df6f60
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966717"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="8c9d7-102">Subexpressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c9d7-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="8c9d7-103">Declara os parâmetros e o código que define uma expressão lambda de sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c9d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c9d7-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="8c9d7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8c9d7-105">Parts</span></span>  
  
|<span data-ttu-id="8c9d7-106">Termo</span><span class="sxs-lookup"><span data-stu-id="8c9d7-106">Term</span></span>|<span data-ttu-id="8c9d7-107">Definição</span><span class="sxs-lookup"><span data-stu-id="8c9d7-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="8c9d7-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-108">Optional.</span></span> <span data-ttu-id="8c9d7-109">Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="8c9d7-110">Os parênteses devem estar presentes mesmo quando a lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="8c9d7-111">Para obter mais informações, consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="8c9d7-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="8c9d7-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-112">Required.</span></span> <span data-ttu-id="8c9d7-113">Uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="8c9d7-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-114">Required.</span></span> <span data-ttu-id="8c9d7-115">Uma lista de instruções.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c9d7-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c9d7-116">Remarks</span></span>  
 <span data-ttu-id="8c9d7-117">Um *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="8c9d7-118">Você pode usar uma expressão lambda em qualquer lugar que você pode usar um tipo de delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="8c9d7-119">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [declaração de delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="8c9d7-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="8c9d7-120">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="8c9d7-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="8c9d7-121">A sintaxe de uma expressão lambda lembra a de uma sub-rotina padrão.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="8c9d7-122">As diferenças são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8c9d7-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="8c9d7-123">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="8c9d7-124">Uma expressão lambda não pode ter um modificador, tais como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="8c9d7-125">O corpo de uma expressão lambda de linha única deve ser uma instrução, não é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="8c9d7-126">O corpo pode consistir de uma chamada para um procedimento sub, mas não uma chamada para um procedimento function.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="8c9d7-127">Em uma expressão lambda, ou todos os parâmetros devem ter especificado todos os parâmetros ou tipos de dados devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="8c9d7-128">Opcional e `ParamArray` parâmetros não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="8c9d7-129">Parâmetros genéricos não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c9d7-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8c9d7-130">Example</span></span>  
 <span data-ttu-id="8c9d7-131">A seguir está um exemplo de uma expressão lambda que grava um valor no console.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="8c9d7-132">O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas de uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="8c9d7-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="8c9d7-133">Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8c9d7-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="8c9d7-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c9d7-134">See also</span></span>
- [<span data-ttu-id="8c9d7-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="8c9d7-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="8c9d7-136">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="8c9d7-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="8c9d7-137">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="8c9d7-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="8c9d7-138">Instruções</span><span class="sxs-lookup"><span data-stu-id="8c9d7-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="8c9d7-139">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="8c9d7-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
