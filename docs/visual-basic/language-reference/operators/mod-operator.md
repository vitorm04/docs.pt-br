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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 456c19fc8e28517a0662b58e338028e1c75cd8c8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360525"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="30e84-102">Operador Mod (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30e84-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="30e84-103">Divide dois números e retorna apenas o resto.</span><span class="sxs-lookup"><span data-stu-id="30e84-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30e84-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="30e84-105">Partes</span><span class="sxs-lookup"><span data-stu-id="30e84-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="30e84-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="30e84-106">Required.</span></span> <span data-ttu-id="30e84-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="30e84-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="30e84-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="30e84-108">Required.</span></span> <span data-ttu-id="30e84-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="30e84-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="30e84-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="30e84-110">Supported types</span></span>  
 <span data-ttu-id="30e84-111">Todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="30e84-111">All numeric types.</span></span> <span data-ttu-id="30e84-112">Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="30e84-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="30e84-113">Resultado</span><span class="sxs-lookup"><span data-stu-id="30e84-113">Result</span></span>

<span data-ttu-id="30e84-114">O resultado é o resto após `number1` é dividida por `number2`.</span><span class="sxs-lookup"><span data-stu-id="30e84-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="30e84-115">Por exemplo, a expressão `14 Mod 4` será avaliada como 2.</span><span class="sxs-lookup"><span data-stu-id="30e84-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="30e84-116">Há uma diferença entre *restante* e *modulus* em matemática, com resultados diferentes para números negativos.</span><span class="sxs-lookup"><span data-stu-id="30e84-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="30e84-117">O `Mod` operador no Visual Basic, o .NET Framework `op_Modulus` operador e subjacente [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) todos executam uma operação do restante de instrução de IL.</span><span class="sxs-lookup"><span data-stu-id="30e84-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="30e84-118">O resultado de uma `Mod` operação retém o sinal do dividendo, `number1`, e, portanto, pode ser positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="30e84-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="30e84-119">O resultado é sempre no intervalo (-`number2`, `number2`), exclusivo.</span><span class="sxs-lookup"><span data-stu-id="30e84-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="30e84-120">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="30e84-120">For example:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="30e84-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="30e84-121">Remarks</span></span>  
 <span data-ttu-id="30e84-122">Se qualquer um dos `number1` ou `number2` é um valor de ponto flutuante, o restante da divisão de ponto flutuante é retornado.</span><span class="sxs-lookup"><span data-stu-id="30e84-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="30e84-123">O tipo de dados do resultado é o menor tipo de dados que pode conter todos os possíveis valores resultantes da divisão com tipos de dados do `number1` e `number2`.</span><span class="sxs-lookup"><span data-stu-id="30e84-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="30e84-124">Se `number1` ou `number2` é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="30e84-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="30e84-125">Operadores relacionados incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="30e84-125">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="30e84-126">O [\ operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) retorna o quociente de inteiro de uma divisão.</span><span class="sxs-lookup"><span data-stu-id="30e84-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="30e84-127">Por exemplo, a expressão `14 \ 4` é avaliada como 3.</span><span class="sxs-lookup"><span data-stu-id="30e84-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="30e84-128">O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) retorna o quociente completo, incluindo o restante, como um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="30e84-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="30e84-129">Por exemplo, a expressão `14 / 4` avaliará como 3.5.</span><span class="sxs-lookup"><span data-stu-id="30e84-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="30e84-130">Tentativa de divisão por zero</span><span class="sxs-lookup"><span data-stu-id="30e84-130">Attempted division by zero</span></span>  
 <span data-ttu-id="30e84-131">Se `number2` for avaliada como zero, o comportamento do `Mod` operador depende do tipo de dados dos operandos.</span><span class="sxs-lookup"><span data-stu-id="30e84-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="30e84-132">Uma divisão integral gera um <xref:System.DivideByZeroException> exceção.</span><span class="sxs-lookup"><span data-stu-id="30e84-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="30e84-133">Retorna uma divisão de ponto flutuante <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="30e84-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="30e84-134">Fórmula equivalente</span><span class="sxs-lookup"><span data-stu-id="30e84-134">Equivalent formula</span></span>  
 <span data-ttu-id="30e84-135">A expressão `a Mod b` é equivalente a uma das fórmulas a seguir:</span><span class="sxs-lookup"><span data-stu-id="30e84-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="30e84-136">Ponto flutuante imprecisão</span><span class="sxs-lookup"><span data-stu-id="30e84-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="30e84-137">Quando você trabalha com números de ponto flutuante, lembre-se de que eles nem sempre têm uma representação decimal precisa na memória.</span><span class="sxs-lookup"><span data-stu-id="30e84-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="30e84-138">Isso pode levar a resultados inesperados em certas operações, como comparação de valor e o `Mod` operador.</span><span class="sxs-lookup"><span data-stu-id="30e84-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="30e84-139">Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="30e84-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="30e84-140">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="30e84-140">Overloading</span></span>  
 <span data-ttu-id="30e84-141">O `Mod` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="30e84-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="30e84-142">Se seu código se aplica `Mod` para uma instância de uma classe ou estrutura que inclua tal uma sobrecarga, certifique-se que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="30e84-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="30e84-143">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="30e84-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30e84-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30e84-144">Example</span></span>  
 <span data-ttu-id="30e84-145">O exemplo a seguir usa o `Mod` operador dividir dois números e retornar somente o resto.</span><span class="sxs-lookup"><span data-stu-id="30e84-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="30e84-146">Se o número for um número de ponto flutuante, o resultado é um número de ponto flutuante que representa o restante.</span><span class="sxs-lookup"><span data-stu-id="30e84-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="30e84-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30e84-147">Example</span></span>  
 <span data-ttu-id="30e84-148">O exemplo a seguir demonstra a imprecisão potencial de operandos de ponto flutuantes.</span><span class="sxs-lookup"><span data-stu-id="30e84-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="30e84-149">Na primeira instrução, os operandos forem `Double`, e 0.2 é uma fração binária infinitamente de repetição com um valor armazenado de 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="30e84-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="30e84-150">Na segunda instrução, o literal de caractere de tipo `D` força a ambos os operandos para `Decimal`, e 0.2 tem uma representação exata.</span><span class="sxs-lookup"><span data-stu-id="30e84-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="30e84-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30e84-151">See also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="30e84-152">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="30e84-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="30e84-153">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30e84-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="30e84-154">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="30e84-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="30e84-155">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="30e84-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="30e84-156">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30e84-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="30e84-157">\ Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30e84-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
