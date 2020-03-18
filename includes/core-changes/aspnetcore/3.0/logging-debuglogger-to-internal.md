---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393998"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="525d8-101">Registro: Classe DebugLogger feita internamente</span><span class="sxs-lookup"><span data-stu-id="525d8-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="525d8-102">Antes de ASP.NET Núcleo `DebugLogger`3.0, o `public`modificador de acesso era .</span><span class="sxs-lookup"><span data-stu-id="525d8-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="525d8-103">Em ASP.NET Núcleo 3.0, o `internal`modificador de acesso mudou para .</span><span class="sxs-lookup"><span data-stu-id="525d8-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="525d8-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="525d8-104">Version introduced</span></span>

<span data-ttu-id="525d8-105">3.0</span><span class="sxs-lookup"><span data-stu-id="525d8-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="525d8-106">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="525d8-106">Reason for change</span></span>

<span data-ttu-id="525d8-107">A mudança está sendo feita para:</span><span class="sxs-lookup"><span data-stu-id="525d8-107">The change is being made to:</span></span>

* <span data-ttu-id="525d8-108">Impor consistência com outras implementações `ConsoleLogger`de madeireiros, tais como .</span><span class="sxs-lookup"><span data-stu-id="525d8-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="525d8-109">Reduza a superfície da API.</span><span class="sxs-lookup"><span data-stu-id="525d8-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="525d8-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="525d8-110">Recommended action</span></span>

<span data-ttu-id="525d8-111">Use <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` o método de extensão para permitir o registro de depuração.</span><span class="sxs-lookup"><span data-stu-id="525d8-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="525d8-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>também está `public` ainda no caso de o serviço precisar ser registrado manualmente.</span><span class="sxs-lookup"><span data-stu-id="525d8-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="525d8-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="525d8-113">Category</span></span>

<span data-ttu-id="525d8-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="525d8-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="525d8-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="525d8-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
