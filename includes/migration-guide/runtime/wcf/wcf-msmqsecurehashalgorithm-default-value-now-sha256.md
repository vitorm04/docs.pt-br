---
ms.openlocfilehash: a2d4b7592727ca20ee79867094d6972eb9c4baed
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857238"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>O valor padrão MsmqSecureHashAlgorithm do WCF agora é SHA256

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.7.1, o algoritmo de assinatura da mensagem padrão no WCF para mensagens Msmq é SHA256. No .NET Framework 4.7 e versões anteriores, o algoritmo de assinatura da mensagem padrão é SHA1.|
|Sugestão|Se houver problemas de compatibilidade com essa alteração no .NET Framework 4.7.1 ou uma versão posterior, será possível recusá-la adicionando a seguinte linha à seção <code>&lt;runtime&gt;</code> do arquivo app.config:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Tempo de execução|

