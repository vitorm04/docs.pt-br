---
title: Operador Not (Visual Basic)
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
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824191"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="6b516-102">Operador Not (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b516-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="6b516-103">Realiza negação lógica em uma `Boolean` expressão ou negação bit a bit em uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="6b516-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b516-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b516-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="6b516-105">Partes</span><span class="sxs-lookup"><span data-stu-id="6b516-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="6b516-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6b516-106">Required.</span></span> <span data-ttu-id="6b516-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="6b516-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="6b516-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6b516-108">Required.</span></span> <span data-ttu-id="6b516-109">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="6b516-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b516-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b516-110">Remarks</span></span>  
 <span data-ttu-id="6b516-111">Para `Boolean` expressões, a tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="6b516-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="6b516-112">Se `expression` é</span><span class="sxs-lookup"><span data-stu-id="6b516-112">If `expression` is</span></span>|<span data-ttu-id="6b516-113">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="6b516-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="6b516-114">Para expressões numéricas, o `Not` operador inverte os valores de bits de qualquer expressão numérica e define o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="6b516-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="6b516-115">Se bit no `expression` é</span><span class="sxs-lookup"><span data-stu-id="6b516-115">If bit in `expression` is</span></span>|<span data-ttu-id="6b516-116">O bit no `result` é</span><span class="sxs-lookup"><span data-stu-id="6b516-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="6b516-117">1</span><span class="sxs-lookup"><span data-stu-id="6b516-117">1</span></span>|<span data-ttu-id="6b516-118">0</span><span class="sxs-lookup"><span data-stu-id="6b516-118">0</span></span>|  
|<span data-ttu-id="6b516-119">0</span><span class="sxs-lookup"><span data-stu-id="6b516-119">0</span></span>|<span data-ttu-id="6b516-120">1</span><span class="sxs-lookup"><span data-stu-id="6b516-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="6b516-121">Como os operadores lógicos e bit a bit tem uma precedência inferior outros operadores aritméticos e relacionais, todas as operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.</span><span class="sxs-lookup"><span data-stu-id="6b516-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="6b516-122">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="6b516-122">Data Types</span></span>  
 <span data-ttu-id="6b516-123">Para Boleana, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6b516-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="6b516-124">Para uma negação bit a bit, o tipo de dados do resultado é o mesmo da `expression`.</span><span class="sxs-lookup"><span data-stu-id="6b516-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="6b516-125">No entanto, se a expressão é `Decimal`, o resultado é `Long`.</span><span class="sxs-lookup"><span data-stu-id="6b516-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="6b516-126">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="6b516-126">Overloading</span></span>  
 <span data-ttu-id="6b516-127">O `Not` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando o operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="6b516-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="6b516-128">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="6b516-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="6b516-129">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="6b516-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b516-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b516-130">Example</span></span>  
 <span data-ttu-id="6b516-131">O exemplo a seguir usa o `Not` operador para realizar a negação lógica em uma `Boolean` expressão.</span><span class="sxs-lookup"><span data-stu-id="6b516-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="6b516-132">O resultado é um `Boolean` que representa o inverso do valor da expressão.</span><span class="sxs-lookup"><span data-stu-id="6b516-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="6b516-133">O exemplo anterior produz resultados `False` e `True`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6b516-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b516-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b516-134">Example</span></span>  
 <span data-ttu-id="6b516-135">O exemplo a seguir usa o `Not` operador para realizar a negação lógica dos bits individuais de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="6b516-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="6b516-136">O bit no padrão de resultado é definido como o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.</span><span class="sxs-lookup"><span data-stu-id="6b516-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="6b516-137">O exemplo anterior produz resultados -11, -9 e -7, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6b516-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b516-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b516-138">See also</span></span>

- [<span data-ttu-id="6b516-139">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b516-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="6b516-140">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b516-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="6b516-141">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="6b516-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="6b516-142">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b516-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
