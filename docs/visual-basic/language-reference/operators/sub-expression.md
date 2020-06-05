---
title: Subexpressão
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: f862730220d0595faecaa915b1eaad2a3cdc0053
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406308"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="af5ce-102">Subexpressão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af5ce-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="af5ce-103">Declara os parâmetros e o código que definem uma expressão lambda de sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="af5ce-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af5ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af5ce-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="af5ce-105">Partes</span><span class="sxs-lookup"><span data-stu-id="af5ce-105">Parts</span></span>  
  
|<span data-ttu-id="af5ce-106">Termo</span><span class="sxs-lookup"><span data-stu-id="af5ce-106">Term</span></span>|<span data-ttu-id="af5ce-107">Definição</span><span class="sxs-lookup"><span data-stu-id="af5ce-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="af5ce-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="af5ce-108">Optional.</span></span> <span data-ttu-id="af5ce-109">Uma lista de nomes de variáveis locais que representam os parâmetros do procedimento.</span><span class="sxs-lookup"><span data-stu-id="af5ce-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="af5ce-110">Os parênteses devem estar presentes mesmo quando a lista estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="af5ce-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="af5ce-111">Para obter mais informações, consulte [lista de parâmetros](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="af5ce-111">For more information, see [Parameter List](../statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="af5ce-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="af5ce-112">Required.</span></span> <span data-ttu-id="af5ce-113">Uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="af5ce-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="af5ce-114">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="af5ce-114">Required.</span></span> <span data-ttu-id="af5ce-115">Uma lista de instruções.</span><span class="sxs-lookup"><span data-stu-id="af5ce-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af5ce-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="af5ce-116">Remarks</span></span>  
 <span data-ttu-id="af5ce-117">Uma *expressão lambda* é uma sub-rotina que não tem um nome e que executa uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="af5ce-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="af5ce-118">Você pode usar uma expressão lambda em qualquer lugar que possa usar um tipo delegado, exceto como um argumento para `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="af5ce-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="af5ce-119">Para obter mais informações sobre delegados e o uso de expressões lambda com delegados, consulte [instrução delegate](../statements/delegate-statement.md) e [conversão de delegado reduzida](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="af5ce-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="af5ce-120">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="af5ce-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="af5ce-121">A sintaxe de uma expressão lambda é semelhante à de uma sub-rotina padrão.</span><span class="sxs-lookup"><span data-stu-id="af5ce-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="af5ce-122">As diferenças são:</span><span class="sxs-lookup"><span data-stu-id="af5ce-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="af5ce-123">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="af5ce-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="af5ce-124">Uma expressão lambda não pode ter um modificador, como `Overloads` ou `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="af5ce-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="af5ce-125">O corpo de uma expressão lambda de linha única deve ser uma instrução, não uma expressão.</span><span class="sxs-lookup"><span data-stu-id="af5ce-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="af5ce-126">O corpo pode consistir em uma chamada para um procedimento Sub, mas não uma chamada para um procedimento Function.</span><span class="sxs-lookup"><span data-stu-id="af5ce-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="af5ce-127">Em uma expressão lambda, todos os parâmetros devem ter tipos de dados especificados ou todos os parâmetros devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="af5ce-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="af5ce-128">Parâmetros opcionais e `ParamArray` não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="af5ce-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="af5ce-129">Parâmetros genéricos não são permitidos em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="af5ce-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af5ce-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af5ce-130">Example</span></span>  
 <span data-ttu-id="af5ce-131">Veja a seguir um exemplo de uma expressão lambda que grava um valor no console.</span><span class="sxs-lookup"><span data-stu-id="af5ce-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="af5ce-132">O exemplo mostra a sintaxe de expressão lambda de linha única e de várias linhas para uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="af5ce-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="af5ce-133">Para obter mais exemplos, consulte [expressões lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="af5ce-133">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="af5ce-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="af5ce-134">See also</span></span>

- [<span data-ttu-id="af5ce-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="af5ce-135">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="af5ce-136">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="af5ce-136">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="af5ce-137">Operadores e expressões</span><span class="sxs-lookup"><span data-stu-id="af5ce-137">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="af5ce-138">Instruções</span><span class="sxs-lookup"><span data-stu-id="af5ce-138">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="af5ce-139">Conversão de delegado reduzida</span><span class="sxs-lookup"><span data-stu-id="af5ce-139">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
