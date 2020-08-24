---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393998"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="c5aa7-101">Log: classe DebugLogger criada internamente</span><span class="sxs-lookup"><span data-stu-id="c5aa7-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="c5aa7-102">Antes do ASP.NET Core 3,0, o `DebugLogger` modificador de acesso foi `public` .</span><span class="sxs-lookup"><span data-stu-id="c5aa7-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="c5aa7-103">No ASP.NET Core 3,0, o modificador de acesso foi alterado para `internal` .</span><span class="sxs-lookup"><span data-stu-id="c5aa7-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c5aa7-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c5aa7-104">Version introduced</span></span>

<span data-ttu-id="c5aa7-105">3,0</span><span class="sxs-lookup"><span data-stu-id="c5aa7-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c5aa7-106">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="c5aa7-106">Reason for change</span></span>

<span data-ttu-id="c5aa7-107">A alteração está sendo feita para:</span><span class="sxs-lookup"><span data-stu-id="c5aa7-107">The change is being made to:</span></span>

* <span data-ttu-id="c5aa7-108">Impor consistência com outras implementações de agente, como `ConsoleLogger` .</span><span class="sxs-lookup"><span data-stu-id="c5aa7-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="c5aa7-109">Reduza a superfície da API.</span><span class="sxs-lookup"><span data-stu-id="c5aa7-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5aa7-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c5aa7-110">Recommended action</span></span>

<span data-ttu-id="c5aa7-111">Use o <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` método de extensão para habilitar o log de depuração.</span><span class="sxs-lookup"><span data-stu-id="c5aa7-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="c5aa7-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> também é ainda `public` no caso de o serviço precisar ser registrado manualmente.</span><span class="sxs-lookup"><span data-stu-id="c5aa7-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="c5aa7-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="c5aa7-113">Category</span></span>

<span data-ttu-id="c5aa7-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c5aa7-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5aa7-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c5aa7-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
