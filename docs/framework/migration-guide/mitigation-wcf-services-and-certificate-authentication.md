---
title: "Mitigação: serviços WCF e autenticação de certificado | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: 0b32fa96cd002e927fa00e8c2a797d1ff6b17cb8
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
<a id="mitigation-wcf-services-and-certificate-authentication" class="xliff"></a>
# Mitigação: serviços WCF e autenticação de certificado
O .NET Framework 4.6 adiciona o TLS 1.1 e o TLS 1.2 à lista padrão de protocolos SSL do WCF. Quando os computadores cliente e servidor têm o .NET Framework 4.6 ou posteriores instalados, o TLS 1.2 é usado para negociação.  
  
<a id="impact" class="xliff"></a>
## Impacto  
 O TLS 1.2 não dá suporte à autenticação do certificado MD5. Consequentemente, se um cliente usar um certificado SSL que use MD5 para o algoritmo de hash, o cliente WCF falhará ao se conectar ao serviço WCF. Para saber mais, confira [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md) (Mitigação: serviços WCF e autenticação de certificado).  
  
<a id="mitigation" class="xliff"></a>
## Redução  
 Você pode contornar esse problema para que um cliente WCF possa se conectar a um servidor WCF seguindo um destes procedimentos:  
  
-   Atualize o certificado para não usar o algoritmo MD5. Esta é a solução recomendada.  
  
-   Se a associação não tiver sido configurada dinamicamente no código-fonte, atualize o arquivo de configuração de aplicativo para usar o TLS 1.1 ou uma versão anterior do protocolo. Isso permite que você continue usando um certificado com o algoritmo de hash MD5.  
  
    > [!CAUTION]
    >  Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.  
  
     O arquivo de configuração que se segue demonstra isso:  
  
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
  
-   Se a associação foi configurada dinamicamente no código-fonte, atualize a propriedade <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName> para usar o TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=fullName>) ou uma versão anterior do protocolo no código-fonte.  
  
    > [!CAUTION]
    >  Essa solução alternativa não é recomendada, pois um certificado com o algoritmo de hash MD5 é considerado inseguro.  
  
<a id="see-also" class="xliff"></a>
## Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)

