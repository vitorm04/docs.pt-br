---
title: O evento '<eventname1>' não pode implementar o evento '<eventname2>' na interface '<interface>' porque seus tipos delegados '<delegate1>' e '<delegate2>' não correspondem.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 9581168fa86f8f0715e004b60c2eb2a813cd38ab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840517"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="f6f9e-102">Evento '\<eventname1 >' não pode implementar o evento '\<eventname2 >' na interface '\<interface >' porque seus tipos delegados\<delegate1 >' e '\<delegate2 >' não coincidem</span><span class="sxs-lookup"><span data-stu-id="f6f9e-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="f6f9e-103">Visual Basic não pode implementar um evento porque o tipo de delegado do evento não corresponde ao tipo de delegado do evento na interface.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="f6f9e-104">Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá-los junto com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="f6f9e-105">Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando a `As` sintaxe e especifique o mesmo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="f6f9e-106">**ID do erro:** BC31423</span><span class="sxs-lookup"><span data-stu-id="f6f9e-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6f9e-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f6f9e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f6f9e-108">Implemente os eventos separadamente.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="f6f9e-109">—ou—</span><span class="sxs-lookup"><span data-stu-id="f6f9e-109">—or—</span></span>  
  
-   <span data-ttu-id="f6f9e-110">Defina os eventos na interface usando o `As` sintaxe e especifique o mesmo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="f6f9e-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f9e-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6f9e-111">See also</span></span>

- [<span data-ttu-id="f6f9e-112">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="f6f9e-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="f6f9e-113">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="f6f9e-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="f6f9e-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="f6f9e-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
