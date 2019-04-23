---
ms.openlocfilehash: 34d7395e72f6ef252ac68366bcd346cd8d464036
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236107"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Permitir notação de URI relativo especial quando o Unicode estiver presente

|   |   |
|---|---|
|Detalhes|<xref:System.Uri> não gerará mais uma <xref:System.NullReferenceException> ao chamar <xref:System.Uri.TryCreate%2A> em determinados URIs relativos que contêm Unicode. A reprodução mais simples de <xref:System.NullReferenceException> está abaixo, com as duas instruções equivalentes:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Para reproduzir a <xref:System.NullReferenceException>, os itens a seguir precisam ser verdadeiros:<ul><li>O URI precisa ser especificado como relativo acrescentando 'http:' a ele e não inserindo '//' depois dele.</li><li>O URI precisa conter Unicode codificado por porcentagem ou símbolos não reservados.</li></ul>|
|Sugestão|Os usuários que dependem desse comportamento para não permitir URIs relativos precisam especificar <xref:System.UriKind.Absolute?displayProperty=nameWithType> durante a criação de um URI.|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
