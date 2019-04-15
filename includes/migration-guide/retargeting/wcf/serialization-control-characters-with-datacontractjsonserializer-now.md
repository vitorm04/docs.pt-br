---
ms.openlocfilehash: 0642b184d85306a453d429f247dad95a259cb012
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236369"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serialização de caracteres de controle com DataContractJsonSerializer agora é compatível com ECMAScript V6 e V8

|   |   |
|---|---|
|Detalhes|No .NET framework 4.6.2 e nas versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> não serializava alguns caracteres de controle especiais, como \b, \f e \t, de uma forma compatível com os padrões ECMAScript V6 e V8. A partir do .NET Framework 4.7, a serialização desses caracteres de controle é compatível com o ECMAScript V6 e V8.|
|Sugestão|Por padrão, esse novo layout é habilitado para aplicativos que se destinam ao .NET Framework 4.7. Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção <code>&lt;runtime&gt;</code> do arquivo app.config ou web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
