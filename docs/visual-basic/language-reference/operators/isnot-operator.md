---
title: Operador IsNot
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811035"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="c280e-102">Operador IsNot (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c280e-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="c280e-103">Compara duas variáveis de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="c280e-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="c280e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c280e-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="c280e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c280e-105">Parts</span></span>

- `result`

  <span data-ttu-id="c280e-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="c280e-106">Required.</span></span> <span data-ttu-id="c280e-107">Um valor `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c280e-107">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="c280e-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="c280e-108">Required.</span></span> <span data-ttu-id="c280e-109">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="c280e-109">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="c280e-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="c280e-110">Required.</span></span> <span data-ttu-id="c280e-111">Qualquer `Object` variável ou expressão.</span><span class="sxs-lookup"><span data-stu-id="c280e-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="c280e-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c280e-112">Remarks</span></span>

<span data-ttu-id="c280e-113">O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes.</span><span class="sxs-lookup"><span data-stu-id="c280e-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="c280e-114">No entanto, ele não executa comparações de valor.</span><span class="sxs-lookup"><span data-stu-id="c280e-114">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="c280e-115">Se `object1` e `object2` ambos se referirem exatamente à mesma instância de objeto, `result` será `False` ; se não forem, `result` é `True` .</span><span class="sxs-lookup"><span data-stu-id="c280e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="c280e-116">`IsNot` é o oposto do `Is` operador.</span><span class="sxs-lookup"><span data-stu-id="c280e-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="c280e-117">A vantagem do `IsNot` é que você pode evitar uma sintaxe estranha com `Not` e `Is` , que pode ser difícil de ler.</span><span class="sxs-lookup"><span data-stu-id="c280e-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="c280e-118">Você pode usar os `Is` `IsNot` operadores e para testar os objetos de ligação antecipada e de associação tardia.</span><span class="sxs-lookup"><span data-stu-id="c280e-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="c280e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c280e-119">Example</span></span>

<span data-ttu-id="c280e-120">O exemplo de código a seguir usa o `Is` operador e o `IsNot` operador para realizar a mesma comparação.</span><span class="sxs-lookup"><span data-stu-id="c280e-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="c280e-121">Use o operador TypeOf com o operador IsNot</span><span class="sxs-lookup"><span data-stu-id="c280e-121">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="c280e-122">A partir do Visual Basic 14, você pode usar o `TypeOf` operador com o `IsNot` operador para testar se um objeto *não* é compatível com um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="c280e-122">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="c280e-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c280e-123">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="c280e-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="c280e-124">See also</span></span>

- [<span data-ttu-id="c280e-125">Operador Is</span><span class="sxs-lookup"><span data-stu-id="c280e-125">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="c280e-126">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="c280e-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="c280e-127">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c280e-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c280e-128">Como testar se dois objetos são iguais</span><span class="sxs-lookup"><span data-stu-id="c280e-128">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
