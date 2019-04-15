---
ms.openlocfilehash: 897bb0b0650c633b87a792516c62566f491ec3fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233912"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>O DeflateStream usa APIs nativas para descompactação

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.7.2, a implementação da descompactação na classe <code>T:System.IO.Compression.DeflateStream</code> foi alterada para usar APIs nativas do Windows por padrão. Normalmente, isso resulta em uma melhoria significativa de desempenho. Todos os aplicativos .NET direcionados ao .NET Framework versão 4.7.2 ou superior usam a implementação nativo. Essa alteração pode resultar em algumas diferenças no comportamento, que incluem:<ul><li>As mensagens de exceção podem ser diferentes. No entanto, o tipo de exceção gerada permanece o mesmo.</li><li>Algumas situações especiais, como não ter memória suficiente para concluir uma operação, podem ser tratadas de maneira diferente.</li><li>Existem diferenças conhecidas para analisar o cabeçalho gzip (observação: somente o <code>GZipStream</code> definido para descompactação é afetado):</li><li>As exceções durante a análise de cabeçalhos inválidos podem ser geradas em momentos diferentes.</li><li>A implementação nativa impõe que os valores de alguns sinalizadores reservados dentro do cabeçalho gzip (ou seja, [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) são definidos de acordo com a especificação, o que pode causar a geração de uma exceção em casos em que, anteriormente, valores inválidos eram ignorados.</li></ul>|
|Sugestão|Se a descompactação com as APIs nativas tiver prejudicado o comportamento do aplicativo, você poderá recusar esse recurso adicionando a opção <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> à seção <code>runtime</code> do arquivo app.config e configurando-a como <code>true</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|
