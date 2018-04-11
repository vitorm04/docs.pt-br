---
title: Operador += (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ac8f5679aa90c50c15c33a957cfc75d9ccecde6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="e4c51-102">Operador += (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4c51-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="e4c51-103">Adiciona o valor de uma expressão numérica para o valor de uma variável numérica ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4c51-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="e4c51-104">Também pode ser usado para concatenar uma `String` expressão para uma `String` variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4c51-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c51-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4c51-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e4c51-106">Partes</span><span class="sxs-lookup"><span data-stu-id="e4c51-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e4c51-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e4c51-107">Required.</span></span> <span data-ttu-id="e4c51-108">Qualquer numéricos ou `String` variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="e4c51-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e4c51-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e4c51-109">Required.</span></span> <span data-ttu-id="e4c51-110">Qualquer numéricos ou `String` expressão.</span><span class="sxs-lookup"><span data-stu-id="e4c51-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4c51-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4c51-111">Remarks</span></span>  
 <span data-ttu-id="e4c51-112">O elemento à esquerda do `+=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="e4c51-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e4c51-113">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="e4c51-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e4c51-114">O `+=` operador adiciona o valor à sua direita à variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="e4c51-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="e4c51-115">O `+=` operador também pode ser usado para concatenar a `String` expressão à direita para o `String` variável ou propriedade em sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="e4c51-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4c51-116">Quando você usa o `+=` operador, você não poderá determinar se a concatenação de cadeia de caracteres ou adição ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="e4c51-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="e4c51-117">Use o `&=` operador de concatenação para eliminar a ambiguidade e fornecer o código autodocumentado.</span><span class="sxs-lookup"><span data-stu-id="e4c51-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="e4c51-118">Este operador de atribuição implicitamente executa widening mas conversões de estreitamento não se o ambiente de compilação impõe a semântica estrita.</span><span class="sxs-lookup"><span data-stu-id="e4c51-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="e4c51-119">Para obter mais informações sobre essas conversões, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e4c51-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="e4c51-120">Para obter mais informações sobre a semântica estrita e permissiva, consulte [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e4c51-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="e4c51-121">Se a semântica permissiva é permitida, o `+=` operador implicitamente executa uma variedade de conversões de cadeia de caracteres e numéricos idênticas àqueles executados pelo `+` operador.</span><span class="sxs-lookup"><span data-stu-id="e4c51-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="e4c51-122">Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="e4c51-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e4c51-123">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="e4c51-123">Overloading</span></span>  
 <span data-ttu-id="e4c51-124">O `+` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e4c51-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e4c51-125">Sobrecarga de `+` operador afeta o comportamento do `+=` operador.</span><span class="sxs-lookup"><span data-stu-id="e4c51-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="e4c51-126">Se seu código usa `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="e4c51-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e4c51-127">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e4c51-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c51-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4c51-128">Example</span></span>  
 <span data-ttu-id="e4c51-129">O exemplo a seguir usa o `+=` operador para combinar o valor de uma variável com outra.</span><span class="sxs-lookup"><span data-stu-id="e4c51-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="e4c51-130">A primeira parte usa `+=` com variáveis numéricas para adicionar um valor para outro.</span><span class="sxs-lookup"><span data-stu-id="e4c51-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="e4c51-131">A segunda parte usa `+=` com `String` variáveis para concatenar um valor com outro.</span><span class="sxs-lookup"><span data-stu-id="e4c51-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="e4c51-132">Em ambos os casos, o resultado é atribuído à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="e4c51-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 <span data-ttu-id="e4c51-133">O valor de `num1` agora é 13 e o valor de `str1` é agora "103".</span><span class="sxs-lookup"><span data-stu-id="e4c51-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c51-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4c51-134">See Also</span></span>  
 [<span data-ttu-id="e4c51-135">Operador +</span><span class="sxs-lookup"><span data-stu-id="e4c51-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [<span data-ttu-id="e4c51-136">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="e4c51-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="e4c51-137">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="e4c51-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="e4c51-138">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="e4c51-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="e4c51-139">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4c51-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e4c51-140">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="e4c51-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e4c51-141">Instruções</span><span class="sxs-lookup"><span data-stu-id="e4c51-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
