---
ms.openlocfilehash: 60937459b6f18e9abae87ad2dc97c3942325eedc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619789"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="3e14b-101">Adaptadores de fluxo do WinRT não chamam mais FlushAsync automaticamente ao fechar</span><span class="sxs-lookup"><span data-stu-id="3e14b-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

#### <a name="details"></a><span data-ttu-id="3e14b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3e14b-102">Details</span></span>

<span data-ttu-id="3e14b-103">Em aplicativos da Windows Store, os adaptadores de fluxo do Windows Runtime não chamam mais o método de FlushAsync do método Dispose.</span><span class="sxs-lookup"><span data-stu-id="3e14b-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3e14b-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3e14b-104">Suggestion</span></span>

<span data-ttu-id="3e14b-105">Essa alteração deve ser transparente.</span><span class="sxs-lookup"><span data-stu-id="3e14b-105">This change should be transparent.</span></span> <span data-ttu-id="3e14b-106">Os desenvolvedores podem restaurar o comportamento anterior gravando um código como este:</span><span class="sxs-lookup"><span data-stu-id="3e14b-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| <span data-ttu-id="3e14b-107">Name</span><span class="sxs-lookup"><span data-stu-id="3e14b-107">Name</span></span>    | <span data-ttu-id="3e14b-108">Valor</span><span class="sxs-lookup"><span data-stu-id="3e14b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3e14b-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="3e14b-109">Scope</span></span>   |<span data-ttu-id="3e14b-110">Transparente</span><span class="sxs-lookup"><span data-stu-id="3e14b-110">Transparent</span></span>|
|<span data-ttu-id="3e14b-111">Versão</span><span class="sxs-lookup"><span data-stu-id="3e14b-111">Version</span></span>|<span data-ttu-id="3e14b-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="3e14b-112">4.5.1</span></span>|
|<span data-ttu-id="3e14b-113">Type</span><span class="sxs-lookup"><span data-stu-id="3e14b-113">Type</span></span>|<span data-ttu-id="3e14b-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="3e14b-114">Runtime</span></span>|
