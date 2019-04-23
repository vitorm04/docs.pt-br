---
title: O objeto ou a classe não dá suporte ao conjunto de eventos
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342876"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="6f524-102">O objeto ou a classe não dá suporte ao conjunto de eventos</span><span class="sxs-lookup"><span data-stu-id="6f524-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="6f524-103">Você tentou usar um `WithEvents` variável com um componente que não pode funcionar como uma origem de evento para o conjunto de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="6f524-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="6f524-104">Por exemplo, você quiser coletar os eventos de um objeto e, em seguida, criar outro objeto que `Implements` o primeiro objeto.</span><span class="sxs-lookup"><span data-stu-id="6f524-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="6f524-105">Embora você possa pensar que você pode coletar os eventos do objeto implementado, isso nem sempre é o caso.</span><span class="sxs-lookup"><span data-stu-id="6f524-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="6f524-106">`Implements` apenas implementa uma interface para métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="6f524-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="6f524-107">`WithEvents` Não há suporte para privado `UserControls`, porque o tipo de informação necessária para elevar o `ObjectEvent` não está disponível em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6f524-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f524-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6f524-108">To correct this error</span></span>  
  
1. <span data-ttu-id="6f524-109">Você não pode coletar eventos para um componente que não faz eventos fonte.</span><span class="sxs-lookup"><span data-stu-id="6f524-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f524-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f524-110">See also</span></span>

- [<span data-ttu-id="6f524-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="6f524-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="6f524-112">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="6f524-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
