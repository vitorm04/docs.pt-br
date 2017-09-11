---
title: Operador IsNot (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isnot
dev_langs:
- VB
helpviewer_keywords:
- IsNot operator
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
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
ms.openlocfilehash: 95e329db54a4141ada413fb38f36a1d282f91195
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="11c71-102">Operador IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11c71-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="11c71-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="11c71-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11c71-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="11c71-105">Partes</span><span class="sxs-lookup"><span data-stu-id="11c71-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="11c71-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="11c71-106">Required.</span></span> <span data-ttu-id="11c71-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="11c71-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="11c71-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="11c71-108">Required.</span></span> <span data-ttu-id="11c71-109">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="11c71-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="11c71-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="11c71-110">Required.</span></span> <span data-ttu-id="11c71-111">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="11c71-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11c71-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="11c71-112">Remarks</span></span>  
 <span data-ttu-id="11c71-113">O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="11c71-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="11c71-114">No entanto, ele não realiza comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="11c71-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="11c71-115">Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `False`; se não, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="11c71-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="11c71-116">`IsNot`é o oposto do `Is` operador.</span><span class="sxs-lookup"><span data-stu-id="11c71-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="11c71-117">A vantagem de `IsNot` é que você pode evitar sintaxes estranhas com `Not` e `Is`, que pode ser difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="11c71-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="11c71-118">Você pode usar o `Is` e `IsNot` operadores para testar objetos de associação antecipada e tardia.</span><span class="sxs-lookup"><span data-stu-id="11c71-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11c71-119">O `IsNot` operador não pode ser usado para comparar expressões retornadas do `TypeOf` operador.</span><span class="sxs-lookup"><span data-stu-id="11c71-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="11c71-120">Em vez disso, você deve usar o `Not` e `Is` operadores.</span><span class="sxs-lookup"><span data-stu-id="11c71-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11c71-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11c71-121">Example</span></span>  
 <span data-ttu-id="11c71-122">O exemplo de código a seguir usa o `Is` operador e o `IsNot` operador para realizar a mesma comparação.</span><span class="sxs-lookup"><span data-stu-id="11c71-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 <span data-ttu-id="11c71-123">[!code-vb[29 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="11c71-123">[!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c71-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11c71-124">See Also</span></span>  
 <span data-ttu-id="11c71-125">[Operador is](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="11c71-125">[Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="11c71-126"> [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="11c71-126"> [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md) </span></span>  
<span data-ttu-id="11c71-127"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="11c71-127"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="11c71-128"> [Como testar se dois objetos são iguais](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)</span><span class="sxs-lookup"><span data-stu-id="11c71-128"> [How to: Test Whether Two Objects Are the Same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)</span></span>

