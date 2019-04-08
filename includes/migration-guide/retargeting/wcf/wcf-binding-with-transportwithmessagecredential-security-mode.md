---
ms.openlocfilehash: ce7e2db3f74ec24f47b1c224335451c997c4c349
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760948"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Associação do WCF com o modo de segurança TransportWithMessageCredential

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.6.1, a associação do WCF que usar o modo de segurança TransportWithMessageCredential poderá ser configurada para receber mensagens com cabeçalhos &quot;to&quot; não assinados para chaves de segurança assimétricas. Por padrão, os cabeçalhos &quot;to&quot; não assinados continuarão a ser rejeitados no NET Framework 4.6.1. Eles só serão aceitos se o aplicativo aceitar esse novo modo de operação usando a opção de configuração Switch.System.ServiceModel.AllowUnsignedToHeader.|
|Sugestão|Como esse é um recurso de aceitação, ele não deve afetar o comportamento dos aplicativos existentes.<br/>Para controlar se o novo comportamento está sendo usado ou não, use a seguinte configuração:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Transparente|
|Versão|4.6.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

