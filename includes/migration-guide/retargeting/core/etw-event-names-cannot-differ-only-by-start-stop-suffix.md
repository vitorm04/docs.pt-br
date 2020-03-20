---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804612"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="fe440-101">Nomes de evento ETW não podem ser diferentes apenas por um sufixo "Start" ou "Stop"</span><span class="sxs-lookup"><span data-stu-id="fe440-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fe440-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fe440-102">Details</span></span>|<span data-ttu-id="fe440-103">No .NET Framework 4.6 e 4.6.1, o runtime gera uma <xref:System.ArgumentException> quando dois nomes de evento ETW (Rastreamento de Eventos para Windows) diferem somente por um sufixo &quot;Start&quot; ou &quot;Stop&quot; (como quando um evento é denominado <code>LogUser</code> e outro é denominado <code>LogUserStart</code>).</span><span class="sxs-lookup"><span data-stu-id="fe440-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix (as when one event is named <code>LogUser</code> and another is named <code>LogUserStart</code>).</span></span> <span data-ttu-id="fe440-104">Nesse caso, o runtime não pode construir a origem do evento, que não pode emitir nenhum log.</span><span class="sxs-lookup"><span data-stu-id="fe440-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>|
|<span data-ttu-id="fe440-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fe440-105">Suggestion</span></span>|<span data-ttu-id="fe440-106">Para evitar a exceção, certifique-se de que nenhum dos dois nomes de eventos difiram somente por um sufixo &quot;Start&quot; ou &quot;Stop&quot;. Esse requisito foi removido a partir do .NET Framework 4.6.2. O runtime pode resolver a ambiguidade de nomes de evento que diferem somente pelos sufixos &quot;Start&quot; e &quot;Stop&quot;.</span><span class="sxs-lookup"><span data-stu-id="fe440-106">To prevent the exception, ensure that no two event names differ only by a &quot;Start&quot; or &quot;Stop&quot; suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the &quot;Start&quot; and &quot;Stop&quot; suffix.</span></span>|
|<span data-ttu-id="fe440-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="fe440-107">Scope</span></span>|<span data-ttu-id="fe440-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fe440-108">Edge</span></span>|
|<span data-ttu-id="fe440-109">Versão</span><span class="sxs-lookup"><span data-stu-id="fe440-109">Version</span></span>|<span data-ttu-id="fe440-110">4.6</span><span class="sxs-lookup"><span data-stu-id="fe440-110">4.6</span></span>|
|<span data-ttu-id="fe440-111">Type</span><span class="sxs-lookup"><span data-stu-id="fe440-111">Type</span></span>|<span data-ttu-id="fe440-112">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="fe440-112">Retargeting</span></span>|
