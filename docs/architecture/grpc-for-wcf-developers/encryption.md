---
title: Criptografia e segurança de rede-gRPC para desenvolvedores do WCF
description: Algumas observações sobre segurança de rede e criptografia no gRPC
ms.date: 09/02/2019
ms.openlocfilehash: f8a7aeaf2a65e4ff56ac33d728e40f09a436f7a6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542761"
---
# <a name="encryption-and-network-security"></a>Criptografia e segurança de rede

O WCF (modelo de segurança de rede para Windows Communication Foundation) é extensivo e complexo. Ele inclui segurança em nível de transporte usando HTTPS ou TLS via TCP e segurança em nível de mensagem usando a especificação WS-Security para criptografar mensagens individuais.

gRPC deixa a rede segura para o protocolo HTTP/2 subjacente, que você pode proteger usando certificados TLS.

Navegadores da Web insistem no uso de conexões TLS para HTTP/2, mas com a maioria dos clientes programáticos, incluindo. `HttpClient`de rede, o pode usar HTTP/2 em conexões não criptografadas. o `HttpClient` requer criptografia por padrão, mas você pode substituí-lo usando uma opção de <xref:System.AppContext>.

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Para APIs públicas, você sempre deve usar conexões TLS e fornecer certificados válidos para seus serviços de uma autoridade SSL apropriada. O [LetsEncrypt](https://letsencrypt.org) fornece certificados SSL gratuitos e automatizados, e a maioria das infra-estruturas de hospedagem atualmente dá suporte ao padrão LetsEncrypt com plug-ins ou extensões comuns.

Para serviços internos em uma rede corporativa, você ainda deve considerar o uso do TLS para proteger o tráfego de rede de e para seus serviços gRPCs.

Se você precisar usar o TLS explícito entre os serviços em execução no kubernetes, considere usar uma autoridade de certificação no cluster e um controlador do Gerenciador de certificados como [CERT-Manager](https://docs.cert-manager.io/en/latest/). Você pode atribuir certificados automaticamente aos serviços no momento da implantação.

>[!div class="step-by-step"]
>[Anterior](channel-credentials.md)
>[Próximo](grpc-in-production.md)
