---
ms.openlocfilehash: 99a7fa0fcfce6d490a182f85709b5dd0e0e8c86f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497051"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="edc46-101">EventSource.WriteEvent deve passar a WriteEvent os mesmos parâmetros que recebeu (mais ID)</span><span class="sxs-lookup"><span data-stu-id="edc46-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="edc46-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="edc46-102">Details</span></span>

<span data-ttu-id="edc46-103">O runtime agora impõe o contrato que especifica o seguinte: uma classe derivada de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> que define um método de evento ETW deve chamar o método de classe base <code>EventSource.WriteEvent</code> com a ID do evento seguido dos mesmos argumentos que o método de evento ETW passou.</span><span class="sxs-lookup"><span data-stu-id="edc46-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="edc46-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="edc46-104">Suggestion</span></span>

<span data-ttu-id="edc46-105">Uma exceção <xref:System.IndexOutOfRangeException?displayProperty=fullName> será acionada se um <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> ler dados <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> no processo de uma origem de evento que viola esse contrato.</span><span class="sxs-lookup"><span data-stu-id="edc46-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="edc46-106">Nome</span><span class="sxs-lookup"><span data-stu-id="edc46-106">Name</span></span>    | <span data-ttu-id="edc46-107">Valor</span><span class="sxs-lookup"><span data-stu-id="edc46-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="edc46-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="edc46-108">Scope</span></span>   |<span data-ttu-id="edc46-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="edc46-109">Minor</span></span>|
|<span data-ttu-id="edc46-110">Versão</span><span class="sxs-lookup"><span data-stu-id="edc46-110">Version</span></span>|<span data-ttu-id="edc46-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="edc46-111">4.5.1</span></span>|
|<span data-ttu-id="edc46-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="edc46-112">Type</span></span>|<span data-ttu-id="edc46-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="edc46-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="edc46-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="edc46-114">Affected APIs</span></span>

<span data-ttu-id="edc46-115">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="edc46-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
