---
title: Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Not
dev_langs:
- VB
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator
- inverse bit values in variables
- bitwise operators, NOT operator
- bitwise comparison
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
caps.latest.revision: 11
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
ms.openlocfilehash: 6ce24e2569325c0aeab5295181673b84d151f741
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="4d07d-102">Operador Not (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d07d-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="4d07d-103">Executa negação lógica em uma `Boolean` expressão ou negação bit a bit em uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4d07d-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d07d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d07d-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="4d07d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4d07d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="4d07d-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4d07d-106">Required.</span></span> <span data-ttu-id="4d07d-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4d07d-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="4d07d-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4d07d-108">Required.</span></span> <span data-ttu-id="4d07d-109">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4d07d-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d07d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d07d-110">Remarks</span></span>  
 <span data-ttu-id="4d07d-111">Para `Boolean` expressões, a tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="4d07d-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="4d07d-112">If `expression` is</span><span class="sxs-lookup"><span data-stu-id="4d07d-112">If `expression` is</span></span>|<span data-ttu-id="4d07d-113">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="4d07d-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="4d07d-114">Para expressões numéricas, o `Not` operador inverte os valores dos bits de qualquer expressão numérica e configura o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4d07d-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="4d07d-115">Se bit no `expression` é</span><span class="sxs-lookup"><span data-stu-id="4d07d-115">If bit in `expression` is</span></span>|<span data-ttu-id="4d07d-116">O bit no `result` é</span><span class="sxs-lookup"><span data-stu-id="4d07d-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="4d07d-117">1</span><span class="sxs-lookup"><span data-stu-id="4d07d-117">1</span></span>|<span data-ttu-id="4d07d-118">0</span><span class="sxs-lookup"><span data-stu-id="4d07d-118">0</span></span>|  
|<span data-ttu-id="4d07d-119">0</span><span class="sxs-lookup"><span data-stu-id="4d07d-119">0</span></span>|<span data-ttu-id="4d07d-120">1</span><span class="sxs-lookup"><span data-stu-id="4d07d-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4d07d-121">Como os operadores lógicos e bit a bit possuem uma precedência menor que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.</span><span class="sxs-lookup"><span data-stu-id="4d07d-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="4d07d-122">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="4d07d-122">Data Types</span></span>  
 <span data-ttu-id="4d07d-123">Para uma negação Boleana, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="4d07d-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="4d07d-124">Para uma negação bit a bit, o tipo de dados do resultado é o mesmo que `expression`.</span><span class="sxs-lookup"><span data-stu-id="4d07d-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="4d07d-125">No entanto, se a expressão for `Decimal`, o resultado é `Long`.</span><span class="sxs-lookup"><span data-stu-id="4d07d-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4d07d-126">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="4d07d-126">Overloading</span></span>  
 <span data-ttu-id="4d07d-127">O `Not` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="4d07d-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="4d07d-128">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="4d07d-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4d07d-129">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4d07d-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d07d-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d07d-130">Example</span></span>  
 <span data-ttu-id="4d07d-131">O exemplo a seguir usa o `Not` operador para realizar negação lógica em uma `Boolean` expressão.</span><span class="sxs-lookup"><span data-stu-id="4d07d-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="4d07d-132">O resultado é um `Boolean` que representa o inverso do valor da expressão.</span><span class="sxs-lookup"><span data-stu-id="4d07d-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 <span data-ttu-id="4d07d-133">[!code-vb[33 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4d07d-133">[!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="4d07d-134">O exemplo anterior produz resultados de `False` e `True`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4d07d-134">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d07d-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d07d-135">Example</span></span>  
 <span data-ttu-id="4d07d-136">O exemplo a seguir usa o `Not` operador para realizar negação lógica dos bits individuais de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4d07d-136">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="4d07d-137">O bit no padrão resultante é definido como o inverso do bit correspondente no padrão de operando, incluindo o bit de sinal.</span><span class="sxs-lookup"><span data-stu-id="4d07d-137">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 <span data-ttu-id="4d07d-138">[!code-vb[VbVbalrOperators&#34;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4d07d-138">[!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="4d07d-139">O exemplo anterior produz resultados –&11;, –9 e -7, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="4d07d-139">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d07d-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d07d-140">See Also</span></span>  
 <span data-ttu-id="4d07d-141">[Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4d07d-141">[Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="4d07d-142"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="4d07d-142"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="4d07d-143"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="4d07d-143"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="4d07d-144"> [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="4d07d-144"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>

