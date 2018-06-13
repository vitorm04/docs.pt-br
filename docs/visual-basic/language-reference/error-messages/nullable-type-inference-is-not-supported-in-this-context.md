---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593185"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="7dda3-102">Inferência de tipo que permite valor nulo não suportada neste contexto</span><span class="sxs-lookup"><span data-stu-id="7dda3-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="7dda3-103">Estruturas e tipos de valor podem ser declaradas anuláveis.</span><span class="sxs-lookup"><span data-stu-id="7dda3-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="7dda3-104">No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipo.</span><span class="sxs-lookup"><span data-stu-id="7dda3-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="7dda3-105">Os exemplos a seguir causam esse erro.</span><span class="sxs-lookup"><span data-stu-id="7dda3-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="7dda3-106">**ID do erro:** BC36629</span><span class="sxs-lookup"><span data-stu-id="7dda3-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7dda3-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7dda3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="7dda3-108">Use um `As` cláusula para declarar a variável como anulável.</span><span class="sxs-lookup"><span data-stu-id="7dda3-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dda3-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7dda3-109">See Also</span></span>  
 [<span data-ttu-id="7dda3-110">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="7dda3-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="7dda3-111">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="7dda3-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
