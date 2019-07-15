---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804612"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="589f9-101">Nomes de evento ETW não podem ser diferentes apenas por um sufixo "Start" ou "Stop"</span><span class="sxs-lookup"><span data-stu-id="589f9-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="589f9-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="589f9-102">Details</span></span>|<span data-ttu-id="589f9-103">No .NET Framework 4.6 e 4.6.1, o tempo de execução gera uma <xref:System.ArgumentException> quando dois nomes de evento ETW (Rastreamento de Eventos para Windows) diferem somente por um sufixo &quot;Start&quot; ou &quot;Stop&quot; (como quando um evento é denominado <code>LogUser</code> e outro é denominado <code>LogUserStart</code>).</span><span class="sxs-lookup"><span data-stu-id="589f9-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="589f9-104">Nesse caso, o tempo de execução não pode construir a origem do evento, que não pode emitir nenhum log.</span><span class="sxs-lookup"><span data-stu-id="589f9-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="589f9-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="589f9-105">Suggestion</span></span>|<span data-ttu-id="589f9-106">Para evitar a exceção, certifique-se de que nenhum dos dois nomes de eventos difiram somente por um sufixo &quot;Start&quot; ou &quot;Stop&quot;. Esse requisito foi removido a partir do .NET Framework 4.6.2. O tempo de execução pode resolver a ambiguidade de nomes de evento que diferem somente pelos sufixos &quot;Start&quot; e &quot;Stop&quot;.</span><span class="sxs-lookup"><span data-stu-id="589f9-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="589f9-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="589f9-107">Scope</span></span>|<span data-ttu-id="589f9-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="589f9-108">Edge</span></span>|
|<span data-ttu-id="589f9-109">Versão</span><span class="sxs-lookup"><span data-stu-id="589f9-109">Version</span></span>|<span data-ttu-id="589f9-110">4.6</span><span class="sxs-lookup"><span data-stu-id="589f9-110">4.6</span></span>|
|<span data-ttu-id="589f9-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="589f9-111">Type</span></span>|<span data-ttu-id="589f9-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="589f9-112">Retargeting</span></span>|

