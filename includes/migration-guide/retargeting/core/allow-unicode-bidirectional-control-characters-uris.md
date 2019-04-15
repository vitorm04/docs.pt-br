---
ms.openlocfilehash: 3e9a1009167d8a765bc401d64a574bd123736ccd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233907"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Permitir caracteres de controle bidirecionais Unicode em URIs

|   |   |
|---|---|
|Detalhes|O Unicode especifica vários caracteres de controle especiais usados para especificar a orientação do texto. Nas versões anteriores do .NET Framework, esses caracteres eram excluídos incorretamente de todos os URIs mesmo quando estavam presentes em sua forma codificada por porcentagem. Para atender melhor ao [RFC 3987](https://tools.ietf.org/html/rfc3987), agora esses caracteres são permitidos nos URIs. Quando encontrados sem codificação em um URI, eles são codificados por porcentagem. Quando encontrados codificados por porcentagem, eles são deixados no estado em que se encontram.|
|Sugestão|Para aplicativos direcionados a versões do .NET Framework começando com a 4.7.2, o suporte para caracteres bidirecionais Unicode é habilitado por padrão. Se essa alteração não for desejada, você poderá desabilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Para aplicativos direcionados a versões anteriores do .NET Framework, mas executados em versões começando com o .NET Framework 4.7.2, o suporte para caracteres bidirecionais Unicode é desabilitado por padrão. Você poderá habilitá-la adicionando a seguinte opção [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) à seção <code>&lt;runtime&gt;</code> do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
