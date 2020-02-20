---
ms.openlocfilehash: 2c532bf3778b940f68db859420dd12826e9da388
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77465985"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serialização de caracteres de controle com DataContractJsonSerializer agora é compatível com ECMAScript V6 e V8

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2 e versões anteriores, o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> não serializava alguns caracteres de controle especiais, como \b, \f e \t, de forma que fosse compatível com os padrões ECMAScript V6 e V8. A partir do .NET Framework 4,7, a serialização desses caracteres de controle é compatível com ECMAScript V6 e V8.|
|Sugestão|Por padrão, esse novo layout é habilitado para aplicativos que se destinam ao .NET Framework 4.7. Se esse comportamento não for desejado, você poderá recusar esse recurso adicionando a seguinte linha na seção <code>&lt;runtime&gt;</code> do arquivo app.config ou web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|
