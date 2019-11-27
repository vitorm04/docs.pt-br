---
title: Operador IsNot
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 616506f64d20e1f150b443433f1b69040136a5ba
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336069"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="1c002-102">Operador IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c002-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="1c002-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="1c002-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c002-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c002-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="1c002-105">Partes</span><span class="sxs-lookup"><span data-stu-id="1c002-105">Parts</span></span>
 <span data-ttu-id="1c002-106">`result` Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c002-106">`result` Required.</span></span> <span data-ttu-id="1c002-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1c002-107">A `Boolean` value.</span></span>

 <span data-ttu-id="1c002-108">`object1` Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c002-108">`object1` Required.</span></span> <span data-ttu-id="1c002-109">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="1c002-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="1c002-110">`object2` Necessário.</span><span class="sxs-lookup"><span data-stu-id="1c002-110">`object2` Required.</span></span> <span data-ttu-id="1c002-111">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="1c002-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c002-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1c002-112">Remarks</span></span>
 <span data-ttu-id="1c002-113">O operador `IsNot` determina se duas referências de objeto se referem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="1c002-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="1c002-114">No entanto, ele não executa comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="1c002-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="1c002-115">Se `object1` e `object2` fizerem referência exatamente à mesma instância de objeto, `result` será `False`; Se não tiverem, `result` será `True`.</span><span class="sxs-lookup"><span data-stu-id="1c002-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="1c002-116">`IsNot` é o oposto do operador de `Is`.</span><span class="sxs-lookup"><span data-stu-id="1c002-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="1c002-117">A vantagem do `IsNot` é que você pode evitar uma sintaxe estranha com `Not` e `Is`, o que pode ser difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="1c002-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="1c002-118">Você pode usar os operadores de `Is` e `IsNot` para testar os objetos de ligação antecipada e de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="1c002-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="1c002-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c002-119">Example</span></span>
 <span data-ttu-id="1c002-120">O exemplo de código a seguir usa tanto o operador de `Is` quanto o operador de `IsNot` para realizar a mesma comparação.</span><span class="sxs-lookup"><span data-stu-id="1c002-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="1c002-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c002-121">See also</span></span>

- [<span data-ttu-id="1c002-122">Operador Is</span><span class="sxs-lookup"><span data-stu-id="1c002-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="1c002-123">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="1c002-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="1c002-124">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c002-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1c002-125">Como testar se dois objetos são iguais</span><span class="sxs-lookup"><span data-stu-id="1c002-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
