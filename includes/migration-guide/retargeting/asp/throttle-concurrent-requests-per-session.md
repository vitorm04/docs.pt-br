---
ms.openlocfilehash: db8eb017bdf166b0f1a241f5a8f7db9b9430898a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760149"
---
### <a name="throttle-concurrent-requests-per-session"></a>Limitação de solicitações simultâneas por sessão

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2 e versões anteriores, o ASP.NET executa solicitações com a mesma Sessionid sequencialmente e sempre emite a Sessionid por meio de um cookie por padrão. Se uma página levar muito tempo para responder, ele prejudicará significativamente o desempenho do servidor simplesmente pressionando F5 no navegador. Na correção, adicionou-se um contador que acompanha as solicitações enfileiradas e encerra as solicitações quando elas excedem um limite especificado. O valor padrão é 50. Se o limite for alcançado, um aviso será registrado no log de eventos e uma resposta HTTP 500 poderá ser registrada no log do IIS.|
|Sugestão|Para restaurar o comportamento antigo, você pode adicionar a seguinte configuração ao arquivo web.config para recusar o novo comportamento.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|

