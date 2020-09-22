---
title: O objeto ou a classe não dá suporte ao conjunto de eventos
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873650"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="2c649-102">O objeto ou a classe não dá suporte ao conjunto de eventos</span><span class="sxs-lookup"><span data-stu-id="2c649-102">Object or class does not support the set of events</span></span>

<span data-ttu-id="2c649-103">Você tentou usar uma `WithEvents` variável com um componente que não pode funcionar como uma origem do evento para o conjunto de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="2c649-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="2c649-104">Por exemplo, você queria coletar os eventos de um objeto e, em seguida, criar outro objeto que `Implements` o primeiro objeto.</span><span class="sxs-lookup"><span data-stu-id="2c649-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="2c649-105">Embora você possa imaginar que possa coletar os eventos do objeto implementado, esse nem sempre é o caso.</span><span class="sxs-lookup"><span data-stu-id="2c649-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="2c649-106">`Implements` implementa apenas uma interface para métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="2c649-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="2c649-107">`WithEvents` Não tem suporte para privado `UserControls` , porque as informações de tipo necessárias para gerar o `ObjectEvent` não estão disponíveis no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2c649-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c649-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2c649-108">To correct this error</span></span>  
  
1. <span data-ttu-id="2c649-109">Você não pode coletar eventos para um componente que não tem eventos de origem.</span><span class="sxs-lookup"><span data-stu-id="2c649-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c649-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="2c649-110">See also</span></span>

- [<span data-ttu-id="2c649-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="2c649-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="2c649-112">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="2c649-112">Implements Statement</span></span>](../statements/implements-statement.md)
