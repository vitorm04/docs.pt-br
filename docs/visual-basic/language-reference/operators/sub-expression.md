---
title: "Sub expressão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: 6
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 8bbc09b0a8cbd6d9d585097e1e1dab31525116f3
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="c3b51-102">Subexpressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3b51-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="c3b51-103">Declara os parâmetros e o código que define uma expressão lambda de sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="c3b51-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b51-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3b51-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="c3b51-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c3b51-105">Parts</span></span>  
  
|<span data-ttu-id="c3b51-106">Termo</span><span class="sxs-lookup"><span data-stu-id="c3b51-106">Term</span></span>|<span data-ttu-id="c3b51-107">Definição</span><span class="sxs-lookup"><span data-stu-id="c3b51-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="c3b51-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c3b51-108">Optional.</span></span> <span data-ttu-id="c3b51-109">Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento.</span><span class="sxs-lookup"><span data-stu-id="c3b51-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="c3b51-110">Os parênteses devem estar presentes mesmo quando a lista está vazia.</span><span class="sxs-lookup"><span data-stu-id="c3b51-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="c3b51-111">Para obter mais informações, consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="c3b51-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="c3b51-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c3b51-112">Required.</span></span> <span data-ttu-id="c3b51-113">Uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="c3b51-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="c3b51-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c3b51-114">Required.</span></span> <span data-ttu-id="c3b51-115">Uma lista de instruções.</span><span class="sxs-lookup"><span data-stu-id="c3b51-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3b51-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3b51-116">Remarks</span></span>  
 <span data-ttu-id="c3b51-117">A *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="c3b51-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="c3b51-118">Você pode usar uma expressão lambda em qualquer lugar que você pode usar um tipo delegado, exceto como um argumento para `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="c3b51-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="c3b51-119">Para obter mais informações sobre o uso de expressões lambda com delegados e delegados, consulte [instrução delegado](../../../visual-basic/language-reference/statements/delegate-statement.md) e [conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="c3b51-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="c3b51-120">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="c3b51-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="c3b51-121">A sintaxe de uma expressão lambda lembra a de uma sub-rotina padrão.</span><span class="sxs-lookup"><span data-stu-id="c3b51-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="c3b51-122">As diferenças são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="c3b51-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="c3b51-123">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="c3b51-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="c3b51-124">Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c3b51-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="c3b51-125">O corpo de uma expressão lambda de linha deve ser uma instrução, não é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c3b51-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="c3b51-126">O corpo pode consistir de uma chamada para um procedimento sub, mas não uma chamada para um procedimento function.</span><span class="sxs-lookup"><span data-stu-id="c3b51-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="c3b51-127">Em uma expressão lambda, ou todos os parâmetros devem especificar todos os parâmetros ou tipos de dados devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="c3b51-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="c3b51-128">Opcional e `ParamArray` parâmetros não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="c3b51-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="c3b51-129">Parâmetros genéricos não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="c3b51-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b51-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3b51-130">Example</span></span>  
 <span data-ttu-id="c3b51-131">A seguir está um exemplo de uma expressão lambda que grava um valor para o console.</span><span class="sxs-lookup"><span data-stu-id="c3b51-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="c3b51-132">O exemplo mostra os dois a sintaxe da expressão lambda de linha e de várias linhas de uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="c3b51-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="c3b51-133">Para obter mais exemplos, consulte [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c3b51-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="c3b51-134">[!code-vb[VbVbalrLambdas&#15;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c3b51-134">[!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b51-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3b51-135">See Also</span></span>  
 <span data-ttu-id="c3b51-136">[Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c3b51-136">[Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="c3b51-137"> [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c3b51-137"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="c3b51-138"> [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="c3b51-138"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="c3b51-139"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="c3b51-139"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="c3b51-140"> [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="c3b51-140"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

