---
ms.openlocfilehash: 19dcdf006de0bfa7c6b0a8127612a49a66a24802
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804515"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x por padrão passa o sinalizador SCH_SEND_AUX_RECORD para a API do SCHANNEL subjacente

|   |   |
|---|---|
|Detalhes|Ao usar TLS 1.x, o .NET Framework depende da API de SCHANNEL do Windows subjacente. A partir do .NET Framework 4.6, o sinalizador [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) é passado por padrão para SCHANNEL. Isso faz com que SCHANNEL divida os dados a serem criptografados em dois registros separados, o primeiro como um byte único e o segundo como <em>n</em>-1 bytes. Em casos raros, isso interrompe a comunicação entre clientes e servidores existentes que supõem que os dados residem em um único registro.|
|Sugestão|Se essa alteração interromper a comunicação com um servidor existente, você poderá desabilitá-la enviando o sinalizador [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred), e restaurar o comportamento anterior de não dividir dados em registros separados adicionando a seguinte opção ao elemento [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na seção [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo de configuração de aplicativo:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Essa configuração é fornecida apenas para compatibilidade com versões anteriores. Caso contrário, seu uso não é recomendado.</blockquote> |
|Escopo|Microsoft Edge|
|Versão|4.6|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

