---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409380"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="dd556-102">Inferência de tipo que permite valor nulo não suportada neste contexto</span><span class="sxs-lookup"><span data-stu-id="dd556-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="dd556-103">Tipos e estruturas de valor podem ser declarados como anuláveis.</span><span class="sxs-lookup"><span data-stu-id="dd556-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="dd556-104">No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="dd556-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="dd556-105">Os exemplos a seguir causam esse erro.</span><span class="sxs-lookup"><span data-stu-id="dd556-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="dd556-106">**ID do erro:** BC36629</span><span class="sxs-lookup"><span data-stu-id="dd556-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd556-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="dd556-107">To correct this error</span></span>  
  
- <span data-ttu-id="dd556-108">Use uma `As` cláusula para declarar a variável como um tipo de valor anulável.</span><span class="sxs-lookup"><span data-stu-id="dd556-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd556-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd556-109">See also</span></span>

- [<span data-ttu-id="dd556-110">Tipos de valor anulável</span><span class="sxs-lookup"><span data-stu-id="dd556-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="dd556-111">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="dd556-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
