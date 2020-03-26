---
title: O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 1660971e2a1a11d7a2d14f222cd149edf4aa4c7b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249507"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="ec575-102">O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="ec575-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="ec575-103">Uma variável declarada como um tipo de valor nulo `Nothing` foi `IsNot` comparada a uma expressão diferente do uso do operador.</span><span class="sxs-lookup"><span data-stu-id="ec575-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="ec575-104">**ID de erro:** BC32128</span><span class="sxs-lookup"><span data-stu-id="ec575-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec575-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ec575-105">To correct this error</span></span>

<span data-ttu-id="ec575-106">Para comparar um tipo anulado a `Nothing` uma `IsNot` expressão diferente `GetType` de usar o operador, chame o método no tipo anulado e compare o resultado com a expressão, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec575-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="ec575-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="ec575-107">See also</span></span>

- [<span data-ttu-id="ec575-108">Tipos de valor anulados</span><span class="sxs-lookup"><span data-stu-id="ec575-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="ec575-109">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="ec575-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
