---
title: Operador IsNot (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ffafff915af8a94e9bc135246064e4c049d41838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596456"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="1c8b4-102">Operador IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c8b4-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="1c8b4-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c8b4-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="1c8b4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1c8b4-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1c8b4-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-106">Required.</span></span> <span data-ttu-id="1c8b4-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="1c8b4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-108">Required.</span></span> <span data-ttu-id="1c8b4-109">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="1c8b4-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-110">Required.</span></span> <span data-ttu-id="1c8b4-111">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c8b4-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c8b4-112">Remarks</span></span>  
 <span data-ttu-id="1c8b4-113">O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="1c8b4-114">No entanto, ele não realiza comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="1c8b4-115">Se `object1` e `object2` fazem referência à mesma instância de objeto, `result` é `False`; caso contrário, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="1c8b4-116">`IsNot` é o oposto do `Is` operador.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="1c8b4-117">A vantagem de `IsNot` é que você pode evitar sintaxes estranhas com `Not` e `Is`, que pode ser difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="1c8b4-118">Você pode usar o `Is` e `IsNot` operadores para testar objetos de associação antecipada e tardia.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c8b4-119">O `IsNot` operador não pode ser usado para comparar expressões retornadas do `TypeOf` operador.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="1c8b4-120">Em vez disso, você deve usar o `Not` e `Is` operadores.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c8b4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c8b4-121">Example</span></span>  
 <span data-ttu-id="1c8b4-122">O exemplo de código a seguir usa ambos os `Is` operador e o `IsNot` operador para realizar a mesma comparação.</span><span class="sxs-lookup"><span data-stu-id="1c8b4-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1c8b4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c8b4-123">See also</span></span>
- [<span data-ttu-id="1c8b4-124">Operador Is</span><span class="sxs-lookup"><span data-stu-id="1c8b4-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="1c8b4-125">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="1c8b4-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="1c8b4-126">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c8b4-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1c8b4-127">Como: Testar se dois objetos são iguais</span><span class="sxs-lookup"><span data-stu-id="1c8b4-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
