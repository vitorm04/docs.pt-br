---
title: Como declarar eventos personalizados para evitar bloqueio (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="34477-102">Como declarar eventos personalizados para evitar bloqueio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34477-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="34477-103">Há várias circunstâncias quando é importante que um manipulador de eventos não bloquear manipuladores de eventos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="34477-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="34477-104">Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="34477-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="34477-105">Por padrão, o campo de repositório de backup para uma declaração de evento é um delegado multicast que serialmente combina todos os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="34477-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="34477-106">Isso significa que, se um manipulador levar muito tempo para concluir, ele bloqueia os outros manipuladores até que ela seja concluída.</span><span class="sxs-lookup"><span data-stu-id="34477-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="34477-107">(Manipuladores de eventos bem comportados nunca devem executar operações longas ou possivelmente de bloqueio.)</span><span class="sxs-lookup"><span data-stu-id="34477-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="34477-108">Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="34477-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34477-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34477-109">Example</span></span>  
 <span data-ttu-id="34477-110">Neste exemplo, o `AddHandler` acessador adiciona o representante para cada manipulador do `Click` evento para um <xref:System.Collections.ArrayList> armazenados no `EventHandlerList` campo.</span><span class="sxs-lookup"><span data-stu-id="34477-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="34477-111">Quando o código dispara o `Click` evento, o `RaiseEvent` acessador chama todos os representantes de manipulador de eventos usando de forma assíncrona o <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> método.</span><span class="sxs-lookup"><span data-stu-id="34477-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="34477-112">Esse método chama cada manipulador em um thread de trabalho e retorna imediatamente, portanto manipuladores não é possível bloquear um ao outro.</span><span class="sxs-lookup"><span data-stu-id="34477-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="34477-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34477-113">See Also</span></span>  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [<span data-ttu-id="34477-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="34477-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="34477-115">Como declarar eventos personalizados para conservar memória</span><span class="sxs-lookup"><span data-stu-id="34477-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
