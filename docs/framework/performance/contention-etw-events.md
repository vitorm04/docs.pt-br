---
title: Eventos ETW de contenção-.NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716129"
---
# <a name="contention-etw-events"></a><span data-ttu-id="8a2b9-102">Eventos ETW de contenção</span><span class="sxs-lookup"><span data-stu-id="8a2b9-102">Contention ETW events</span></span>

<span data-ttu-id="8a2b9-103">Eventos de contenção são acionados sempre que há contenção em bloqueios <xref:System.Threading.Monitor?displayProperty=nameWithType> ou bloqueios nativos usados pelo runtime.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="8a2b9-104">A contenção ocorre quando um thread aguarda um bloqueio, enquanto outro thread possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="8a2b9-105">A tabela a seguir mostra a palavra-chave com a qual os eventos de contenção são acionados, além do nível dos eventos.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="8a2b9-106">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8a2b9-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="8a2b9-107">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="8a2b9-107">Keyword for raising the event</span></span>|<span data-ttu-id="8a2b9-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8a2b9-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="8a2b9-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="8a2b9-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="8a2b9-110">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="8a2b9-110">Informational (4)</span></span>|

<span data-ttu-id="8a2b9-111">A tabela a seguir mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="8a2b9-111">The following table shows event information:</span></span>

|<span data-ttu-id="8a2b9-112">Event</span><span class="sxs-lookup"><span data-stu-id="8a2b9-112">Event</span></span>|<span data-ttu-id="8a2b9-113">ID do evento</span><span class="sxs-lookup"><span data-stu-id="8a2b9-113">Event ID</span></span>|<span data-ttu-id="8a2b9-114">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="8a2b9-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="8a2b9-115">81</span><span class="sxs-lookup"><span data-stu-id="8a2b9-115">81</span></span>|<span data-ttu-id="8a2b9-116">A contenção é iniciada.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-116">Contention starts.</span></span> <span data-ttu-id="8a2b9-117">Esse evento não inclui o tempo de rotação antes que um thread aguarde para adquirir um bloqueio; ele é acionado apenas quando o thread aguarda para adquirir um bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="8a2b9-118">91</span><span class="sxs-lookup"><span data-stu-id="8a2b9-118">91</span></span>|<span data-ttu-id="8a2b9-119">A contenção é encerrada.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-119">Contention ends.</span></span>|

<span data-ttu-id="8a2b9-120">A tabela a seguir mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="8a2b9-120">The following table shows event data:</span></span>

|<span data-ttu-id="8a2b9-121">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="8a2b9-121">Field name</span></span>|<span data-ttu-id="8a2b9-122">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="8a2b9-122">Data type</span></span>|<span data-ttu-id="8a2b9-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a2b9-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="8a2b9-124">Sinalizadores</span><span class="sxs-lookup"><span data-stu-id="8a2b9-124">Flags</span></span>|<span data-ttu-id="8a2b9-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="8a2b9-125">win:UInt8</span></span>|<span data-ttu-id="8a2b9-126">0 para gerenciado; 1 para nativo.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="8a2b9-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8a2b9-127">ClrInstanceID</span></span>|<span data-ttu-id="8a2b9-128">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="8a2b9-128">win:UInt16</span></span>|<span data-ttu-id="8a2b9-129">ID exclusiva da instância do CLR.</span><span class="sxs-lookup"><span data-stu-id="8a2b9-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8a2b9-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="8a2b9-130">See also</span></span>

- [<span data-ttu-id="8a2b9-131">Eventos de CLR ETW</span><span class="sxs-lookup"><span data-stu-id="8a2b9-131">CLR ETW Events</span></span>](clr-etw-events.md)
