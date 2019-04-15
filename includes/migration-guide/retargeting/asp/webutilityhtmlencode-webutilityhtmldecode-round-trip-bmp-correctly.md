---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234602"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode e WebUtility.HtmlDecode vão e voltam corretamente ao BMP

|   |   |
|---|---|
|Detalhes|Nos aplicativos destinados ao .NET Framework 4.5, os caracteres fora do BMP (Basic Multilingual Plane) vão e voltam corretamente quando são passados para os métodos <xref:System.Net.WebUtility.HtmlDecode(System.String)>.|
|Sugestão|Essa alteração não deve afetar os aplicativos atuais, mas para restaurar o comportamento original, defina o atributo <code>targetFramework</code> do elemento <code>&lt;httpRuntime&gt;</code> como uma cadeia de caracteres diferente de &quot;4.5&quot;. Você também pode definir os atributos <code>unicodeEncodingConformance</code> e <code>unicodeDecodingConformance</code> do elemento de configuração <code>&lt;webUtility&gt;</code> para controlar esse comportamento independentemente da versão de destino do .NET Framework.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|
