---
ms.openlocfilehash: c0be08023f80bf0f96cc08f34b9ea8c5a73839e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77465994"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName não é NULL ao usar o DataAnnotations.ValidationAttribute personalizado

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.2 e versões anteriores, ao usar um <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personalizado, a propriedade <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retorna `null`. Na versão .NET Framework 4.8 antes da atualização de outubro de 2019, ele retorna o nome do membro. Começando com [.NET Framework Outubro 2019 Visualização de Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) de `null` Qualidade para .NET Framework 4.8, ele retorna por padrão, mas você pode optar por retornar o nome do membro em vez disso. |
|Sugestão|Adicione a seguinte configuração ao seu arquivo *web.config* para que a propriedade retorne o nome do membro no [.NET Framework Outubro 2019 Visualização do Rollup de Qualidade](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) para .NET Framework 4.8 e versões posteriores:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Na versão .NET Framework 4.8 antes da atualização de outubro de 2019, adicionar isso ao `null`seu arquivo *web.config* restaura o comportamento anterior e o retorno da propriedade .|
|Escopo|Unknown (desconhecido)|
|Versão|4.8|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
