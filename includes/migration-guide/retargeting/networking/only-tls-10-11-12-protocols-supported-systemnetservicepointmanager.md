---
ms.openlocfilehash: 2a8f20bef8e865235b857014e6d24c625c851d83
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804565"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Somente os protocolos Tls 1.0, 1.1 e 1.2 são compatíveis com System.Net.ServicePointManager e System.Net.Security.SslStream

|   |   |
|---|---|
|Detalhes|Começando no .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager> e <xref:System.Net.Security.SslStream> têm permissão para usar somente um dos três seguintes protocolos: Tls1.0, Tls1.1 ou Tls1.2. Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.|
|Sugestão|A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls1.2. Se não for viável ou se os aplicativos cliente estiverem desfeitos, a classe <xref:System.AppContext?displayProperty=name> poderá ser usada para recusar esse recurso de duas maneiras:<ol><li>Configurar de forma programática as opções de compatibilidade na instância <xref:System.AppContext?displayProperty=name>, conforme explicado [aqui](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Adicionando a seguinte linha na seção <code>&lt;runtime&gt;</code> do arquivo app.config:</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.6|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|

