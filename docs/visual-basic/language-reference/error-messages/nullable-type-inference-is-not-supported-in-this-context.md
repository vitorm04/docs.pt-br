---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249494"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="b849c-102">Inferência de tipo que permite valor nulo não suportada neste contexto</span><span class="sxs-lookup"><span data-stu-id="b849c-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="b849c-103">Tipos e estruturas de valor podem ser declaradas anuladas.</span><span class="sxs-lookup"><span data-stu-id="b849c-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="b849c-104">No entanto, você não pode usar a declaração anulada em combinação com a inferência do tipo.</span><span class="sxs-lookup"><span data-stu-id="b849c-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="b849c-105">Os exemplos a seguir causam esse erro.</span><span class="sxs-lookup"><span data-stu-id="b849c-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="b849c-106">**ID de erro:** BC36629</span><span class="sxs-lookup"><span data-stu-id="b849c-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b849c-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b849c-107">To correct this error</span></span>  
  
- <span data-ttu-id="b849c-108">Use `As` uma cláusula para declarar a variável como um tipo de valor anulado.</span><span class="sxs-lookup"><span data-stu-id="b849c-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b849c-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="b849c-109">See also</span></span>

- [<span data-ttu-id="b849c-110">Tipos de valor anulados</span><span class="sxs-lookup"><span data-stu-id="b849c-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="b849c-111">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="b849c-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
