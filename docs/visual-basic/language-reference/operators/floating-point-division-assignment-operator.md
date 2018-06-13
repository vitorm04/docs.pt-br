---
title: Operador /= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604088"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="87ca9-102">Operador /= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87ca9-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="87ca9-103">Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado de ponto flutuante para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="87ca9-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ca9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87ca9-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="87ca9-105">Partes</span><span class="sxs-lookup"><span data-stu-id="87ca9-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="87ca9-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="87ca9-106">Required.</span></span> <span data-ttu-id="87ca9-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="87ca9-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="87ca9-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="87ca9-108">Required.</span></span> <span data-ttu-id="87ca9-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="87ca9-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ca9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="87ca9-110">Remarks</span></span>  
 <span data-ttu-id="87ca9-111">O elemento à esquerda do `/=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="87ca9-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="87ca9-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="87ca9-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="87ca9-113">O `/=` operador primeiro divide o valor da variável ou propriedade (no lado esquerdo do operador) pelo valor da expressão (no lado direito do operador).</span><span class="sxs-lookup"><span data-stu-id="87ca9-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="87ca9-114">O operador, em seguida, atribui o resultado dessa operação de ponto flutuante para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="87ca9-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="87ca9-115">Essa instrução atribui um `Double` valor à variável ou propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="87ca9-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="87ca9-116">Se `Option Strict` é `On`, `variableorproperty` deve ser um `Double`.</span><span class="sxs-lookup"><span data-stu-id="87ca9-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="87ca9-117">Se `Option Strict` é `Off`, Visual Basic executará uma conversão implícita e atribui o valor resultante para `variableorproperty`, com um possível erro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="87ca9-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="87ca9-118">Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="87ca9-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="87ca9-119">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="87ca9-119">Overloading</span></span>  
 <span data-ttu-id="87ca9-120">O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="87ca9-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="87ca9-121">Sobrecarga de `/` operador afeta o comportamento do `/=` operador.</span><span class="sxs-lookup"><span data-stu-id="87ca9-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="87ca9-122">Se seu código usa `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique-se de compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="87ca9-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="87ca9-123">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="87ca9-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ca9-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87ca9-124">Example</span></span>  
 <span data-ttu-id="87ca9-125">O exemplo a seguir usa o `/=` operador para dividir uma `Integer` variável por um segundo e atribuir a quociente à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="87ca9-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="87ca9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87ca9-126">See Also</span></span>  
 [<span data-ttu-id="87ca9-127">/ Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87ca9-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="87ca9-128">\\= Operador</span><span class="sxs-lookup"><span data-stu-id="87ca9-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="87ca9-129">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="87ca9-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="87ca9-130">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="87ca9-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="87ca9-131">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87ca9-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="87ca9-132">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="87ca9-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="87ca9-133">Instruções</span><span class="sxs-lookup"><span data-stu-id="87ca9-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
