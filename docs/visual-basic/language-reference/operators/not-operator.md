---
title: Operador Not
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 56cdeb80a217dbce15921eddd6a43d8d1b049376
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401453"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="182a8-102">Operador Not (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="182a8-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="182a8-103">Executa uma negação lógica em uma `Boolean` expressão ou uma negação de bits em uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="182a8-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="182a8-104">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="182a8-105">Partes</span><span class="sxs-lookup"><span data-stu-id="182a8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="182a8-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="182a8-106">Required.</span></span> <span data-ttu-id="182a8-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="182a8-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="182a8-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="182a8-108">Required.</span></span> <span data-ttu-id="182a8-109">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="182a8-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="182a8-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="182a8-110">Remarks</span></span>  
 <span data-ttu-id="182a8-111">Para `Boolean` expressões, a tabela a seguir ilustra como o `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="182a8-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="182a8-112">Se `expression` for </span><span class="sxs-lookup"><span data-stu-id="182a8-112">If `expression` is</span></span>|<span data-ttu-id="182a8-113">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="182a8-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="182a8-114">Para expressões numéricas, o `Not` operador inverte os valores de bit de qualquer expressão numérica e define o bit correspondente de `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="182a8-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="182a8-115">Se o bit in `expression` for</span><span class="sxs-lookup"><span data-stu-id="182a8-115">If bit in `expression` is</span></span>|<span data-ttu-id="182a8-116">O bit em `result` é</span><span class="sxs-lookup"><span data-stu-id="182a8-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="182a8-117">1</span><span class="sxs-lookup"><span data-stu-id="182a8-117">1</span></span>|<span data-ttu-id="182a8-118">0</span><span class="sxs-lookup"><span data-stu-id="182a8-118">0</span></span>|  
|<span data-ttu-id="182a8-119">0</span><span class="sxs-lookup"><span data-stu-id="182a8-119">0</span></span>|<span data-ttu-id="182a8-120">1</span><span class="sxs-lookup"><span data-stu-id="182a8-120">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="182a8-121">Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução</span><span class="sxs-lookup"><span data-stu-id="182a8-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="182a8-122">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="182a8-122">Data Types</span></span>  
 <span data-ttu-id="182a8-123">Para uma negação booliana, o tipo de dados do resultado é `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="182a8-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="182a8-124">Para uma negação de bit que não é possível, o tipo de dados de resultado é o mesmo do `expression` .</span><span class="sxs-lookup"><span data-stu-id="182a8-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="182a8-125">No entanto, se expression for `Decimal` , o resultado será `Long` .</span><span class="sxs-lookup"><span data-stu-id="182a8-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="182a8-126">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="182a8-126">Overloading</span></span>  
 <span data-ttu-id="182a8-127">O `Not` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="182a8-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="182a8-128">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="182a8-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="182a8-129">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="182a8-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="182a8-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="182a8-130">Example</span></span>  
 <span data-ttu-id="182a8-131">O exemplo a seguir usa o `Not` operador para executar a negação lógica em uma `Boolean` expressão.</span><span class="sxs-lookup"><span data-stu-id="182a8-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="182a8-132">O resultado é um `Boolean` valor que representa o inverso do valor da expressão.</span><span class="sxs-lookup"><span data-stu-id="182a8-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="182a8-133">O exemplo anterior produz resultados de `False` e `True` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="182a8-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="182a8-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="182a8-134">Example</span></span>  
 <span data-ttu-id="182a8-135">O exemplo a seguir usa o `Not` operador para executar a negação lógica dos bits individuais de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="182a8-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="182a8-136">O bit no padrão de resultado é definido como o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.</span><span class="sxs-lookup"><span data-stu-id="182a8-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="182a8-137">O exemplo anterior produz resultados de – 11, – 9 e – 7, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="182a8-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182a8-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="182a8-138">See also</span></span>

- [<span data-ttu-id="182a8-139">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="182a8-139">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="182a8-140">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="182a8-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="182a8-141">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="182a8-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="182a8-142">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="182a8-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
