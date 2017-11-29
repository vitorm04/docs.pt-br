---
title: "O objeto ou a classe não dá suporte ao conjunto de eventos"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="7df3a-102">O objeto ou a classe não dá suporte ao conjunto de eventos</span><span class="sxs-lookup"><span data-stu-id="7df3a-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="7df3a-103">Você tentou usar um `WithEvents` variável com um componente que não pode funcionar como uma fonte de evento para o conjunto de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="7df3a-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="7df3a-104">Por exemplo, se desejar coletar eventos de um objeto, então criar outro objeto que `Implements` o primeiro objeto.</span><span class="sxs-lookup"><span data-stu-id="7df3a-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="7df3a-105">Embora você possa pensar que você pode coletar os eventos do objeto implementado, isso não é sempre o caso.</span><span class="sxs-lookup"><span data-stu-id="7df3a-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="7df3a-106">`Implements`apenas implementa uma interface para métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="7df3a-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="7df3a-107">`WithEvents`Não há suporte para privada `UserControls`, porque as informações de tipo necessária elevar o `ObjectEvent` não está disponível em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7df3a-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7df3a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7df3a-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="7df3a-109">Você não é possível coletar eventos de um componente que não faz eventos fonte.</span><span class="sxs-lookup"><span data-stu-id="7df3a-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7df3a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7df3a-110">See Also</span></span>  
 [<span data-ttu-id="7df3a-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="7df3a-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="7df3a-112">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="7df3a-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
