---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77465994"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName não é NULL ao usar o DataAnnotations.ValidationAttribute personalizado

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.2 e versões anteriores, ao usar um <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personalizado, a propriedade <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retorna `null`. Na versão .NET Framework 4,8 anterior à atualização de outubro de 2019, ela retorna o nome do membro. Começando com [.NET Framework visualização de outubro de 2019 de Rollup de qualidade](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) para .NET Framework 4,8, ele retorna `null` por padrão, mas você pode optar por retornar o nome do membro em vez disso. |
|Sugestão|Adicione a configuração a seguir ao seu arquivo *Web. config* para que a propriedade retorne o nome do membro em [.NET Framework visualização de outubro de 2019 de Rollup de qualidade](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) para .NET Framework 4,8 e versões posteriores:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Na versão .NET Framework 4,8 anterior à atualização de outubro de 2019, adicionar isso ao seu arquivo *Web. config* restaura o comportamento anterior e a propriedade retorna `null`.|
|Escopo|Unknown (desconhecido)|
|Versão|4.8|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
