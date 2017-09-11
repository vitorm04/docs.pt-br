---
title: 'Como: declarar eventos personalizados para evitar bloqueio (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
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
ms.openlocfilehash: 52181d1c307e4e312f4511719e540fd6d5bfcfa8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="6dca1-102">Como declarar eventos personalizados para evitar bloqueio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6dca1-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="6dca1-103">Há várias circunstâncias quando é importante que um manipulador de eventos não bloqueie os manipuladores de eventos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="6dca1-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="6dca1-104">Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6dca1-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="6dca1-105">Por padrão, o campo de armazenamento de backup para uma declaração de evento é um delegado multicast que serialmente combina todos os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="6dca1-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="6dca1-106">Isso significa que, se um manipulador levar muito tempo para concluir, ele bloqueia os outros manipuladores até que ela seja concluída.</span><span class="sxs-lookup"><span data-stu-id="6dca1-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="6dca1-107">(Os manipuladores de eventos bem comportados nunca devem executar operações longas ou possivelmente de bloqueio.)</span><span class="sxs-lookup"><span data-stu-id="6dca1-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="6dca1-108">Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6dca1-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dca1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6dca1-109">Example</span></span>  
 <span data-ttu-id="6dca1-110">Neste exemplo, o `AddHandler` acessador adiciona o representante para cada manipulador do `Click` evento para um <xref:System.Collections.ArrayList>armazenados no `EventHandlerList` campo.</xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="6dca1-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="6dca1-111">Quando o código dispara o `Click` evento, o `RaiseEvent` acessador chama todos os representantes de manipulador de eventos usando de forma assíncrona o <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>método.</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="6dca1-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="6dca1-112">Esse método chama cada manipulador em um thread de trabalho e retorna imediatamente, portanto, manipuladores não podem bloquear um ao outro.</span><span class="sxs-lookup"><span data-stu-id="6dca1-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 <span data-ttu-id="6dca1-113">[!code-vb[VbVbalrEvents&#27;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6dca1-113">[!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dca1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dca1-114">See Also</span></span>  
 <span data-ttu-id="6dca1-115"><xref:System.Collections.ArrayList></xref:System.Collections.ArrayList></span><span class="sxs-lookup"><span data-stu-id="6dca1-115"><xref:System.Collections.ArrayList></span></span>   
 <span data-ttu-id="6dca1-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span><span class="sxs-lookup"><span data-stu-id="6dca1-116"><xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></span></span>   
<span data-ttu-id="6dca1-117"> [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="6dca1-117"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="6dca1-118"> [Como declarar eventos personalizados para conservar memória](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span><span class="sxs-lookup"><span data-stu-id="6dca1-118"> [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)</span></span>
