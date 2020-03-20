---
ms.openlocfilehash: b57e0acb03a99f33460a7b6c880280b37e01a17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859235"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>Segurança de transporte do WCF é compatível com certificados armazenados usando CNG

|   |   |
|---|---|
|Detalhes|Começando com os aplicativos destinados ao .NET Framework 4.6.2, a segurança de transporte do WCF é compatível com certificados armazenados usando a CNG (Biblioteca de Criptografia do Windows). Esse suporte é limitado a certificados com uma chave pública que tenha um expoente não superior a 32 bits de comprimento. Quando o aplicativo é destinado ao .NET Framework 4.6.2, esse recurso é ativado por padrão. Em versões anteriores do .NET Framework, a tentativa de usar os certificados X509 com um provedor de armazenamento de chaves CSG gera uma exceção.|
|Sugestão|Os aplicativos destinados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2, podem habilitar a compatibilidade com os certificados CNG adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config ou web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Isso também pode ser feito de modo programático com o seguinte código:<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Observe que, por causa dessa alteração, qualquer código de tratamento de exceção que dependa da tentativa de iniciar a comunicação segura com um certificado CNG para falhar não será mais executado.|
|Escopo|Secundária|
|Versão|4.6.2|
|Type|Redirecionando|
