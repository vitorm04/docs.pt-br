---
ms.openlocfilehash: afcb9b950d4c47b4251dcc8ab0cf9cfc702005c8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496624"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a><span data-ttu-id="bf585-101">Serviços WCF que usam NETTCP com a segurança SSL e autenticação de certificado MD5</span><span class="sxs-lookup"><span data-stu-id="bf585-101">WCF services that use NETTCP with SSL security and MD5 certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="bf585-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="bf585-102">Details</span></span>

<span data-ttu-id="bf585-103">O .NET Framework 4.6 adiciona o TLS 1.1 e o TLS 1.2 à lista padrão de protocolos SSL do WCF.</span><span class="sxs-lookup"><span data-stu-id="bf585-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL default protocol list.</span></span> <span data-ttu-id="bf585-104">Quando os computadores cliente e servidor têm o .NET Framework 4.6 ou versões posteriores instaladas, o TLS 1.2 é usado para negociação. O TLS 1.2 não é compatível com a autenticação do certificado MD5.</span><span class="sxs-lookup"><span data-stu-id="bf585-104">When both client and server machines have the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="bf585-105">Consequentemente, se um cliente usar um certificado MD5, o cliente WCF falhará ao se conectar ao serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="bf585-105">As a result, if a customer uses an MD5 certificate, the WCF client will fail to connect to the WCF service.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bf585-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="bf585-106">Suggestion</span></span>

<span data-ttu-id="bf585-107">Você pode contornar esse problema para que um cliente WCF possa se conectar a um servidor WCF seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="bf585-107">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="bf585-108">Atualize o certificado para não usar o algoritmo MD5.</span><span class="sxs-lookup"><span data-stu-id="bf585-108">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="bf585-109">Esta é a solução recomendada.</span><span class="sxs-lookup"><span data-stu-id="bf585-109">This is the recommended solution.</span></span>
- <span data-ttu-id="bf585-110">Se a associação não tiver sido configurada dinamicamente no código-fonte, atualize o arquivo de configuração de aplicativo para usar o TLS 1.1 ou uma versão anterior do protocolo.</span><span class="sxs-lookup"><span data-stu-id="bf585-110">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="bf585-111">Isso permite que você continue usando um certificado com o algoritmo de hash MD5.</span><span class="sxs-lookup"><span data-stu-id="bf585-111">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

> [!WARNING]
> <span data-ttu-id="bf585-112">Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.</span><span class="sxs-lookup"><span data-stu-id="bf585-112">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

<span data-ttu-id="bf585-113">O arquivo de configuração que se segue demonstra isso:</span><span class="sxs-lookup"><span data-stu-id="bf585-113">The following configuration file does this:</span></span>

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- <span data-ttu-id="bf585-114">Se a associação foi configurada dinamicamente no código-fonte, atualize a propriedade <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> para usar o TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou uma versão anterior do protocolo no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="bf585-114">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> or an earlier version of the protocol in the source code.</span></span>

> [!WARNING]
> <span data-ttu-id="bf585-115">Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.</span><span class="sxs-lookup"><span data-stu-id="bf585-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

| <span data-ttu-id="bf585-116">Nome</span><span class="sxs-lookup"><span data-stu-id="bf585-116">Name</span></span>    | <span data-ttu-id="bf585-117">Valor</span><span class="sxs-lookup"><span data-stu-id="bf585-117">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="bf585-118">Escopo</span><span class="sxs-lookup"><span data-stu-id="bf585-118">Scope</span></span>   | <span data-ttu-id="bf585-119">Secundária</span><span class="sxs-lookup"><span data-stu-id="bf585-119">Minor</span></span>   |
| <span data-ttu-id="bf585-120">Versão</span><span class="sxs-lookup"><span data-stu-id="bf585-120">Version</span></span> | <span data-ttu-id="bf585-121">4.6</span><span class="sxs-lookup"><span data-stu-id="bf585-121">4.6</span></span>     |
| <span data-ttu-id="bf585-122">Tipo</span><span class="sxs-lookup"><span data-stu-id="bf585-122">Type</span></span>    | <span data-ttu-id="bf585-123">Runtime</span><span class="sxs-lookup"><span data-stu-id="bf585-123">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="bf585-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="bf585-124">Affected APIs</span></span>

<span data-ttu-id="bf585-125">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="bf585-125">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
