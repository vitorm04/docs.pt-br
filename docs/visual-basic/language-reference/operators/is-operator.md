---
title: Operador Is (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 8beca1dc8788514224f70cacc5b8ede0974f5230
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601944"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="ba955-102">Operador Is (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba955-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="ba955-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="ba955-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba955-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba955-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="ba955-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ba955-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="ba955-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ba955-106">Required.</span></span> <span data-ttu-id="ba955-107">Qualquer `Boolean` valor.</span><span class="sxs-lookup"><span data-stu-id="ba955-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="ba955-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ba955-108">Required.</span></span> <span data-ttu-id="ba955-109">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="ba955-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="ba955-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ba955-110">Required.</span></span> <span data-ttu-id="ba955-111">Qualquer `Object` nome.</span><span class="sxs-lookup"><span data-stu-id="ba955-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba955-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ba955-112">Remarks</span></span>  
 <span data-ttu-id="ba955-113">O `Is` operador determina se duas referências de objeto referem-se ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="ba955-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="ba955-114">No entanto, ele não realiza comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="ba955-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="ba955-115">Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `True`; caso contrário, `result` é `False`.</span><span class="sxs-lookup"><span data-stu-id="ba955-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="ba955-116">`Is` também pode ser usado com o `TypeOf` palavra-chave para fazer um `TypeOf`... `Is` expressão, que testa se uma variável de objeto é compatível com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="ba955-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba955-117">O `Is` palavra-chave também é usada a [selecione... Caso a instrução](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ba955-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba955-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba955-118">Example</span></span>  
 <span data-ttu-id="ba955-119">O exemplo a seguir usa o `Is` operador para comparar pares de referências de objeto.</span><span class="sxs-lookup"><span data-stu-id="ba955-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="ba955-120">Os resultados são atribuídos a um `Boolean` valor representando se os dois objetos são idênticos.</span><span class="sxs-lookup"><span data-stu-id="ba955-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="ba955-121">Como demonstrado no exemplo anterior, você pode usar o `Is` operador para o teste associação inicial e objetos de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="ba955-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba955-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba955-122">See Also</span></span>  
 [<span data-ttu-id="ba955-123">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="ba955-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="ba955-124">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="ba955-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="ba955-125">Operadores de comparação no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba955-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="ba955-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba955-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="ba955-127">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="ba955-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="ba955-128">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="ba955-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
