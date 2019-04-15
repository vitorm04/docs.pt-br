---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235068"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="5534c-101">Adaptadores de fluxo do WinRT não chamam mais FlushAsync automaticamente ao fechar</span><span class="sxs-lookup"><span data-stu-id="5534c-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5534c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5534c-102">Details</span></span>|<span data-ttu-id="5534c-103">Em aplicativos da Windows Store, os adaptadores de fluxo do Windows Runtime não chamam mais o método de FlushAsync do método Dispose.</span><span class="sxs-lookup"><span data-stu-id="5534c-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="5534c-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5534c-104">Suggestion</span></span>|<span data-ttu-id="5534c-105">Essa alteração deve ser transparente.</span><span class="sxs-lookup"><span data-stu-id="5534c-105">This change should be transparent.</span></span> <span data-ttu-id="5534c-106">Os desenvolvedores podem restaurar o comportamento anterior gravando um código como este:</span><span class="sxs-lookup"><span data-stu-id="5534c-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="5534c-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="5534c-107">Scope</span></span>|<span data-ttu-id="5534c-108">Transparente</span><span class="sxs-lookup"><span data-stu-id="5534c-108">Transparent</span></span>|
|<span data-ttu-id="5534c-109">Versão</span><span class="sxs-lookup"><span data-stu-id="5534c-109">Version</span></span>|<span data-ttu-id="5534c-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5534c-110">4.5.1</span></span>|
|<span data-ttu-id="5534c-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="5534c-111">Type</span></span>|<span data-ttu-id="5534c-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5534c-112">Runtime</span></span>|
