---
title: Operador ^= (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="21d4b-102">Operador ^= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21d4b-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="21d4b-103">Gera o valor de uma variável ou propriedade à potência de uma expressão e atribui o resultado de volta para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="21d4b-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21d4b-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="21d4b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="21d4b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="21d4b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21d4b-106">Required.</span></span> <span data-ttu-id="21d4b-107">Qualquer variável numérica ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="21d4b-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="21d4b-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="21d4b-108">Required.</span></span> <span data-ttu-id="21d4b-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="21d4b-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21d4b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="21d4b-110">Remarks</span></span>  
 <span data-ttu-id="21d4b-111">O elemento à esquerda do `^=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="21d4b-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="21d4b-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="21d4b-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="21d4b-113">O `^=` operador primeiro gera o valor da variável ou propriedade (no lado esquerdo do operador) para a potência do valor da expressão (no lado direito do operador).</span><span class="sxs-lookup"><span data-stu-id="21d4b-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="21d4b-114">O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="21d4b-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="21d4b-115">Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="21d4b-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="21d4b-116">Operandos de qualquer outro tipo são convertidos em `Double`, e o resultado é sempre `Double`.</span><span class="sxs-lookup"><span data-stu-id="21d4b-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="21d4b-117">O valor de `expression` pode ser fracionário, negativo, ou ambos.</span><span class="sxs-lookup"><span data-stu-id="21d4b-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="21d4b-118">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="21d4b-118">Overloading</span></span>  
 <span data-ttu-id="21d4b-119">O [^ operador](../../../visual-basic/language-reference/operators/exponentiation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="21d4b-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="21d4b-120">Sobrecarga de `^` operador afeta o comportamento do `^=` operador.</span><span class="sxs-lookup"><span data-stu-id="21d4b-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="21d4b-121">Se seu código usa `^=` em uma classe ou estrutura que sobrecarrega `^`, certifique-se de compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="21d4b-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="21d4b-122">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="21d4b-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21d4b-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21d4b-123">Example</span></span>  
 <span data-ttu-id="21d4b-124">O exemplo a seguir usa o `^=` operador para aumentar o valor de um `Integer` variável à potência de uma segunda variável e atribui o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="21d4b-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="21d4b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21d4b-125">See Also</span></span>  
 [<span data-ttu-id="21d4b-126">Operador ^</span><span class="sxs-lookup"><span data-stu-id="21d4b-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [<span data-ttu-id="21d4b-127">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="21d4b-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="21d4b-128">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="21d4b-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="21d4b-129">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21d4b-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="21d4b-130">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="21d4b-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="21d4b-131">Instruções</span><span class="sxs-lookup"><span data-stu-id="21d4b-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
