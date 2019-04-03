---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 9f7f878649d8b96f050b56d5b878eb3d67e027ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819236"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="f6b0a-102">Inferência de tipo que permite valor nulo não suportada neste contexto</span><span class="sxs-lookup"><span data-stu-id="f6b0a-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="f6b0a-103">Tipos de valor e estruturas podem ser declaradas que permitem valor nulas.</span><span class="sxs-lookup"><span data-stu-id="f6b0a-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="f6b0a-104">No entanto, você não pode usar a declaração que permite valor nula em combinação com a inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="f6b0a-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="f6b0a-105">Os exemplos a seguir causam esse erro.</span><span class="sxs-lookup"><span data-stu-id="f6b0a-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="f6b0a-106">**ID do erro:** BC36629</span><span class="sxs-lookup"><span data-stu-id="f6b0a-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6b0a-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f6b0a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f6b0a-108">Use um `As` cláusula para declarar a variável como anulável.</span><span class="sxs-lookup"><span data-stu-id="f6b0a-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b0a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6b0a-109">See also</span></span>

- [<span data-ttu-id="f6b0a-110">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="f6b0a-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="f6b0a-111">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="f6b0a-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
