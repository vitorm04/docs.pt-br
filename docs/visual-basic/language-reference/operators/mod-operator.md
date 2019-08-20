---
title: Operador Mod (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: c801facd95d93652414409549bb5ff2fa633748b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611527"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="ae9f3-102">Operador Mod (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae9f3-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="ae9f3-103">Divide dois números e retorna apenas o resto.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae9f3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae9f3-104">Syntax</span></span>

```vb
result = number1 Mod number2
```
  
## <a name="parts"></a><span data-ttu-id="ae9f3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ae9f3-105">Parts</span></span>  
 <span data-ttu-id="ae9f3-106">`result` Necessário.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-106">`result` Required.</span></span> <span data-ttu-id="ae9f3-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-107">Any numeric variable or property.</span></span>

 <span data-ttu-id="ae9f3-108">`number1` Necessário.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-108">`number1` Required.</span></span> <span data-ttu-id="ae9f3-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-109">Any numeric expression.</span></span>

 <span data-ttu-id="ae9f3-110">`number2` Necessário.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-110">`number2` Required.</span></span> <span data-ttu-id="ae9f3-111">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="ae9f3-112">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="ae9f3-112">Supported types</span></span>
 <span data-ttu-id="ae9f3-113">Todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-113">All numeric types.</span></span> <span data-ttu-id="ae9f3-114">Isso inclui os tipos de ponto flutuante e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="ae9f3-115">Resultado</span><span class="sxs-lookup"><span data-stu-id="ae9f3-115">Result</span></span>

<span data-ttu-id="ae9f3-116">O resultado é o resto após `number1` ser dividido por `number2`.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="ae9f3-117">Por exemplo, a expressão `14 Mod 4` é avaliada como 2.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="ae9f3-118">Há uma diferença entre *resto* e *módulo* em matemática, com resultados diferentes para números negativos.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="ae9f3-119">O `Mod` operador em Visual Basic, o operador `op_Modulus` de .NET Framework e a instrução de Il de [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) subjacente All executam uma operação pendente.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="ae9f3-120">O resultado de uma `Mod` operação retém o sinal do dividendo, `number1`e, portanto, pode ser positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="ae9f3-121">O resultado está sempre no intervalo (-`number2`, `number2`), exclusivo.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="ae9f3-122">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ae9f3-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="ae9f3-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae9f3-123">Remarks</span></span>
 <span data-ttu-id="ae9f3-124">`number1` Se ou `number2` for um valor de ponto flutuante, o restante de ponto flutuante da divisão será retornado.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="ae9f3-125">O tipo de dados do resultado é o menor tipo de dados que pode conter todos os valores possíveis que resultam da divisão com os `number1` tipos `number2`de dados de e.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

 <span data-ttu-id="ae9f3-126">Se `number1` ou`number2` for avaliado como [Nothing](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

 <span data-ttu-id="ae9f3-127">Os operadores relacionados incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ae9f3-127">Related operators include the following:</span></span>

- <span data-ttu-id="ae9f3-128">O [operador \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente inteiro de uma divisão.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="ae9f3-129">Por exemplo, a expressão `14 \ 4` é avaliada como 3.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="ae9f3-130">O [operador/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, incluindo o resto, como um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="ae9f3-131">Por exemplo, a expressão `14 / 4` é avaliada como 3,5.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="ae9f3-132">Tentativa de divisão por zero</span><span class="sxs-lookup"><span data-stu-id="ae9f3-132">Attempted division by zero</span></span>
 <span data-ttu-id="ae9f3-133">Se `number2` for avaliada como zero, o comportamento `Mod` do operador dependerá do tipo de dados dos operandos:</span><span class="sxs-lookup"><span data-stu-id="ae9f3-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>
 - <span data-ttu-id="ae9f3-134">Uma divisão integral gera uma <xref:System.DivideByZeroException> exceção se `number2` não puder ser determinada em tempo de compilação e gerará um erro `BC30542    Division by zero occurred while evaluating this expression` em tempo `number2` de compilação se for avaliado como zero em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542    Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
 - <span data-ttu-id="ae9f3-135">Uma divisão de ponto flutuante retorna <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="ae9f3-136">Fórmula equivalente</span><span class="sxs-lookup"><span data-stu-id="ae9f3-136">Equivalent formula</span></span>
 <span data-ttu-id="ae9f3-137">A expressão `a Mod b` é equivalente a qualquer uma das seguintes fórmulas:</span><span class="sxs-lookup"><span data-stu-id="ae9f3-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

 `a - (b * (a \ b))`

 `a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="ae9f3-138">Irprecisão de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="ae9f3-138">Floating-point imprecision</span></span>
 <span data-ttu-id="ae9f3-139">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação decimal precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="ae9f3-140">Isso pode levar a resultados inesperados de determinadas operações, como comparação de valor `Mod` e o operador.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="ae9f3-141">Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae9f3-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="ae9f3-142">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="ae9f3-142">Overloading</span></span>
 <span data-ttu-id="ae9f3-143">O `Mod` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="ae9f3-144">Se o seu código `Mod` se aplicar a uma instância de uma classe ou estrutura que inclua tal sobrecarga, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ae9f3-145">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ae9f3-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="ae9f3-146">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae9f3-146">Example</span></span>
 <span data-ttu-id="ae9f3-147">O exemplo a seguir usa `Mod` o operador para dividir dois números e retornar apenas o resto.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="ae9f3-148">Se um dos números for um número de ponto flutuante, o resultado será um número de ponto flutuante que representa o restante.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="ae9f3-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ae9f3-149">Example</span></span>
 <span data-ttu-id="ae9f3-150">O exemplo a seguir demonstra a possível imprecisão de operandos de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="ae9f3-151">Na primeira instrução, os operandos são `Double`e 0,2 é uma fração binária infinitamente repetida com um valor armazenado de 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="ae9f3-152">Na segunda instrução, o caractere `D` de tipo literal força ambos os operandos para `Decimal`e 0,2 tem uma representação precisa.</span><span class="sxs-lookup"><span data-stu-id="ae9f3-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="ae9f3-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae9f3-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="ae9f3-154">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="ae9f3-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ae9f3-155">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae9f3-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ae9f3-156">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="ae9f3-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ae9f3-157">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="ae9f3-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="ae9f3-158">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae9f3-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="ae9f3-159">Operador \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae9f3-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
