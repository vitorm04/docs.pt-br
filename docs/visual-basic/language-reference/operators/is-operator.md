---
title: Operador Is
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349540"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="f1ed6-102">Operador Is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1ed6-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="f1ed6-103">Compares two object reference variables.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ed6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1ed6-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="f1ed6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="f1ed6-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f1ed6-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-106">Required.</span></span> <span data-ttu-id="f1ed6-107">Any `Boolean` value.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="f1ed6-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-108">Required.</span></span> <span data-ttu-id="f1ed6-109">Any `Object` name.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="f1ed6-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-110">Required.</span></span> <span data-ttu-id="f1ed6-111">Any `Object` name.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1ed6-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1ed6-112">Remarks</span></span>  
 <span data-ttu-id="f1ed6-113">The `Is` operator determines if two object references refer to the same object.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="f1ed6-114">However, it does not perform value comparisons.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="f1ed6-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="f1ed6-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1ed6-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f1ed6-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1ed6-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1ed6-118">Example</span></span>  
 <span data-ttu-id="f1ed6-119">The following example uses the `Is` operator to compare pairs of object references.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="f1ed6-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="f1ed6-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span><span class="sxs-lookup"><span data-stu-id="f1ed6-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1ed6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1ed6-122">See also</span></span>

- [<span data-ttu-id="f1ed6-123">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="f1ed6-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="f1ed6-124">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="f1ed6-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="f1ed6-125">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1ed6-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="f1ed6-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1ed6-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f1ed6-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="f1ed6-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f1ed6-128">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="f1ed6-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
