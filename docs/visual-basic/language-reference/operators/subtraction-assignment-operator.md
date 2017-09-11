---
title: -= Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
dev_langs:
- VB
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
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
ms.openlocfilehash: 694033ec89e32b5fdba4092bd60292af536f58dd
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="--operator-visual-basic"></a><span data-ttu-id="4666b-102">Operador -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4666b-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="4666b-103">Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="4666b-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4666b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4666b-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="4666b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4666b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="4666b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4666b-106">Required.</span></span> <span data-ttu-id="4666b-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="4666b-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="4666b-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4666b-108">Required.</span></span> <span data-ttu-id="4666b-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="4666b-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4666b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4666b-110">Remarks</span></span>  
 <span data-ttu-id="4666b-111">O elemento à esquerda do `-=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="4666b-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4666b-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4666b-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="4666b-113">O `-=` operador primeiro subtrai o valor da expressão (no lado direito do operador) do valor da variável ou propriedade (no lado esquerdo do operador).</span><span class="sxs-lookup"><span data-stu-id="4666b-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="4666b-114">O operador atribui o resultado da operação à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="4666b-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4666b-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="4666b-115">Overloading</span></span>  
 <span data-ttu-id="4666b-116">O [-operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="4666b-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4666b-117">Sobrecarga de `-` operador afeta o comportamento do `-=` operador.</span><span class="sxs-lookup"><span data-stu-id="4666b-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="4666b-118">Se seu código usa `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="4666b-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4666b-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4666b-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4666b-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4666b-120">Example</span></span>  
 <span data-ttu-id="4666b-121">O exemplo a seguir usa o `-=` operador para subtrair um `Integer` variável de outra e atribui o resultado à variável último.</span><span class="sxs-lookup"><span data-stu-id="4666b-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 <span data-ttu-id="4666b-122">[!code-vb[VbVbalrOperators n º&11;](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4666b-122">[!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4666b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4666b-123">See Also</span></span>  
 <span data-ttu-id="4666b-124">[-Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) </span><span class="sxs-lookup"><span data-stu-id="4666b-124">[- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) </span></span>  
<span data-ttu-id="4666b-125"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4666b-125"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="4666b-126"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="4666b-126"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="4666b-127"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="4666b-127"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="4666b-128"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="4666b-128"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="4666b-129"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="4666b-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

