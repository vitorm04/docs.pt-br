---
ms.openlocfilehash: ae9ba8aaf842c6607020abf76c981266f5c4dd61
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856939"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Melhor validação do certificado de confiança de cadeia do WCF para autenticação de certificado do Net.Tcp

|   |   |
|---|---|
|Detalhes|O .NET framework 4.7.2 melhorou a validação do certificado de confiança de cadeia ao usar a autenticação de certificado com a segurança de transporte com o WCF. Com essa melhoria, os certificados do cliente que são usados para autenticar um servidor precisam ser configurados para autenticação do cliente.  Da mesma forma, os certificados do servidor usados para autenticar um servidor precisam ser configurados para autenticação do servidor. Com essa alteração, se o certificado raiz for desabilitado, a validação da cadeia de certificados falhará. A mesma alteração também foi feita para o .NET Framework 3.5 e as versões posteriores por meio do pacote cumulativo de segurança do Windows. Encontre mais informações [aqui](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Essa alteração é habilitada por padrão e pode ser desabilitada por uma definição de configuração.|
|Sugestão|<ul><li>Valide se a certificação do servidor e do cliente têm o OID de EKU necessário. Caso contrário, atualize a certificação.</li><li>Valide se o certificado raiz é inválido. Nesse caso, atualize o certificado raiz.</li><li>Como recusar a alteração: Caso não possa atualizar o certificado, solucione temporariamente a alteração da falha com as definições de configuração a seguir. No entanto, se você recusar a alteração, isso deixará seu sistema vulnerável ao problema de segurança.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Secundário|
|Versão|4.7.2|
|Tipo|Tempo de execução|

