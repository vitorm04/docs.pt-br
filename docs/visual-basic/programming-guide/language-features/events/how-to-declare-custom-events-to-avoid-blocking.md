---
title: Como declarar eventos personalizados para evitar bloqueio
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405151"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a><span data-ttu-id="38bb1-102">Como declarar eventos personalizados para evitar bloqueio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38bb1-102">How to: Declare Custom Events To Avoid Blocking (Visual Basic)</span></span>
<span data-ttu-id="38bb1-103">Há várias circunstâncias em que é importante que um manipulador de eventos não bloqueie os manipuladores de eventos subsequentes.</span><span class="sxs-lookup"><span data-stu-id="38bb1-103">There are several circumstances when it is important that one event handler not block subsequent event handlers.</span></span> <span data-ttu-id="38bb1-104">Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="38bb1-104">Custom events allow the event to call its event handlers asynchronously.</span></span>  
  
 <span data-ttu-id="38bb1-105">Por padrão, o campo de armazenamento de backup para uma declaração de evento é um delegado de multicast que combina em série todos os manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="38bb1-105">By default, the backing-store field for an event declaration is a multicast delegate that serially combines all the event handlers.</span></span> <span data-ttu-id="38bb1-106">Isso significa que, se um manipulador levar muito tempo para ser concluído, ele bloqueará os outros manipuladores até que seja concluído.</span><span class="sxs-lookup"><span data-stu-id="38bb1-106">This means that if one handler takes a long time to complete, it blocks the other handlers until it completes.</span></span> <span data-ttu-id="38bb1-107">(Manipuladores de eventos bem comparados nunca devem executar operações demoradas ou potencialmente bloqueadas.)</span><span class="sxs-lookup"><span data-stu-id="38bb1-107">(Well-behaved event handlers should never perform lengthy or potentially blocking operations.)</span></span>  
  
 <span data-ttu-id="38bb1-108">Em vez de usar a implementação padrão de eventos que Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="38bb1-108">Instead of using the default implementation of events that Visual Basic provides, you can use a custom event to execute the event handlers asynchronously.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38bb1-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38bb1-109">Example</span></span>  
 <span data-ttu-id="38bb1-110">Neste exemplo, o `AddHandler` acessador adiciona o delegado para cada manipulador do `Click` evento a um <xref:System.Collections.ArrayList> armazenado no `EventHandlerList` campo.</span><span class="sxs-lookup"><span data-stu-id="38bb1-110">In this example, the `AddHandler` accessor adds the delegate for each handler of the `Click` event to an <xref:System.Collections.ArrayList> stored in the `EventHandlerList` field.</span></span>  
  
 <span data-ttu-id="38bb1-111">Quando o código gera o `Click` evento, o `RaiseEvent` acessador invoca todos os delegados do manipulador de eventos de forma assíncrona usando o <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> método.</span><span class="sxs-lookup"><span data-stu-id="38bb1-111">When code raises the `Click` event, the `RaiseEvent` accessor invokes all the event handler delegates asynchronously using the <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> method.</span></span> <span data-ttu-id="38bb1-112">Esse método invoca cada manipulador em um thread de trabalho e retorna imediatamente, portanto, os manipuladores não podem bloquear um ao outro.</span><span class="sxs-lookup"><span data-stu-id="38bb1-112">That method invokes each handler on a worker thread and returns immediately, so handlers cannot block one another.</span></span>  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a><span data-ttu-id="38bb1-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="38bb1-113">See also</span></span>

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [<span data-ttu-id="38bb1-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="38bb1-114">Events</span></span>](index.md)
- [<span data-ttu-id="38bb1-115">Como declarar eventos personalizados para conservar memória</span><span class="sxs-lookup"><span data-stu-id="38bb1-115">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)
