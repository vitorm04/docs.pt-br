---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608474"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="d4508-101">WinHttpHandler removido do tempo de execução do .NET</span><span class="sxs-lookup"><span data-stu-id="d4508-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="d4508-102">A `WinHttpHandler` classe foi removida do assembly *System.Net.Http.dll* .</span><span class="sxs-lookup"><span data-stu-id="d4508-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="d4508-103">Agora, ele está disponível apenas como um [pacote NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)fora de banda (OOB).</span><span class="sxs-lookup"><span data-stu-id="d4508-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d4508-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d4508-104">Version introduced</span></span>

<span data-ttu-id="d4508-105">5.0</span><span class="sxs-lookup"><span data-stu-id="d4508-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="d4508-106">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="d4508-106">Change description</span></span>

<span data-ttu-id="d4508-107">Nas versões anteriores do .NET, a <xref:System.Net.Http.WinHttpHandler> classe está disponível como parte das principais bibliotecas do .net.</span><span class="sxs-lookup"><span data-stu-id="d4508-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="d4508-108">A partir do .NET 5,0, a <xref:System.Net.Http.WinHttpHandler> classe só está disponível como um [pacote NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)instalado separadamente.</span><span class="sxs-lookup"><span data-stu-id="d4508-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d4508-109">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d4508-109">Recommended action</span></span>

<span data-ttu-id="d4508-110">Instale o [pacote NuGet System .net. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="d4508-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="d4508-111">Ou, se você não precisar de recursos específicos do WinHTTP, use <xref:System.Net.Http.SocketsHttpHandler> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d4508-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="d4508-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="d4508-112">Category</span></span>

<span data-ttu-id="d4508-113">Rede</span><span class="sxs-lookup"><span data-stu-id="d4508-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d4508-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d4508-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
