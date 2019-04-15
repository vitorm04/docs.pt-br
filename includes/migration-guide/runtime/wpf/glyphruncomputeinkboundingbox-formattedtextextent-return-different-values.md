---
ms.openlocfilehash: 059aa6f5885634b22b64d594563973f17fd2c4e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235063"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun.ComputeInkBoundingBox() e FormattedText.Extent retornam valores diferentes começando no .NET Framework 4.5

|   |   |
|---|---|
|Detalhes|Foram feitas melhorias em <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> e <xref:System.Windows.Media.FormattedText.Extent> do .NET Framework 4.5 para resolver problemas em que as caixas eram muito pequenas para o glifos contidos em alguns casos no .NET Framework 4.0. Como resultado, algumas caixas delimitadoras serão maiores a partir do .NET Framework 4.5, resultando em diferenças sutis no layout da interface do usuário.|
|Sugestão|Lembre-se de que alguns tamanhos de caixa delimitadora do glifo aumentaram. Essas alterações geralmente aprimorarão a apresentação e os testes de caixa de clique, mas se o comportamento anterior (anterior ao .NET 4.5) for desejado, ele poderá ser aceito com a adição da seguinte entrada ao arquivo app.config:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
