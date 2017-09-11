---
title: "Objeto ou classe não dá suporte para o conjunto de eventos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID459
dev_langs:
- VB
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: 8
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
ms.openlocfilehash: b256cced02be96c9f2981d6446aa3d64a2a0ff84
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="55fab-102">O objeto ou a classe não dá suporte ao conjunto de eventos</span><span class="sxs-lookup"><span data-stu-id="55fab-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="55fab-103">Você tentou usar um `WithEvents` variável com um componente que não pode trabalhar como uma fonte de evento para o conjunto de eventos especificado.</span><span class="sxs-lookup"><span data-stu-id="55fab-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="55fab-104">Por exemplo, se desejar coletar eventos de um objeto, então criar outro objeto que `Implements` o primeiro objeto.</span><span class="sxs-lookup"><span data-stu-id="55fab-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="55fab-105">Embora você possa pensar que você pode coletar os eventos do objeto implementado, isso nem sempre é o caso.</span><span class="sxs-lookup"><span data-stu-id="55fab-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="55fab-106">`Implements`apenas implementa uma interface para métodos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="55fab-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="55fab-107">`WithEvents`Não há suporte para particular`UserControls`, pois a informação de tipo necessária para elevar o `ObjectEvent` não está disponível em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="55fab-107">`WithEvents` is not supported for private`UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="55fab-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="55fab-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="55fab-109">Você não pode coletar eventos de um componente que não faz eventos fonte.</span><span class="sxs-lookup"><span data-stu-id="55fab-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fab-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55fab-110">See Also</span></span>  
 <span data-ttu-id="55fab-111">[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) </span><span class="sxs-lookup"><span data-stu-id="55fab-111">[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) </span></span>  
<span data-ttu-id="55fab-112"> [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)</span><span class="sxs-lookup"><span data-stu-id="55fab-112"> [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)</span></span>
