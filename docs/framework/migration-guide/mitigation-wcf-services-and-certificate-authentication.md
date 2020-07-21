---
title: 'Mitigação: serviços WCF e autenticação de certificado'
description: Saiba como mitigar problemas de autenticação de certificado das alterações para a lista padrão do protocolo SSL do WCF no .NET Framework 4,6.
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
ms.openlocfilehash: b6460e58bb32151003430d6573c4bcf1b514081b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475366"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="38f5c-103">Mitigação: serviços WCF e autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="38f5c-103">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="38f5c-104">O .NET Framework 4.6 adiciona o TLS 1.1 e o TLS 1.2 à lista padrão de protocolos SSL do WCF.</span><span class="sxs-lookup"><span data-stu-id="38f5c-104">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="38f5c-105">Quando os computadores cliente e servidor têm o .NET Framework 4.6 ou posteriores instalados, o TLS 1.2 é usado para negociação.</span><span class="sxs-lookup"><span data-stu-id="38f5c-105">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="38f5c-106">Impacto</span><span class="sxs-lookup"><span data-stu-id="38f5c-106">Impact</span></span>

<span data-ttu-id="38f5c-107">O TLS 1.2 não dá suporte à autenticação do certificado MD5.</span><span class="sxs-lookup"><span data-stu-id="38f5c-107">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="38f5c-108">Como resultado, se um cliente usar um certificado SSL que usa MD5 para o algoritmo de hash, o cliente WCF falhará ao se conectar ao serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="38f5c-108">As a result, if a customer uses an SSL certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="38f5c-109">Para saber mais, confira [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md) (Mitigação: serviços WCF e autenticação de certificado).</span><span class="sxs-lookup"><span data-stu-id="38f5c-109">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="38f5c-110">Atenuação</span><span class="sxs-lookup"><span data-stu-id="38f5c-110">Mitigation</span></span>

<span data-ttu-id="38f5c-111">Você pode contornar esse problema para que um cliente WCF possa se conectar a um servidor WCF seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="38f5c-111">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="38f5c-112">Atualize o certificado para não usar o algoritmo MD5.</span><span class="sxs-lookup"><span data-stu-id="38f5c-112">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="38f5c-113">Esta é a solução recomendada.</span><span class="sxs-lookup"><span data-stu-id="38f5c-113">This is the recommended solution.</span></span>

- <span data-ttu-id="38f5c-114">Se a associação não tiver sido configurada dinamicamente no código-fonte, atualize o arquivo de configuração de aplicativo para usar o TLS 1.1 ou uma versão anterior do protocolo.</span><span class="sxs-lookup"><span data-stu-id="38f5c-114">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="38f5c-115">Isso permite que você continue usando um certificado com o algoritmo de hash MD5.</span><span class="sxs-lookup"><span data-stu-id="38f5c-115">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="38f5c-116">Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.</span><span class="sxs-lookup"><span data-stu-id="38f5c-116">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="38f5c-117">O arquivo de configuração que se segue demonstra isso:</span><span class="sxs-lookup"><span data-stu-id="38f5c-117">The following configuration file does this:</span></span>

  ```xml
  <configuration>
      <system.serviceModel>
          <bindings>
              <netTcpBinding>
                  <binding>
                      <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                          <transport clientCredentialType="None|Windows|Certificate"
                                              protectionLevel="None|Sign|EncryptAndSign"
                                              sslProtocols="Ssl3|Tls1|Tls11">
                          </transport>
                      </security>
                  </binding>
              </netTcpBinding>
          </bindings>
      </system.serviceModel>
  </configuration>
  ```

- <span data-ttu-id="38f5c-118">Se a associação foi configurada dinamicamente no código-fonte, atualize a propriedade <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> para usar o TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou uma versão anterior do protocolo no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="38f5c-118">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="38f5c-119">Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.</span><span class="sxs-lookup"><span data-stu-id="38f5c-119">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="38f5c-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38f5c-120">See also</span></span>

- [<span data-ttu-id="38f5c-121">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="38f5c-121">Application compatibility</span></span>](application-compatibility.md)
