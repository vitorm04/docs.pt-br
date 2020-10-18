---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 610d2dc427d882c412b87eb67f021a8a86025f25
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159919"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="5adc4-102">BC36629: não há suporte para inferência de tipo anulável neste contexto</span><span class="sxs-lookup"><span data-stu-id="5adc4-102">BC36629: Nullable type inference is not supported in this context</span></span>

<span data-ttu-id="5adc4-103">Tipos e estruturas de valor podem ser declarados como anuláveis.</span><span class="sxs-lookup"><span data-stu-id="5adc4-103">Value types and structures can be declared nullable.</span></span>

```vb
Dim a? As Integer
Dim b As Integer?
```

 <span data-ttu-id="5adc4-104">No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="5adc4-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="5adc4-105">Os exemplos a seguir causam esse erro.</span><span class="sxs-lookup"><span data-stu-id="5adc4-105">The following examples cause this error.</span></span>

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 <span data-ttu-id="5adc4-106">**ID do erro:** BC36629</span><span class="sxs-lookup"><span data-stu-id="5adc4-106">**Error ID:** BC36629</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="5adc4-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5adc4-107">To correct this error</span></span>

- <span data-ttu-id="5adc4-108">Use uma `As` cláusula para declarar a variável como um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="5adc4-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>

## <a name="see-also"></a><span data-ttu-id="5adc4-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="5adc4-109">See also</span></span>

- [<span data-ttu-id="5adc4-110">Tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="5adc4-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="5adc4-111">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="5adc4-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
