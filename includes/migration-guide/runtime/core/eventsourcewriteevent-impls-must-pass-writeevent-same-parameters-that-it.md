---
ms.openlocfilehash: 47d0aa554d88726caca35fa6bebe4d863fdc0695
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803174"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="46e52-101">EventSource.WriteEvent deve passar a WriteEvent os mesmos parâmetros que recebeu (mais ID)</span><span class="sxs-lookup"><span data-stu-id="46e52-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="46e52-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="46e52-102">Details</span></span>|<span data-ttu-id="46e52-103">O tempo de execução agora aplica o contrato que especifica o seguinte: Uma classe derivada de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> que define um método de evento ETW deve chamar o método de classe base <code>EventSource.WriteEvent</code> com a ID do evento seguido dos mesmos argumentos que o método de evento ETW passou.</span><span class="sxs-lookup"><span data-stu-id="46e52-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>|
|<span data-ttu-id="46e52-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="46e52-104">Suggestion</span></span>|<span data-ttu-id="46e52-105">Uma exceção <xref:System.IndexOutOfRangeException?displayProperty=name> será acionada se um <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> ler dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> no processo de uma origem de evento que viola esse contrato.</span><span class="sxs-lookup"><span data-stu-id="46e52-105">An <xref:System.IndexOutOfRangeException?displayProperty=name> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=name> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=name> data in process for an event source that violates this contract.</span></span>|
|<span data-ttu-id="46e52-106">Escopo</span><span class="sxs-lookup"><span data-stu-id="46e52-106">Scope</span></span>|<span data-ttu-id="46e52-107">Secundário</span><span class="sxs-lookup"><span data-stu-id="46e52-107">Minor</span></span>|
|<span data-ttu-id="46e52-108">Versão</span><span class="sxs-lookup"><span data-stu-id="46e52-108">Version</span></span>|<span data-ttu-id="46e52-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="46e52-109">4.5.1</span></span>|
|<span data-ttu-id="46e52-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="46e52-110">Type</span></span>|<span data-ttu-id="46e52-111">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="46e52-111">Runtime</span></span>|
