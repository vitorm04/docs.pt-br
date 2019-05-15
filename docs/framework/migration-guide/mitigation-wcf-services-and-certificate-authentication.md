---
title: 'Mitigação: Serviços WCF e autenticação de certificado'
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f94cabb482a237395854fcdc91df476c567069c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599504"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="c0ebe-102">Mitigação: Serviços WCF e autenticação de certificado</span><span class="sxs-lookup"><span data-stu-id="c0ebe-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="c0ebe-103">O .NET Framework 4.6 adiciona o TLS 1.1 e o TLS 1.2 à lista padrão de protocolos SSL do WCF.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="c0ebe-104">Quando os computadores cliente e servidor têm o .NET Framework 4.6 ou posteriores instalados, o TLS 1.2 é usado para negociação.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="c0ebe-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="c0ebe-105">Impact</span></span>  
 <span data-ttu-id="c0ebe-106">O TLS 1.2 não dá suporte à autenticação do certificado MD5.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="c0ebe-107">Consequentemente, se um cliente usar um certificado SSL que use MD5 para o algoritmo de hash, o cliente WCF falhará ao se conectar ao serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="c0ebe-108">Para obter mais informações, confira [Mitigação: Serviços WCF e autenticação de certificado](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c0ebe-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="c0ebe-109">Redução</span><span class="sxs-lookup"><span data-stu-id="c0ebe-109">Mitigation</span></span>  
 <span data-ttu-id="c0ebe-110">Você pode contornar esse problema para que um cliente WCF possa se conectar a um servidor WCF seguindo um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="c0ebe-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
- <span data-ttu-id="c0ebe-111">Atualize o certificado para não usar o algoritmo MD5.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="c0ebe-112">Esta é a solução recomendada.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-112">This is the recommended solution.</span></span>  
  
- <span data-ttu-id="c0ebe-113">Se a associação não tiver sido configurada dinamicamente no código-fonte, atualize o arquivo de configuração de aplicativo para usar o TLS 1.1 ou uma versão anterior do protocolo.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="c0ebe-114">Isso permite que você continue usando um certificado com o algoritmo de hash MD5.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="c0ebe-115">Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="c0ebe-116">O arquivo de configuração que se segue demonstra isso:</span><span class="sxs-lookup"><span data-stu-id="c0ebe-116">The following configuration file does this:</span></span>  
  
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
        </system.ServiceModel>  
    </configuration>  
    ```  
  
- <span data-ttu-id="c0ebe-117">Se a associação foi configurada dinamicamente no código-fonte, atualize a propriedade <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> para usar o TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) ou uma versão anterior do protocolo no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="c0ebe-118">Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.</span><span class="sxs-lookup"><span data-stu-id="c0ebe-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ebe-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0ebe-119">See also</span></span>

- [<span data-ttu-id="c0ebe-120">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c0ebe-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
