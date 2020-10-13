---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997749"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a>Conjuntos de codificação TLS padrão para .NET no Linux

O .NET, no Linux, agora respeita a configuração do OpenSSL para conjuntos de codificação padrão ao fazer o TLS/SSL por meio de <xref:System.Net.Security.SslStream> operações de nível superior ou de classe, como https por meio da <xref:System.Net.Http.HttpClient> classe. Quando os conjuntos de codificação padrão não são explicitamente configurados, o .NET no Linux usa uma lista rigorosamente restrita de conjuntos de codificação permitidos.

#### <a name="change-description"></a>Descrição das alterações

Nas versões anteriores do .NET, o .NET não respeita a configuração do sistema para conjuntos de codificação padrão. A lista do pacote de criptografia padrão para .NET no Linux é muito permissiva.

A partir do .NET 5,0, o .NET no Linux respeita a configuração do OpenSSL para conjuntos de codificação padrão quando ele é especificado no *OpenSSL. cnf*. Quando os conjuntos de codificação não são explicitamente configurados, os únicos conjuntos de codificação permitidos são os seguintes:

- Pacotes de criptografia TLS 1,3
- TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

Como esse padrão de fallback não inclui conjuntos de codificação compatíveis com TLS 1,0 ou TLS 1,1, essas versões de protocolo mais antigas são efetivamente desabilitadas por padrão.

O fornecimento de um valor de CipherSuitePolicy para SslStream para uma sessão específica ainda substituirá o conteúdo do arquivo de configuração e/ou o padrão de fallback do .NET.

#### <a name="reason-for-change"></a>Motivo da alteração

Os usuários que executam o .NET no Linux solicitaram que a configuração padrão <xref:System.Net.Security.SslStream> seja alterada para uma que fornecesse uma alta classificação de segurança de ferramentas de avaliação de terceiros.

#### <a name="version-introduced"></a>Versão introduzida

RC1 5,0

#### <a name="recommended-action"></a>Ação recomendada

Os novos padrões provavelmente funcionarão ao se comunicar com clientes ou servidores modernos. Se você precisar expandir a lista padrão de pacotes de criptografia para aceitar clientes herdados (ou contatar servidores herdados), especifique um `CipherSuitePolicy` valor ou altere o arquivo de configuração do OpenSSL. Em muitas distribuições do Linux, o arquivo de configuração do OpenSSL está em */etc/SSL/OpenSSL.cnf*.

Este arquivo *OpenSSL. cnf* de exemplo é um arquivo mínimo equivalente à política de pacotes de criptografia padrão para o .NET 5,0 e posterior no Linux. Em vez de substituir o arquivo do sistema, mescle esses conceitos com o arquivo que está presente no seu sistema.

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

Nas distribuições Red Hat Enterprise Linux, CentOS e Fedora, os aplicativos .NET assumem como padrão os conjuntos de codificação permitidos pelas políticas de criptografia de todo o sistema. Nessas distribuições, use a configuração de políticas de criptografia em vez do *OpenSSL. cnf*.

#### <a name="category"></a>Categoria

- Criptografia
- Segurança

#### <a name="affected-apis"></a>APIs afetadas

Não detectible por meio da análise de API.

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
