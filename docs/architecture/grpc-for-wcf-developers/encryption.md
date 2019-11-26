---
title: Criptografia e segurança de rede-gRPC para desenvolvedores do WCF
description: Algumas observações sobre segurança de rede e criptografia no gRPC
ms.date: 09/02/2019
ms.openlocfilehash: fd993a2d75e97011c6c92cee02c24c5358a211ad
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967771"
---
# <a name="encryption-and-network-security"></a>Criptografia e segurança de rede

O modelo de segurança de rede do WCF é extensivo e complexo, incluindo segurança em nível de transporte usando HTTPS ou TLS sobre TCP e segurança em nível de mensagem usando a especificação WS-Security para criptografar mensagens individuais.

gRPC deixa a rede segura para o protocolo HTTP/2 subjacente, que pode ser protegido usando certificados TLS regulares.

Navegadores da Web insistem no uso de conexões TLS para HTTP/2, mas com a maioria dos clientes programáticos, incluindo. `HttpClient`de rede, o pode usar HTTP/2 em conexões não criptografadas. *o* `HttpClient` requer criptografia por padrão, mas você pode substituí-lo usando uma opção de <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Para APIs públicas, você sempre deve usar conexões TLS e fornecer certificados válidos para seus serviços de uma autoridade SSL apropriada. O [LetsEncrypt](https://letsencrypt.org) fornece certificados SSL gratuitos e automatizados, e a maior parte da infraestrutura de hospedagem atualmente dá suporte ao padrão LetsEncrypt com plug-ins ou extensões comuns.

Para serviços internos em uma rede corporativa, você ainda deve considerar o uso do TLS para proteger o tráfego de rede de e para seus serviços gRPCs.

A comunicação entre os microserviços em um cluster como o kubernetes ou o Docker Swarm é, em geral, criptografada automaticamente pela camada de rede do contêiner, portanto, não é necessário implementar o TLS em serviços executados exclusivamente nesse cluster. Haverá mais informações sobre esse assunto na seção "malha de serviço" do próximo capítulo.

Se você precisar usar o TLS explícito entre os serviços em execução no kubernetes, considere usar uma autoridade de certificação no cluster e um controlador do Gerenciador de certificados como [CERT-Manager](https://docs.cert-manager.io/en/latest/) para atribuir certificados automaticamente aos serviços no momento da implantação.

>[!div class="step-by-step"]
>[Anterior](channel-credentials.md)
>[Próximo](grpc-in-production.md)
