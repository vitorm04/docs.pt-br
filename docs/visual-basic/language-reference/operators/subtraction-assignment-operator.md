---
title: Operador -= (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 753e3efca311da9e09c67131969626ff59c130f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="575dc-102">Operador -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575dc-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="575dc-103">Subtrai o valor de uma expressão do valor de uma variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="575dc-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="575dc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="575dc-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="575dc-105">Partes</span><span class="sxs-lookup"><span data-stu-id="575dc-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="575dc-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="575dc-106">Required.</span></span> <span data-ttu-id="575dc-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="575dc-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="575dc-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="575dc-108">Required.</span></span> <span data-ttu-id="575dc-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="575dc-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="575dc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="575dc-110">Remarks</span></span>  
 <span data-ttu-id="575dc-111">O elemento à esquerda do `-=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="575dc-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="575dc-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="575dc-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="575dc-113">O `-=` operador primeiro subtrai o valor da expressão (no lado direito do operador) do valor da variável ou propriedade (no lado esquerdo do operador).</span><span class="sxs-lookup"><span data-stu-id="575dc-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="575dc-114">O operador, em seguida, atribui o resultado dessa operação à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="575dc-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="575dc-115">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="575dc-115">Overloading</span></span>  
 <span data-ttu-id="575dc-116">O [-operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="575dc-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="575dc-117">Sobrecarga de `-` operador afeta o comportamento do `-=` operador.</span><span class="sxs-lookup"><span data-stu-id="575dc-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="575dc-118">Se seu código usa `-=` em uma classe ou estrutura que sobrecarrega `-`, certifique-se de compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="575dc-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="575dc-119">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="575dc-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="575dc-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="575dc-120">Example</span></span>  
 <span data-ttu-id="575dc-121">O exemplo a seguir usa o `-=` operador subtrair um `Integer` outra variável e atribui o resultado à última variável.</span><span class="sxs-lookup"><span data-stu-id="575dc-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="575dc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="575dc-122">See Also</span></span>  
 [<span data-ttu-id="575dc-123">-Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575dc-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [<span data-ttu-id="575dc-124">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="575dc-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="575dc-125">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="575dc-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="575dc-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="575dc-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="575dc-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="575dc-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="575dc-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="575dc-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
