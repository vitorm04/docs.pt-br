---
title: O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 06dc6f1532fecefba4e507bd0cc24aadc936d137
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524376"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="cf4a6-102">O operando 'IsNot' do tipo 'typename' só pode ser comparado a 'Nothing', porque 'typename' é um tipo que permite valor nulo</span><span class="sxs-lookup"><span data-stu-id="cf4a6-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="cf4a6-103">Uma variável declarada como anulável foi comparada com uma expressão diferente de `Nothing` usando o operador `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="cf4a6-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="cf4a6-104">**ID do erro:** BC32128</span><span class="sxs-lookup"><span data-stu-id="cf4a6-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cf4a6-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cf4a6-105">To correct this error</span></span>

<span data-ttu-id="cf4a6-106">Para comparar um tipo anulável com uma expressão que não seja `Nothing` usando o operador `IsNot`, chame o método `GetType` no tipo anulável e compare o resultado com a expressão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cf4a6-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="cf4a6-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf4a6-107">See also</span></span>

- [<span data-ttu-id="cf4a6-108">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="cf4a6-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="cf4a6-109">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="cf4a6-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
