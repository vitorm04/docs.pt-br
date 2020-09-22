---
title: Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: fbeaa224ea9e095f86c37e571492d83bc98b4397
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871095"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="3bffd-102">Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto</span><span class="sxs-lookup"><span data-stu-id="3bffd-102">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="3bffd-103">Determinadas propriedades, métodos e operações só podem ser aplicadas a `Collection` objetos.</span><span class="sxs-lookup"><span data-stu-id="3bffd-103">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="3bffd-104">Você especificou uma operação ou propriedade que é exclusiva para coleções, mas o objeto não é uma coleção.</span><span class="sxs-lookup"><span data-stu-id="3bffd-104">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3bffd-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3bffd-105">To correct this error</span></span>  
  
1. <span data-ttu-id="3bffd-106">Verifique a ortografia do nome do objeto ou da propriedade ou verifique se o objeto é um `Collection` objeto.</span><span class="sxs-lookup"><span data-stu-id="3bffd-106">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="3bffd-107">Examine o `Add` método usado para adicionar o objeto à coleção para ter certeza de que a sintaxe está correta e que todos os identificadores foram digitados corretamente.</span><span class="sxs-lookup"><span data-stu-id="3bffd-107">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bffd-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="3bffd-108">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
