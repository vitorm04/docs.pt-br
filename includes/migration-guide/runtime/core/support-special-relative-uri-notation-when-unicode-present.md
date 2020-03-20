---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997540"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Permitir notação de URI relativo especial quando o Unicode estiver presente

|   |   |
|---|---|
|Detalhes|<xref:System.Uri>não jogará <xref:System.NullReferenceException> mais <xref:System.Uri.TryCreate%2A> um ao chamar certas URIs relativas contendo Unicode. A reprodução mais <xref:System.NullReferenceException> simples do é abaixo, com as duas afirmações sendo equivalentes:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Para reproduzir a <xref:System.NullReferenceException>, os itens a seguir precisam ser verdadeiros:<ul><li>O URI precisa ser especificado como relativo acrescentando 'http:' a ele e não inserindo '//' depois dele.</li><li>O URI precisa conter Unicode codificado por porcentagem ou símbolos não reservados.</li></ul>|
|Sugestão|Os usuários que dependem desse comportamento para não permitir URIs relativos precisam especificar <xref:System.UriKind.Absolute?displayProperty=nameWithType> durante a criação de um URI.|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
