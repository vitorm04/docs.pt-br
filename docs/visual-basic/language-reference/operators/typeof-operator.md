---
title: Operador TypeOf
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350885"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="62f41-102">Operador TypeOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f41-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="62f41-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span><span class="sxs-lookup"><span data-stu-id="62f41-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="62f41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62f41-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="62f41-105">Partes</span><span class="sxs-lookup"><span data-stu-id="62f41-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="62f41-106">Returned.</span><span class="sxs-lookup"><span data-stu-id="62f41-106">Returned.</span></span> <span data-ttu-id="62f41-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="62f41-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="62f41-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="62f41-108">Required.</span></span> <span data-ttu-id="62f41-109">Any expression that evaluates to a reference type.</span><span class="sxs-lookup"><span data-stu-id="62f41-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="62f41-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="62f41-110">Required.</span></span> <span data-ttu-id="62f41-111">Any data type name.</span><span class="sxs-lookup"><span data-stu-id="62f41-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f41-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="62f41-112">Remarks</span></span>  
 <span data-ttu-id="62f41-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span><span class="sxs-lookup"><span data-stu-id="62f41-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="62f41-114">The compatibility depends on the type category of `typename`.</span><span class="sxs-lookup"><span data-stu-id="62f41-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="62f41-115">The following table shows how compatibility is determined.</span><span class="sxs-lookup"><span data-stu-id="62f41-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="62f41-116">Type category of `typename`</span><span class="sxs-lookup"><span data-stu-id="62f41-116">Type category of `typename`</span></span>|<span data-ttu-id="62f41-117">Compatibility criterion</span><span class="sxs-lookup"><span data-stu-id="62f41-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="62f41-118">Class</span><span class="sxs-lookup"><span data-stu-id="62f41-118">Class</span></span>|<span data-ttu-id="62f41-119">`objectexpression` is of type `typename` or inherits from `typename`</span><span class="sxs-lookup"><span data-stu-id="62f41-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="62f41-120">Estrutura</span><span class="sxs-lookup"><span data-stu-id="62f41-120">Structure</span></span>|<span data-ttu-id="62f41-121">`objectexpression` is of type `typename`</span><span class="sxs-lookup"><span data-stu-id="62f41-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="62f41-122">Interface</span><span class="sxs-lookup"><span data-stu-id="62f41-122">Interface</span></span>|<span data-ttu-id="62f41-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span><span class="sxs-lookup"><span data-stu-id="62f41-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="62f41-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span><span class="sxs-lookup"><span data-stu-id="62f41-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="62f41-125">Caso contrário, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="62f41-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="62f41-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span><span class="sxs-lookup"><span data-stu-id="62f41-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="62f41-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span><span class="sxs-lookup"><span data-stu-id="62f41-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f41-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62f41-128">Example</span></span>  
 <span data-ttu-id="62f41-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span><span class="sxs-lookup"><span data-stu-id="62f41-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="62f41-130">The variable `refInteger` has a run-time type of `Integer`.</span><span class="sxs-lookup"><span data-stu-id="62f41-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="62f41-131">It is compatible with `Integer` but not with `Double`.</span><span class="sxs-lookup"><span data-stu-id="62f41-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="62f41-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="62f41-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="62f41-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="62f41-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="62f41-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="62f41-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f41-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62f41-135">See also</span></span>

- [<span data-ttu-id="62f41-136">Operador Is</span><span class="sxs-lookup"><span data-stu-id="62f41-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="62f41-137">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="62f41-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="62f41-138">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62f41-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="62f41-139">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62f41-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="62f41-140">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="62f41-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="62f41-141">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="62f41-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
