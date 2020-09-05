---
ms.openlocfilehash: 2b4f35fe15f806897e5e4d85ee774b2e4572d974
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497098"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="d78ee-101">Adaptadores de fluxo do WinRT não chamam mais FlushAsync automaticamente ao fechar</span><span class="sxs-lookup"><span data-stu-id="d78ee-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="d78ee-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d78ee-102">Details</span></span>

<span data-ttu-id="d78ee-103">Em aplicativos da Windows Store, os adaptadores de fluxo do Windows Runtime não chamam mais o método de FlushAsync do método Dispose.</span><span class="sxs-lookup"><span data-stu-id="d78ee-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d78ee-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="d78ee-104">Suggestion</span></span>

<span data-ttu-id="d78ee-105">Essa alteração deve ser transparente.</span><span class="sxs-lookup"><span data-stu-id="d78ee-105">This change should be transparent.</span></span> <span data-ttu-id="d78ee-106">Os desenvolvedores podem restaurar o comportamento anterior gravando um código como este:</span><span class="sxs-lookup"><span data-stu-id="d78ee-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="d78ee-107">Nome</span><span class="sxs-lookup"><span data-stu-id="d78ee-107">Name</span></span>    | <span data-ttu-id="d78ee-108">Valor</span><span class="sxs-lookup"><span data-stu-id="d78ee-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d78ee-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="d78ee-109">Scope</span></span>   |<span data-ttu-id="d78ee-110">Transparente</span><span class="sxs-lookup"><span data-stu-id="d78ee-110">Transparent</span></span>|
|<span data-ttu-id="d78ee-111">Versão</span><span class="sxs-lookup"><span data-stu-id="d78ee-111">Version</span></span>|<span data-ttu-id="d78ee-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d78ee-112">4.5.1</span></span>|
|<span data-ttu-id="d78ee-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="d78ee-113">Type</span></span>|<span data-ttu-id="d78ee-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="d78ee-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d78ee-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d78ee-115">Affected APIs</span></span>

<span data-ttu-id="d78ee-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="d78ee-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
