---
title: Como declarar eventos personalizados para evitar bloqueio
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: 8d73d9c4590afb33e7176f647069cafcb3a9d7d8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345141"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="32d2c-102">Como declarar eventos personalizados para evitar bloqueio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32d2c-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="32d2c-103">Há várias circunstâncias em que é importante que um manipulador de eventos não bloqueie os manipuladores de eventos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="32d2c-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="32d2c-104">Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="32d2c-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="32d2c-105">Por padrão, o campo de armazenamento de backup para uma declaração de evento é um delegado de multicast que combina em série todos os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="32d2c-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="32d2c-106">Isso significa que, se um manipulador levar muito tempo para ser concluído, ele bloqueará os outros manipuladores até que seja concluído.</span><span class="sxs-lookup"><span data-stu-id="32d2c-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="32d2c-107">(Manipuladores de eventos bem comparados nunca devem executar operações demoradas ou potencialmente bloqueadas.)</span><span class="sxs-lookup"><span data-stu-id="32d2c-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="32d2c-108">Em vez de usar a implementação padrão de eventos que Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="32d2c-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32d2c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32d2c-109">Example</span></span>  
 <span data-ttu-id="32d2c-110">Neste exemplo, o acessador `AddHandler` adiciona o delegado para cada manipulador do evento `Click` a um <xref:System.Collections.ArrayList> armazenado no campo `EventHandlerList`.</span><span class="sxs-lookup"><span data-stu-id="32d2c-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="32d2c-111">Quando o código gera o evento `Click`, o acessador `RaiseEvent` invoca todos os delegados do manipulador de eventos de forma assíncrona usando o método <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="32d2c-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="32d2c-112">Esse método invoca cada manipulador em um thread de trabalho e retorna imediatamente, portanto, os manipuladores não podem bloquear um ao outro.</span><span class="sxs-lookup"><span data-stu-id="32d2c-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="32d2c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32d2c-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="32d2c-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="32d2c-114">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="32d2c-115">Como declarar eventos personalizados para conservar memória</span><span class="sxs-lookup"><span data-stu-id="32d2c-115">How to: Declare Custom Events To Conserve Memory</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
