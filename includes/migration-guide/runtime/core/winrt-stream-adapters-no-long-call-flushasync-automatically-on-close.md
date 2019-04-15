---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235068"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Adaptadores de fluxo do WinRT não chamam mais FlushAsync automaticamente ao fechar

|   |   |
|---|---|
|Detalhes|Em aplicativos da Windows Store, os adaptadores de fluxo do Windows Runtime não chamam mais o método de FlushAsync do método Dispose.|
|Sugestão|Essa alteração deve ser transparente. Os desenvolvedores podem restaurar o comportamento anterior gravando um código como este:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Escopo|Transparente|
|Versão|4.5.1|
|Tipo|Tempo de execução|
