---
title: O evento '<eventname1>' não pode implementar o evento '<eventname2>' na interface '<interface>' porque seus tipos delegados '<delegate1>' e '<delegate2>' não correspondem.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 32d6733580de8798a66c30d486b8439befd2af19
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409602"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="1e37b-102">O evento '\<eventname1>' não pode implementar o evento '\<eventname2>' na interface '\<interface>' porque seus tipos delegados '\<delegate1>' e '\<delegate2>' não correspondem.</span><span class="sxs-lookup"><span data-stu-id="1e37b-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="1e37b-103">Visual Basic não pode implementar um evento porque o tipo delegado do evento não corresponde ao tipo delegado do evento na interface.</span><span class="sxs-lookup"><span data-stu-id="1e37b-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="1e37b-104">Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tenta implementá-los junto com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="1e37b-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="1e37b-105">Um evento pode implementar dois ou mais eventos somente se todos os eventos implementados forem declarados usando a `As` sintaxe e especificarem o mesmo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="1e37b-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="1e37b-106">**ID do erro:** BC31423</span><span class="sxs-lookup"><span data-stu-id="1e37b-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e37b-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1e37b-107">To correct this error</span></span>  
  
- <span data-ttu-id="1e37b-108">Implemente os eventos separadamente.</span><span class="sxs-lookup"><span data-stu-id="1e37b-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="1e37b-109">— ou —</span><span class="sxs-lookup"><span data-stu-id="1e37b-109">—or—</span></span>  
  
- <span data-ttu-id="1e37b-110">Defina os eventos na interface usando a `As` sintaxe e especifique o mesmo tipo de delegado.</span><span class="sxs-lookup"><span data-stu-id="1e37b-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e37b-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="1e37b-111">See also</span></span>

- [<span data-ttu-id="1e37b-112">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="1e37b-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="1e37b-113">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="1e37b-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="1e37b-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="1e37b-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
