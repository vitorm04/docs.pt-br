---
title: Operador Mod (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="4f160-102">Operador Mod (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f160-102">Mod Operator (Visual Basic)</span></span>
<span data-ttu-id="4f160-103">Divide dois números e retorna somente o resto.</span><span class="sxs-lookup"><span data-stu-id="4f160-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f160-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f160-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="4f160-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4f160-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="4f160-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f160-106">Required.</span></span> <span data-ttu-id="4f160-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4f160-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="4f160-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f160-108">Required.</span></span> <span data-ttu-id="4f160-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4f160-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="4f160-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="4f160-110">Supported Types</span></span>  
 <span data-ttu-id="4f160-111">Todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="4f160-111">All numeric types.</span></span> <span data-ttu-id="4f160-112">Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4f160-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="4f160-113">Resultado</span><span class="sxs-lookup"><span data-stu-id="4f160-113">Result</span></span>  
 <span data-ttu-id="4f160-114">O resultado é o resto após `number1` é dividida por `number2`.</span><span class="sxs-lookup"><span data-stu-id="4f160-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="4f160-115">Por exemplo, a expressão `14 Mod 4` for avaliada como 2.</span><span class="sxs-lookup"><span data-stu-id="4f160-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f160-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f160-116">Remarks</span></span>  
 <span data-ttu-id="4f160-117">Se qualquer um dos `number1` ou `number2` é um valor de ponto flutuante, o restante da divisão de ponto flutuante é retornado.</span><span class="sxs-lookup"><span data-stu-id="4f160-117">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="4f160-118">O tipo de dados do resultado é o menor tipo de dados que pode conter todos os possíveis valores resultantes da divisão com os tipos de dados de `number1` e `number2`.</span><span class="sxs-lookup"><span data-stu-id="4f160-118">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="4f160-119">Se `number1` ou `number2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="4f160-119">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="4f160-120">Relacionadas operadores incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4f160-120">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="4f160-121">O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro de uma divisão.</span><span class="sxs-lookup"><span data-stu-id="4f160-121">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="4f160-122">Por exemplo, a expressão `14 \ 4` é avaliada como 3.</span><span class="sxs-lookup"><span data-stu-id="4f160-122">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="4f160-123">O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, incluindo o restante, como um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="4f160-123">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="4f160-124">Por exemplo, a expressão `14 / 4` avaliará como 3.5.</span><span class="sxs-lookup"><span data-stu-id="4f160-124">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="4f160-125">Tentativa de divisão por Zero</span><span class="sxs-lookup"><span data-stu-id="4f160-125">Attempted Division by Zero</span></span>  
 <span data-ttu-id="4f160-126">Se `number2` for avaliada como zero, o comportamento do `Mod` operador depende do tipo de dados dos operandos.</span><span class="sxs-lookup"><span data-stu-id="4f160-126">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="4f160-127">Uma divisão integral gera um <xref:System.DivideByZeroException> exceção.</span><span class="sxs-lookup"><span data-stu-id="4f160-127">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="4f160-128">Retorna uma divisão de ponto flutuante <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="4f160-128">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="4f160-129">Fórmula equivalente</span><span class="sxs-lookup"><span data-stu-id="4f160-129">Equivalent Formula</span></span>  
 <span data-ttu-id="4f160-130">A expressão `a Mod b` é equivalente a uma das fórmulas a seguir:</span><span class="sxs-lookup"><span data-stu-id="4f160-130">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="4f160-131">Ponto flutuante imprecisão</span><span class="sxs-lookup"><span data-stu-id="4f160-131">Floating-Point Imprecision</span></span>  
 <span data-ttu-id="4f160-132">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="4f160-132">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="4f160-133">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="4f160-133">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="4f160-134">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f160-134">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4f160-135">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="4f160-135">Overloading</span></span>  
 <span data-ttu-id="4f160-136">O `Mod` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="4f160-136">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="4f160-137">Se seu código se aplica `Mod` para uma instância de uma classe ou estrutura que inclua tal uma sobrecarga, certifique-se que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="4f160-137">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4f160-138">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4f160-138">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f160-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f160-139">Example</span></span>  
 <span data-ttu-id="4f160-140">O exemplo a seguir usa o `Mod` operador para dividir dois números e retornar somente o resto.</span><span class="sxs-lookup"><span data-stu-id="4f160-140">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="4f160-141">Se o número for um número de ponto flutuante, o resultado é um número de ponto flutuante que representa o restante.</span><span class="sxs-lookup"><span data-stu-id="4f160-141">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4f160-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f160-142">Example</span></span>  
 <span data-ttu-id="4f160-143">O exemplo a seguir demonstra a imprecisão potencial de operandos de ponto flutuantes.</span><span class="sxs-lookup"><span data-stu-id="4f160-143">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="4f160-144">Na primeira instrução, os operandos são `Double`, e 0.2 é uma fração binária infinitamente de repetição com um valor armazenado de 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="4f160-144">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="4f160-145">Na segunda instrução, o literal de caractere de tipo `D` força ambos os operandos para `Decimal`, e 0.2 tem uma representação exata.</span><span class="sxs-lookup"><span data-stu-id="4f160-145">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4f160-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f160-146">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="4f160-147">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="4f160-147">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="4f160-148">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f160-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="4f160-149">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="4f160-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="4f160-150">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4f160-150">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="4f160-151">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f160-151">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="4f160-152">\ Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f160-152">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
