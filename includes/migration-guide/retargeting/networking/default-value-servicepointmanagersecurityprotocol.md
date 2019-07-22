---
ms.openlocfilehash: 3b3df8ad736f8f1c6a09e3349379b8c689cf731c
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235577"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>O valor padrão de ServicePointManager.SecurityProtocol é SecurityProtocolType.System.Default

|   |   |
|---|---|
|Detalhes|A partir dos aplicativos destinados ao .NET Framework 4.7, o valor padrão da propriedade <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> é <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Essa alteração permite que APIs de rede do .NET Framework baseadas em SslStream (como FTP, HTTPS e SMTP) herdem os protocolos de segurança padrão do sistema operacional em vez de usar valores embutidos em código definidos pelo .NET Framework. O padrão varia de acordo com o sistema operacional e qualquer configuração personalizada executada pelo administrador do sistema. Para obter informações sobre o protocolo SChannel padrão em cada versão do sistema operacional Windows, confira [Protocols in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-) [Protocolos em TLS/SSL (Schannel SSP)].</p>Para aplicativos direcionados a uma versão anterior do .NET Framework, o valor padrão da propriedade <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> depende da versão do .NET Framework de destino. Consulte a [seção de Rede das Alterações de redirecionamento para a migração do .NET Framework 4.5.2 para 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) para obter mais informações.|
|Sugestão|Esta alteração afeta aplicativos direcionados ao .NET Framework 4.7 ou a versões posteriores. </br>Se você preferir usar um protocolo definido em vez de contar com o padrão do sistema, defina explicitamente o valor da propriedade <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>.</br>Se essa alteração não for desejada, você poderá desativá-la incluindo uma configuração na seção [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo. O exemplo a seguir mostra a seção <code>&lt;runtime&gt;</code> e a opção de recusa <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code>:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|
