---
title: + = Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+=
dev_langs:
- VB
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 16
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
ms.openlocfilehash: 37e631327fbc38f750623469dc0b66f40109c9a2
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0860c-102">Operador += (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0860c-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="0860c-103">Adiciona o valor de uma expressão numérica para o valor de uma variável numérica ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0860c-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="0860c-104">Também pode ser usado para concatenar um `String` expressão para um `String` variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0860c-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0860c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0860c-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0860c-106">Partes</span><span class="sxs-lookup"><span data-stu-id="0860c-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="0860c-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0860c-107">Required.</span></span> <span data-ttu-id="0860c-108">Qualquer numérica ou `String` variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="0860c-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="0860c-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0860c-109">Required.</span></span> <span data-ttu-id="0860c-110">Qualquer numérica ou `String` expressão.</span><span class="sxs-lookup"><span data-stu-id="0860c-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0860c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="0860c-111">Remarks</span></span>  
 <span data-ttu-id="0860c-112">O elemento à esquerda do `+=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="0860c-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0860c-113">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0860c-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0860c-114">O `+=` operador adiciona o valor à sua direita à variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="0860c-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="0860c-115">O `+=` operador também pode ser usado para concatenar a `String` expressão à sua direita o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="0860c-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0860c-116">Quando você usa o `+=` operador, você não poderá determinar se a concatenação de cadeia de caracteres ou adição ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="0860c-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="0860c-117">Use o `&=` operador de concatenação para eliminar ambiguidade e fornecer código de documentação própria.</span><span class="sxs-lookup"><span data-stu-id="0860c-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="0860c-118">Este operador de atribuição executa implicitamente mas conversões de estreitamento não se o ambiente de compilação impõe semântica estrita de ampliação.</span><span class="sxs-lookup"><span data-stu-id="0860c-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="0860c-119">Para obter mais informações sobre essas conversões, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0860c-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="0860c-120">Para obter mais informações sobre a semântica estrita e permissiva, consulte [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0860c-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="0860c-121">Se semântica permissiva é permitida, o `+=` operador implicitamente executa várias conversões de cadeia de caracteres e numéricos idênticas àqueles executados pelo `+` operador.</span><span class="sxs-lookup"><span data-stu-id="0860c-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="0860c-122">Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0860c-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0860c-123">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="0860c-123">Overloading</span></span>  
 <span data-ttu-id="0860c-124">O `+` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0860c-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0860c-125">Sobrecarga de `+` operador afeta o comportamento do `+=` operador.</span><span class="sxs-lookup"><span data-stu-id="0860c-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="0860c-126">Se seu código usa `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="0860c-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0860c-127">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0860c-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0860c-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0860c-128">Example</span></span>  
 <span data-ttu-id="0860c-129">O exemplo a seguir usa o `+=` operador para combinar o valor de uma variável com outra.</span><span class="sxs-lookup"><span data-stu-id="0860c-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="0860c-130">A primeira parte usa `+=` com variáveis numéricas para adicionar um valor para outro.</span><span class="sxs-lookup"><span data-stu-id="0860c-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="0860c-131">A segunda parte usa `+=` com `String` variáveis para concatenar um valor com outro.</span><span class="sxs-lookup"><span data-stu-id="0860c-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="0860c-132">Em ambos os casos, o resultado é atribuído à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="0860c-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 <span data-ttu-id="0860c-133">[!code-vb[VbVbalrOperators&#7;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0860c-133">[!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="0860c-134">[!code-vb[VbVbalrOperators n º&8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0860c-134">[!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="0860c-135">O valor de `num1` agora é 13 e o valor de `str1` é agora "103".</span><span class="sxs-lookup"><span data-stu-id="0860c-135">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0860c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0860c-136">See Also</span></span>  
 <span data-ttu-id="0860c-137">[+ Operador](../../../visual-basic/language-reference/operators/addition-operator.md) </span><span class="sxs-lookup"><span data-stu-id="0860c-137">[+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md) </span></span>  
<span data-ttu-id="0860c-138"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="0860c-138"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="0860c-139"> [Operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="0860c-139"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="0860c-140"> [Operadores de concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="0860c-140"> [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md) </span></span>  
<span data-ttu-id="0860c-141"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="0860c-141"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="0860c-142"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="0860c-142"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="0860c-143"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="0860c-143"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

