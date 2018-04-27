---
title: Evento &#39; &lt;eventname1&gt; &#39; não pode implementar o evento &#39; &lt;eventname2&gt; &#39; na interface &#39; &lt;interface&gt; &#39; porque seus tipos delegados &#39; &lt;delegate1&gt; &#39; e &#39; &lt;delegate2&gt; &#39; não coincidem
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41f5984458eb17db04f20b292a0d80783093dcb4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="b3076-102">Evento &#39; &lt;eventname1&gt; &#39; não pode implementar o evento &#39; &lt;eventname2&gt; &#39; na interface &#39; &lt;interface&gt; &#39; porque seus tipos delegados &#39; &lt;delegate1&gt; &#39; e &#39; &lt;delegate2&gt; &#39; não coincidem</span><span class="sxs-lookup"><span data-stu-id="b3076-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="b3076-103">Visual Basic não pode implementar um evento porque o tipo delegado do evento não corresponde ao tipo delegado do evento na interface.</span><span class="sxs-lookup"><span data-stu-id="b3076-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="b3076-104">Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá-las em conjunto com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="b3076-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="b3076-105">Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando o `As` sintaxe e especifique o mesmo tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="b3076-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="b3076-106">**ID do erro:** BC31423</span><span class="sxs-lookup"><span data-stu-id="b3076-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3076-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b3076-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b3076-108">Implemente os eventos separadamente.</span><span class="sxs-lookup"><span data-stu-id="b3076-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="b3076-109">—ou—</span><span class="sxs-lookup"><span data-stu-id="b3076-109">—or—</span></span>  
  
-   <span data-ttu-id="b3076-110">Defina os eventos na interface usando o `As` sintaxe e especifique o mesmo tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="b3076-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3076-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3076-111">See Also</span></span>  
 [<span data-ttu-id="b3076-112">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="b3076-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="b3076-113">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="b3076-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="b3076-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="b3076-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
