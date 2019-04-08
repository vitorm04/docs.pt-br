---
ms.openlocfilehash: 4daa08ce4bbcfe5a7242f19506811e422d0477b7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760712"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>A configuração de aplicativo "dataAnnotations:dataTypeAttribute:disableRegEx" é habilitada por padrão no .NET Framework 4.7.2

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.1, foi introduzida uma configuração de aplicativo (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) que permite que os usuários desabilitem o uso de expressões regulares em atributos de tipo de dados (como <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> e <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). Isso ajuda a reduzir vulnerabilidades de segurança, por exemplo, impedindo que um ataque de negação de serviço use expressões regulares específicas.<br/>No .NET Framework 4.6.1, essa configuração de aplicativo para desabilitar o uso de expressões regulares era definida como <code>false</code> por padrão. Começando com o .NET Framework 4.7.2, a opção de configuração é definida como <code>true</code> por padrão para reduzir ainda mais as vulnerabilidades de segurança de aplicativos Web voltados ao .NET Framework 4.7.2 e acima.|
|Sugestão|Se observar que as expressões regulares em seu aplicativo Web não funcionam após atualizar para o .NET Framework 4.7.2, você poderá atualizar o valor da <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> configuração <code>false</code> para voltar ao comportamento anterior.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appsettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appsettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.2|
|Tipo|Tempo de execução|

