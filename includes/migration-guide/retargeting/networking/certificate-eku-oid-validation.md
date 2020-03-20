---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804420"
---
### <a name="certificate-eku-oid-validation"></a>Validação dos certificados de EKU do OID

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.6, as classes <xref:System.Net.Security.SslStream> ou <xref:System.Net.ServicePointManager> executarão a validação do EKU (uso avançado de chave) do OID (identificador de objeto). Uma extensão de EKU (uso avançado de chave) é uma coleção de OIDs (identificadores de objeto) que indicam os aplicativos que usam a chave. A validação do EKU do OID usa retornos de chamada de certificado remoto para garantir que o certificado remoto tenha o OID correto para a finalidade pretendida.|
|Sugestão|Se essa alteração for indesejável, você pode desativar a validação do Certificado EKU OID [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) adicionando o seguinte switch ao [ \<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) no arquivo de configuração do aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Essa configuração é fornecida apenas para compatibilidade com versões anteriores. Caso contrário, seu uso não é recomendado.</blockquote> |
|Escopo|Secundária|
|Versão|4.6|
|Type|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
