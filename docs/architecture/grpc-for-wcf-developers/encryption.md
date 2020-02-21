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
# <a name="encryption-and-network-security"></a><span data-ttu-id="2ed83-103">Criptografia e segurança de rede</span><span class="sxs-lookup"><span data-stu-id="2ed83-103">Encryption and network security</span></span>

<span data-ttu-id="2ed83-104">O WCF (modelo de segurança de rede para Windows Communication Foundation) é extensivo e complexo.</span><span class="sxs-lookup"><span data-stu-id="2ed83-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="2ed83-105">Ele inclui segurança em nível de transporte usando HTTPS ou TLS via TCP e segurança em nível de mensagem usando a especificação WS-Security para criptografar mensagens individuais.</span><span class="sxs-lookup"><span data-stu-id="2ed83-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="2ed83-106">gRPC deixa a rede segura para o protocolo HTTP/2 subjacente, que você pode proteger usando certificados TLS.</span><span class="sxs-lookup"><span data-stu-id="2ed83-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="2ed83-107">Navegadores da Web insistem no uso de conexões TLS para HTTP/2, mas com a maioria dos clientes programáticos, incluindo. `HttpClient`de rede, o pode usar HTTP/2 em conexões não criptografadas.</span><span class="sxs-lookup"><span data-stu-id="2ed83-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="2ed83-108">o `HttpClient` requer criptografia por padrão, mas você pode substituí-lo usando uma opção de <xref:System.AppContext>.</span><span class="sxs-lookup"><span data-stu-id="2ed83-108">`HttpClient` does require encryption by default, but you can override this by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="2ed83-109">Para APIs públicas, você sempre deve usar conexões TLS e fornecer certificados válidos para seus serviços de uma autoridade SSL apropriada.</span><span class="sxs-lookup"><span data-stu-id="2ed83-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="2ed83-110">O [LetsEncrypt](https://letsencrypt.org) fornece certificados SSL gratuitos e automatizados, e a maioria das infra-estruturas de hospedagem atualmente dá suporte ao padrão LetsEncrypt com plug-ins ou extensões comuns.</span><span class="sxs-lookup"><span data-stu-id="2ed83-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="2ed83-111">Para serviços internos em uma rede corporativa, você ainda deve considerar o uso do TLS para proteger o tráfego de rede de e para seus serviços gRPCs.</span><span class="sxs-lookup"><span data-stu-id="2ed83-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="2ed83-112">Se você precisar usar o TLS explícito entre os serviços em execução no kubernetes, considere usar uma autoridade de certificação no cluster e um controlador do Gerenciador de certificados como [CERT-Manager](https://docs.cert-manager.io/en/latest/).</span><span class="sxs-lookup"><span data-stu-id="2ed83-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="2ed83-113">Você pode atribuir certificados automaticamente aos serviços no momento da implantação.</span><span class="sxs-lookup"><span data-stu-id="2ed83-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2ed83-114">[Anterior](channel-credentials.md)
>[Próximo](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="2ed83-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
