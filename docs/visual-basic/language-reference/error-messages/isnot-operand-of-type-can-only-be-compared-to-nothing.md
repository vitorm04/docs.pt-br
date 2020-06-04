---
title: O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: fb61b04021bd844fade94413b4f3b28b82f6411b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402792"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="94a08-102">O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="94a08-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="94a08-103">Uma variável declarada como um tipo de valor anulável foi comparada a uma expressão diferente de `Nothing` usar o `IsNot` operador.</span><span class="sxs-lookup"><span data-stu-id="94a08-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="94a08-104">**ID do erro:** BC32128</span><span class="sxs-lookup"><span data-stu-id="94a08-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="94a08-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="94a08-105">To correct this error</span></span>

<span data-ttu-id="94a08-106">Para comparar um tipo anulável a uma expressão que não seja `Nothing` usando o `IsNot` operador, chame o `GetType` método no tipo anulável e compare o resultado com a expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="94a08-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="94a08-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="94a08-107">See also</span></span>

- [<span data-ttu-id="94a08-108">Tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="94a08-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="94a08-109">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="94a08-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
