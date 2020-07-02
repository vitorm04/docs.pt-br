---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614271"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="fdcab-101">Limitação de solicitações simultâneas por sessão</span><span class="sxs-lookup"><span data-stu-id="fdcab-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="fdcab-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fdcab-102">Details</span></span>

<span data-ttu-id="fdcab-103">No .NET Framework 4.6.2 e versões anteriores, o ASP.NET executa solicitações com a mesma Sessionid sequencialmente e sempre emite a Sessionid por meio de um cookie por padrão.</span><span class="sxs-lookup"><span data-stu-id="fdcab-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="fdcab-104">Se uma página demorar muito tempo para responder, isso degradará significativamente o desempenho do servidor, pressionando <kbd>F5</kbd> no navegador.</span><span class="sxs-lookup"><span data-stu-id="fdcab-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="fdcab-105">Na correção, adicionou-se um contador que acompanha as solicitações enfileiradas e encerra as solicitações quando elas excedem um limite especificado.</span><span class="sxs-lookup"><span data-stu-id="fdcab-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="fdcab-106">O valor padrão é 50.</span><span class="sxs-lookup"><span data-stu-id="fdcab-106">The default value is 50.</span></span> <span data-ttu-id="fdcab-107">Se o limite for alcançado, um aviso será registrado no log de eventos e uma resposta HTTP 500 poderá ser registrada no log do IIS.</span><span class="sxs-lookup"><span data-stu-id="fdcab-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fdcab-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fdcab-108">Suggestion</span></span>

<span data-ttu-id="fdcab-109">Para restaurar o comportamento antigo, você pode adicionar a seguinte configuração ao arquivo web.config para recusar o novo comportamento.</span><span class="sxs-lookup"><span data-stu-id="fdcab-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="fdcab-110">Name</span><span class="sxs-lookup"><span data-stu-id="fdcab-110">Name</span></span>    | <span data-ttu-id="fdcab-111">Valor</span><span class="sxs-lookup"><span data-stu-id="fdcab-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fdcab-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="fdcab-112">Scope</span></span>   | <span data-ttu-id="fdcab-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fdcab-113">Edge</span></span>        |
| <span data-ttu-id="fdcab-114">Versão</span><span class="sxs-lookup"><span data-stu-id="fdcab-114">Version</span></span> | <span data-ttu-id="fdcab-115">4.7</span><span class="sxs-lookup"><span data-stu-id="fdcab-115">4.7</span></span>         |
| <span data-ttu-id="fdcab-116">Type</span><span class="sxs-lookup"><span data-stu-id="fdcab-116">Type</span></span>    | <span data-ttu-id="fdcab-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="fdcab-117">Retargeting</span></span> |
