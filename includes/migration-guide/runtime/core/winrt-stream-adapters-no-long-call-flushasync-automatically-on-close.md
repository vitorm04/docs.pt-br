---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803192"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a><span data-ttu-id="267eb-101">Adaptadores de fluxo do WinRT não chamam mais FlushAsync automaticamente ao fechar</span><span class="sxs-lookup"><span data-stu-id="267eb-101">WinRT stream adapters no long call FlushAsync automatically on close</span></span>

|   |   |
|---|---|
|<span data-ttu-id="267eb-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="267eb-102">Details</span></span>|<span data-ttu-id="267eb-103">Em aplicativos da Windows Store, os adaptadores de fluxo do Windows Runtime não chamam mais o método de FlushAsync do método Dispose.</span><span class="sxs-lookup"><span data-stu-id="267eb-103">In Windows Store apps, Windows Runtime stream adapters no longer call the FlushAsync method from the Dispose method.</span></span>|
|<span data-ttu-id="267eb-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="267eb-104">Suggestion</span></span>|<span data-ttu-id="267eb-105">Essa alteração deve ser transparente.</span><span class="sxs-lookup"><span data-stu-id="267eb-105">This change should be transparent.</span></span> <span data-ttu-id="267eb-106">Os desenvolvedores podem restaurar o comportamento anterior gravando um código como este:</span><span class="sxs-lookup"><span data-stu-id="267eb-106">Developers can restore the previous behavior by writing code like this:</span></span><pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|<span data-ttu-id="267eb-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="267eb-107">Scope</span></span>|<span data-ttu-id="267eb-108">Transparente</span><span class="sxs-lookup"><span data-stu-id="267eb-108">Transparent</span></span>|
|<span data-ttu-id="267eb-109">Versão</span><span class="sxs-lookup"><span data-stu-id="267eb-109">Version</span></span>|<span data-ttu-id="267eb-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="267eb-110">4.5.1</span></span>|
|<span data-ttu-id="267eb-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="267eb-111">Type</span></span>|<span data-ttu-id="267eb-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="267eb-112">Runtime</span></span>|
