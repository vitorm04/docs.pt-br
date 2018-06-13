---
title: Como acionar e consumir eventos
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efeed61c5748a0a6ac731cdcfce1a110982b2941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572717"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="3b875-102">Como acionar e consumir eventos</span><span class="sxs-lookup"><span data-stu-id="3b875-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="3b875-103">Os exemplos neste tópico mostram como trabalhar com eventos.</span><span class="sxs-lookup"><span data-stu-id="3b875-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="3b875-104">Elas incluem exemplos do representante <xref:System.EventHandler>, o representante <xref:System.EventHandler%601> e um representante personalizado, para ilustrar eventos com e sem dados.</span><span class="sxs-lookup"><span data-stu-id="3b875-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="3b875-105">Os exemplos usam conceitos descritos no artigo [Eventos](../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b875-105">The examples use concepts described in the [Events](../../../docs/standard/events/index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b875-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b875-106">Example</span></span>  
 <span data-ttu-id="3b875-107">O primeiro exemplo mostra como gerar e consumir um evento que não tem dados.</span><span class="sxs-lookup"><span data-stu-id="3b875-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="3b875-108">Ele contém uma classe denominada `Counter` que tem um evento chamado `ThresholdReached`.</span><span class="sxs-lookup"><span data-stu-id="3b875-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="3b875-109">Esse evento é gerado quando um valor de contador é igual ou maior que um valor de limite.</span><span class="sxs-lookup"><span data-stu-id="3b875-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="3b875-110">O representante <xref:System.EventHandler> é associado ao evento, porque nenhum dado de evento é fornecido.</span><span class="sxs-lookup"><span data-stu-id="3b875-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="3b875-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b875-111">Example</span></span>  
 <span data-ttu-id="3b875-112">O exemplo a seguir mostra como gerar e consumir um evento que fornece dados.</span><span class="sxs-lookup"><span data-stu-id="3b875-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="3b875-113">O representante <xref:System.EventHandler%601> é associado ao evento e uma instância de um objeto de dados de evento personalizado é fornecida.</span><span class="sxs-lookup"><span data-stu-id="3b875-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="3b875-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3b875-114">Example</span></span>  
 <span data-ttu-id="3b875-115">O exemplo a seguir mostra como declarar um representante para um evento.</span><span class="sxs-lookup"><span data-stu-id="3b875-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="3b875-116">O representante é chamado `ThresholdReachedEventHandler`.</span><span class="sxs-lookup"><span data-stu-id="3b875-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="3b875-117">Isso é apenas uma ilustração.</span><span class="sxs-lookup"><span data-stu-id="3b875-117">This is just an illustration.</span></span> <span data-ttu-id="3b875-118">Normalmente, você não precisa declarar um representante para um evento, porque pode usar o representante <xref:System.EventHandler> ou <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="3b875-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="3b875-119">Você deve declarar um representante somente em cenários raros, como tornar a classe disponível para o código herdado que não pode usar genéricos.</span><span class="sxs-lookup"><span data-stu-id="3b875-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="3b875-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b875-120">See Also</span></span>  
 [<span data-ttu-id="3b875-121">Eventos</span><span class="sxs-lookup"><span data-stu-id="3b875-121">Events</span></span>](../../../docs/standard/events/index.md)
