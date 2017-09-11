---
title: "Não há suporte para inferência de tipo anulável neste contexto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
dev_langs:
- VB
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c5258933bf8190db7438a0215c06969169f15a71
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="09fb9-102">Inferência de tipo que permite valor nulo não suportada neste contexto</span><span class="sxs-lookup"><span data-stu-id="09fb9-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="09fb9-103">Tipos de valor e estruturas podem ser declaradas anuláveis.</span><span class="sxs-lookup"><span data-stu-id="09fb9-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="09fb9-104">No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="09fb9-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="09fb9-105">Os exemplos a seguir causam esse erro.</span><span class="sxs-lookup"><span data-stu-id="09fb9-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="09fb9-106">**ID do erro:** BC36629</span><span class="sxs-lookup"><span data-stu-id="09fb9-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09fb9-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="09fb9-107">To correct this error</span></span>  
  
-   <span data-ttu-id="09fb9-108">Use um `As` cláusula para declarar a variável como anulável.</span><span class="sxs-lookup"><span data-stu-id="09fb9-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fb9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09fb9-109">See Also</span></span>  
 <span data-ttu-id="09fb9-110">[Tipos de valor anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="09fb9-110">[Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="09fb9-111"> [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="09fb9-111"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>
