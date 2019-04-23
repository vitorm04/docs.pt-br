---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803163"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a>A segurança de mensagens do WCF agora pode usar o TLS1.1 e o TLS1.2

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.7, os clientes podem configurar o TLS1.1 ou o TLS1.2 na segurança de mensagens do WCF, além do SSL3.0 e o TLS1.0, por meio das configurações do aplicativo.|
|Sugestão|No .NET Framework 4.7, a compatibilidade com o TLS1.1 e o TLS1.2 na segurança de mensagens do WCF é desabilitada por padrão. É possível habilitá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|
