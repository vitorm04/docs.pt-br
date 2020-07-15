---
title: Eventos ETW de contenção-.NET
description: Obtenha detalhes sobre os eventos ETW de contenção, que são gerados sempre que há contenção para System. Threading. monitor Locks ou bloqueios nativos usados pelo tempo de execução.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309593"
---
# <a name="contention-etw-events"></a><span data-ttu-id="c33b3-103">Eventos ETW de contenção</span><span class="sxs-lookup"><span data-stu-id="c33b3-103">Contention ETW events</span></span>

<span data-ttu-id="c33b3-104">Eventos de contenção são acionados sempre que há contenção em bloqueios <xref:System.Threading.Monitor?displayProperty=nameWithType> ou bloqueios nativos usados pelo runtime.</span><span class="sxs-lookup"><span data-stu-id="c33b3-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="c33b3-105">A contenção ocorre quando um thread aguarda um bloqueio, enquanto outro thread possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c33b3-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="c33b3-106">A tabela a seguir mostra a palavra-chave com a qual os eventos de contenção são acionados, além do nível dos eventos.</span><span class="sxs-lookup"><span data-stu-id="c33b3-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="c33b3-107">Para obter mais informações, consulte [palavras-chave e níveis do ETW do CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c33b3-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="c33b3-108">Palavra-chave para acionar o evento</span><span class="sxs-lookup"><span data-stu-id="c33b3-108">Keyword for raising the event</span></span>|<span data-ttu-id="c33b3-109">Level</span><span class="sxs-lookup"><span data-stu-id="c33b3-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c33b3-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="c33b3-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="c33b3-111">Informativo (4)</span><span class="sxs-lookup"><span data-stu-id="c33b3-111">Informational (4)</span></span>|

<span data-ttu-id="c33b3-112">A tabela a seguir mostra as informações do evento:</span><span class="sxs-lookup"><span data-stu-id="c33b3-112">The following table shows event information:</span></span>

|<span data-ttu-id="c33b3-113">Evento</span><span class="sxs-lookup"><span data-stu-id="c33b3-113">Event</span></span>|<span data-ttu-id="c33b3-114">ID do evento</span><span class="sxs-lookup"><span data-stu-id="c33b3-114">Event ID</span></span>|<span data-ttu-id="c33b3-115">Acionado quando</span><span class="sxs-lookup"><span data-stu-id="c33b3-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="c33b3-116">81</span><span class="sxs-lookup"><span data-stu-id="c33b3-116">81</span></span>|<span data-ttu-id="c33b3-117">A contenção é iniciada.</span><span class="sxs-lookup"><span data-stu-id="c33b3-117">Contention starts.</span></span> <span data-ttu-id="c33b3-118">Esse evento não inclui o tempo de rotação antes que um thread aguarde para adquirir um bloqueio; ele é acionado apenas quando o thread aguarda para adquirir um bloqueio.</span><span class="sxs-lookup"><span data-stu-id="c33b3-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="c33b3-119">91</span><span class="sxs-lookup"><span data-stu-id="c33b3-119">91</span></span>|<span data-ttu-id="c33b3-120">A contenção é encerrada.</span><span class="sxs-lookup"><span data-stu-id="c33b3-120">Contention ends.</span></span>|

<span data-ttu-id="c33b3-121">A tabela a seguir mostra os dados do evento:</span><span class="sxs-lookup"><span data-stu-id="c33b3-121">The following table shows event data:</span></span>

|<span data-ttu-id="c33b3-122">Nome do campo</span><span class="sxs-lookup"><span data-stu-id="c33b3-122">Field name</span></span>|<span data-ttu-id="c33b3-123">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c33b3-123">Data type</span></span>|<span data-ttu-id="c33b3-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c33b3-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c33b3-125">Flags</span><span class="sxs-lookup"><span data-stu-id="c33b3-125">Flags</span></span>|<span data-ttu-id="c33b3-126">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="c33b3-126">win:UInt8</span></span>|<span data-ttu-id="c33b3-127">0 para gerenciado; 1 para nativo.</span><span class="sxs-lookup"><span data-stu-id="c33b3-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="c33b3-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c33b3-128">ClrInstanceID</span></span>|<span data-ttu-id="c33b3-129">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c33b3-129">win:UInt16</span></span>|<span data-ttu-id="c33b3-130">ID exclusiva da instância do CLR.</span><span class="sxs-lookup"><span data-stu-id="c33b3-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c33b3-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="c33b3-131">See also</span></span>

- [<span data-ttu-id="c33b3-132">Eventos ETW no CLR</span><span class="sxs-lookup"><span data-stu-id="c33b3-132">CLR ETW Events</span></span>](clr-etw-events.md)
