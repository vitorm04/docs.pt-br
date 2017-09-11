---
title: '&amp;= Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
dev_langs:
- VB
helpviewer_keywords:
- operator &=
- assignment statements, compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
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
ms.openlocfilehash: 14807b95580a28425497e6b593ed274c3c20200c
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="fe3cc-102">&amp;= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe3cc-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="fe3cc-103">Concatena uma `String` expressão para um `String` variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe3cc-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fe3cc-105">Partes</span><span class="sxs-lookup"><span data-stu-id="fe3cc-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="fe3cc-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-106">Required.</span></span> <span data-ttu-id="fe3cc-107">Qualquer `String` variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="fe3cc-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-108">Required.</span></span> <span data-ttu-id="fe3cc-109">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="fe3cc-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe3cc-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe3cc-110">Remarks</span></span>  
 <span data-ttu-id="fe3cc-111">O elemento à esquerda do `&=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="fe3cc-112">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="fe3cc-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="fe3cc-113">O `&=` operador concatena a `String` expressão à sua direita o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fe3cc-114">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="fe3cc-114">Overloading</span></span>  
 <span data-ttu-id="fe3cc-115">O [< / operador](../../../visual-basic/language-reference/operators/concatenation-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fe3cc-116">Sobrecarga de `&` operador afeta o comportamento do `&=` operador.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="fe3cc-117">Se seu código usa `&=` em uma classe ou estrutura que sobrecarrega `&`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fe3cc-118">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fe3cc-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe3cc-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe3cc-119">Example</span></span>  
 <span data-ttu-id="fe3cc-120">O exemplo a seguir usa o `&=` operador para concatenar duas `String` variáveis e atribui o resultado à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="fe3cc-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 <span data-ttu-id="fe3cc-121">[!code-vb[VbVbalrOperators n º&3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fe3cc-121">[!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3cc-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe3cc-122">See Also</span></span>  
 <span data-ttu-id="fe3cc-123">[< / Operador](../../../visual-basic/language-reference/operators/concatenation-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fe3cc-123">[& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) </span></span>  
<span data-ttu-id="fe3cc-124"> [+ = Operador](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fe3cc-124"> [+= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span></span>  
<span data-ttu-id="fe3cc-125"> [Operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="fe3cc-125"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="fe3cc-126"> [Operadores de concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="fe3cc-126"> [Concatenation Operators](../../../visual-basic/language-reference/operators/concatenation-operators.md) </span></span>  
<span data-ttu-id="fe3cc-127"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="fe3cc-127"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="fe3cc-128"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="fe3cc-128"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="fe3cc-129"> [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="fe3cc-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

