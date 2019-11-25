---
title: '&amp;= Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350259"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="50d97-102">&amp;= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50d97-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="50d97-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span><span class="sxs-lookup"><span data-stu-id="50d97-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50d97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50d97-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="50d97-105">Partes</span><span class="sxs-lookup"><span data-stu-id="50d97-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="50d97-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="50d97-106">Required.</span></span> <span data-ttu-id="50d97-107">Any `String` variable or property.</span><span class="sxs-lookup"><span data-stu-id="50d97-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="50d97-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="50d97-108">Required.</span></span> <span data-ttu-id="50d97-109">Qualquer expressão de `String` .</span><span class="sxs-lookup"><span data-stu-id="50d97-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50d97-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="50d97-110">Remarks</span></span>  
 <span data-ttu-id="50d97-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span><span class="sxs-lookup"><span data-stu-id="50d97-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="50d97-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="50d97-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="50d97-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span><span class="sxs-lookup"><span data-stu-id="50d97-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="50d97-114">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="50d97-114">Overloading</span></span>  
 <span data-ttu-id="50d97-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="50d97-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="50d97-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span><span class="sxs-lookup"><span data-stu-id="50d97-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="50d97-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="50d97-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="50d97-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="50d97-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d97-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50d97-119">Example</span></span>  
 <span data-ttu-id="50d97-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span><span class="sxs-lookup"><span data-stu-id="50d97-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="50d97-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50d97-121">See also</span></span>

- [<span data-ttu-id="50d97-122">Operador &</span><span class="sxs-lookup"><span data-stu-id="50d97-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="50d97-123">Operador +=</span><span class="sxs-lookup"><span data-stu-id="50d97-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="50d97-124">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="50d97-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="50d97-125">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="50d97-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="50d97-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50d97-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="50d97-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="50d97-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="50d97-128">Instruções</span><span class="sxs-lookup"><span data-stu-id="50d97-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
