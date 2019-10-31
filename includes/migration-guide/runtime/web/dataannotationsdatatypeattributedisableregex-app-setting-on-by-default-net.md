---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085533"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>A configuração de aplicativo "dataAnnotations:dataTypeAttribute:disableRegEx" é habilitada por padrão no .NET Framework 4.7.2

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.1, foi introduzida uma configuração de aplicativo (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) que permite que os usuários desabilitem o uso de expressões regulares em atributos de tipo de dados (como <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> e <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Isso ajuda a reduzir vulnerabilidades de segurança, por exemplo, impedindo que um ataque de negação de serviço use expressões regulares específicas.<br/>No .NET Framework 4.6.1, essa configuração de aplicativo para desabilitar o uso de expressões regulares era definida como <code>false</code> por padrão. A partir do .NET Framework 4.7.2, essa opção de configuração é definida como <code>true</code> por padrão para reduzir ainda mais a vulnerabilidades seguras para aplicativos Web direcionados .NET Framework 4.7.2 e superiores.|
|Sugestão|Se observar que as expressões regulares em seu aplicativo Web não funcionam após atualizar para o .NET Framework 4.7.2, você poderá atualizar o valor da <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> configuração <code>false</code> para voltar ao comportamento anterior.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Version|4.7.2|
|Digite|Tempo de execução|
