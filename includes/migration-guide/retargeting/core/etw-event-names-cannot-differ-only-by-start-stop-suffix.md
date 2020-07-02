---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614276"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="e6160-101">Nomes de evento ETW não podem ser diferentes apenas por um sufixo "Start" ou "Stop"</span><span class="sxs-lookup"><span data-stu-id="e6160-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="e6160-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e6160-102">Details</span></span>

<span data-ttu-id="e6160-103">No .NET Framework 4,6 e 4.6.1, o tempo de execução gera um <xref:System.ArgumentException> quando dois nomes de evento ETW (rastreamento de eventos para Windows) diferem apenas por um sufixo "Start" ou "Stop" (como quando um evento é nomeado `LogUser` e outro é nomeado `LogUserStart` ).</span><span class="sxs-lookup"><span data-stu-id="e6160-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="e6160-104">Nesse caso, o runtime não pode construir a origem do evento, que não pode emitir nenhum log.</span><span class="sxs-lookup"><span data-stu-id="e6160-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e6160-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e6160-105">Suggestion</span></span>

<span data-ttu-id="e6160-106">Para evitar a exceção, verifique se nenhum nome de dois eventos difere apenas por um sufixo "Start" ou "Stop". Esse requisito é removido começando com o .NET Framework 4.6.2; o tempo de execução pode desambiguar nomes de eventos que diferem apenas pelo sufixo "Start" e "Stop".</span><span class="sxs-lookup"><span data-stu-id="e6160-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="e6160-107">Name</span><span class="sxs-lookup"><span data-stu-id="e6160-107">Name</span></span>    | <span data-ttu-id="e6160-108">Valor</span><span class="sxs-lookup"><span data-stu-id="e6160-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e6160-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="e6160-109">Scope</span></span>   | <span data-ttu-id="e6160-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e6160-110">Edge</span></span>        |
| <span data-ttu-id="e6160-111">Versão</span><span class="sxs-lookup"><span data-stu-id="e6160-111">Version</span></span> | <span data-ttu-id="e6160-112">4.6</span><span class="sxs-lookup"><span data-stu-id="e6160-112">4.6</span></span>         |
| <span data-ttu-id="e6160-113">Type</span><span class="sxs-lookup"><span data-stu-id="e6160-113">Type</span></span>    | <span data-ttu-id="e6160-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="e6160-114">Retargeting</span></span> |
