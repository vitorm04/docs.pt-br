---
ms.openlocfilehash: d8c9cec723ec4e57fb4868cc95881be8eb4001b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803152"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a>AddressHeaderCollection do WCF agora gera ArgumentException se um elemento addressHeader for nulo

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.7.1, o construtor <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> gera <xref:System.ArgumentException> se um elemento for <code>null</code>. No .NET Framework 4.7 e versões anteriores, nenhuma exceção é gerada.|
|Sugestão|Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão anterior, será possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})?displayProperty=nameWithType></li></ul>|
