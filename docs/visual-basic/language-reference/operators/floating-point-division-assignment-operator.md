---
title: Operador / = (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
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
ms.openlocfilehash: e877e98104b5c9fd679485b50a88943fac80a696
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0d302-102">Operador /= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d302-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="0d302-103">Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado de ponto flutuante para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d302-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d302-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d302-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0d302-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0d302-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="0d302-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0d302-106">Required.</span></span> <span data-ttu-id="0d302-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d302-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="0d302-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0d302-108">Required.</span></span> <span data-ttu-id="0d302-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="0d302-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d302-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d302-110">Remarks</span></span>  
 <span data-ttu-id="0d302-111">O elemento à esquerda do `/=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="0d302-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0d302-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0d302-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0d302-113">O `/=` operador primeiro divide o valor da variável ou propriedade (no lado esquerdo do operador), o valor da expressão (no lado direito do operador).</span><span class="sxs-lookup"><span data-stu-id="0d302-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="0d302-114">O operador atribui o resultado da operação de ponto flutuante para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0d302-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="0d302-115">Essa instrução atribui um `Double` valor à variável ou propriedade no lado esquerdo.</span><span class="sxs-lookup"><span data-stu-id="0d302-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="0d302-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span><span class="sxs-lookup"><span data-stu-id="0d302-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="0d302-117">Se `Option Strict` é `Off`, Visual Basic executará uma conversão implícita e atribui o valor resultante para `variableorproperty`, com um possível erro em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0d302-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="0d302-118">Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0d302-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0d302-119">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="0d302-119">Overloading</span></span>  
 <span data-ttu-id="0d302-120">O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0d302-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0d302-121">Sobrecarga de `/` operador afeta o comportamento do `/=` operador.</span><span class="sxs-lookup"><span data-stu-id="0d302-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="0d302-122">Se seu código usa `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="0d302-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0d302-123">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0d302-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d302-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d302-124">Example</span></span>  
 <span data-ttu-id="0d302-125">O exemplo a seguir usa o `/=` operador para dividir um `Integer` variável por um segundo e atribuir a quociente à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="0d302-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 <span data-ttu-id="0d302-126">[!code-vb[17 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0d302-126">[!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d302-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d302-127">See Also</span></span>  
 <span data-ttu-id="0d302-128">[/ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="0d302-128">[/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span></span>  
<span data-ttu-id="0d302-129"> [\\= Operador](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="0d302-129"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="0d302-130"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="0d302-130"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="0d302-131"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="0d302-131"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="0d302-132"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="0d302-132"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="0d302-133"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="0d302-133"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="0d302-134"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="0d302-134"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

