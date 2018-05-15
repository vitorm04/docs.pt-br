---
title: Subexpressão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="e5147-102">Subexpressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5147-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="e5147-103">Declara os parâmetros e o código que define uma expressão lambda de sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="e5147-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5147-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5147-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="e5147-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e5147-105">Parts</span></span>  
  
|<span data-ttu-id="e5147-106">Termo</span><span class="sxs-lookup"><span data-stu-id="e5147-106">Term</span></span>|<span data-ttu-id="e5147-107">Definição</span><span class="sxs-lookup"><span data-stu-id="e5147-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="e5147-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e5147-108">Optional.</span></span> <span data-ttu-id="e5147-109">Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento.</span><span class="sxs-lookup"><span data-stu-id="e5147-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="e5147-110">Os parênteses devem estar presentes mesmo quando a lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="e5147-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="e5147-111">Para obter mais informações, consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="e5147-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="e5147-112">Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e5147-112">Required.</span></span> <span data-ttu-id="e5147-113">Uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="e5147-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="e5147-114">Obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e5147-114">Required.</span></span> <span data-ttu-id="e5147-115">Uma lista de instruções.</span><span class="sxs-lookup"><span data-stu-id="e5147-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5147-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5147-116">Remarks</span></span>  
 <span data-ttu-id="e5147-117">Um *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="e5147-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="e5147-118">Você pode usar uma expressão lambda em qualquer lugar que você pode usar um tipo de delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="e5147-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="e5147-119">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [declaração de delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="e5147-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="e5147-120">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="e5147-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="e5147-121">A sintaxe de uma expressão lambda é semelhante a que uma sub-rotina padrão.</span><span class="sxs-lookup"><span data-stu-id="e5147-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="e5147-122">As diferenças são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e5147-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="e5147-123">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="e5147-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="e5147-124">Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="e5147-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="e5147-125">O corpo de uma expressão lambda de linha deve ser uma instrução, não é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="e5147-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="e5147-126">O corpo pode consistir em uma chamada para um procedimento sub, mas não uma chamada para um procedimento function.</span><span class="sxs-lookup"><span data-stu-id="e5147-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="e5147-127">Em uma expressão lambda, ou todos os parâmetros devem especificar tipos de dados ou todos os parâmetros devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="e5147-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="e5147-128">Opcional e `ParamArray` parâmetros não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="e5147-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="e5147-129">Parâmetros genéricos não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="e5147-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5147-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e5147-130">Example</span></span>  
 <span data-ttu-id="e5147-131">A seguir está um exemplo de uma expressão lambda que grava um valor para o console.</span><span class="sxs-lookup"><span data-stu-id="e5147-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="e5147-132">O exemplo mostra dois a sintaxe da expressão lambda de linha e de várias linhas de uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="e5147-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="e5147-133">Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e5147-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e5147-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5147-134">See Also</span></span>  
 [<span data-ttu-id="e5147-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="e5147-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e5147-136">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="e5147-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="e5147-137">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="e5147-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="e5147-138">Instruções</span><span class="sxs-lookup"><span data-stu-id="e5147-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="e5147-139">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="e5147-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
