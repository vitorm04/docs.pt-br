---
ms.openlocfilehash: 3b94c88809513e31a5f226bcfce39abbfa4de378
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017366"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a>ASP.NET ValidationContext.MemberName não é NULL ao usar o DataAnnotations.ValidationAttribute personalizado

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.7.2 e versões anteriores, ao usar um <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> personalizado, a propriedade <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> retorna <code>null</code>.  No .NET Framework 4.8, ela retorna o nome do membro.|
|Sugestão|Para restaurar o comportamento anterior, adicione a seguinte configuração ao seu arquivo de configuração do aplicativo:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Esse comportamento mudará em uma versão de serviço futura, quando você precisará aceitar explicitamente o novo comportamento. A propriedade retornará um valor não nulo para um `ValidationAttribute` personalizado se a opção `aspnet:GetValidationMemberName` for definida como `true`.|
|Escopo|Unknown|
|Versão|4.8|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
