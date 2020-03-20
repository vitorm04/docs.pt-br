---
title: Segurança de transporte com autenticação básica
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 1b2b451eb1ea6a1a49ce1ba8cc1edef1fe72d01b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184349"
---
# <a name="transport-security-with-basic-authentication"></a>Segurança de transporte com autenticação básica
A ilustração a seguir mostra um serviço e cliente da Windows Communication Foundation (WCF). O servidor precisa de um certificado X.509 válido que pode ser usado para ssl (Secure Sockets Layer, camada de soquetes seguros) e os clientes devem confiar no certificado do servidor. Além disso, o serviço Web já possui uma implementação SSL que pode ser usada. Para obter mais informações sobre como ativar a autenticação <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>básica no Internet Information Services (IIS), consulte .  
  
 ![Captura de tela que mostra a segurança do transporte com autenticação básica.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Transporte|  
|Interoperabilidade|Com clientes e serviços de serviços web existentes|  
|Autenticação (Servidor)<br /><br /> Autenticação (Cliente)|Sim (usando HTTPS)<br /><br /> Sim (através do nome de usuário/senha)|  
|Integridade|Sim|  
|Confidencialidade|Sim|  
|Transporte|HTTPS|  
|Associação|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Serviço  
 O seguinte código e configuração devem ser executados independentemente. Realize um dos seguintes procedimentos:  
  
- Crie um serviço autônomo usando o código sem configuração.  
  
- Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto final de serviço que usa um nome de usuário de domínio do Windows e senha para segurança de transferência. Observe que o serviço requer um certificado X.509 para autenticar ao cliente. Para obter mais informações, consulte [Trabalhando com Certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) e [Como: Configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Configuração  
 O seguinte configura um serviço para usar autenticação básica com segurança de nível de transporte:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
  
### <a name="code"></a>Código  
 O código a seguir mostra o código do cliente que inclui o nome de usuário e a senha. Observe que o usuário deve fornecer um nome de usuário e senha válidos do Windows. O código para retornar o nome de usuário e senha não é mostrado aqui. Use uma caixa de diálogo ou outra interface para consultar o usuário para obter as informações.  
  
> [!NOTE]
> Nome de usuário e senha só podem ser definidos usando código.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Configuração  
 O código a seguir mostra a configuração do cliente.  
  
> [!NOTE]
> Não é possível usar a configuração para definir o nome de usuário e a senha. A configuração mostrada aqui deve ser aumentada usando código para definir o nome de usuário e senha.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Como configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Visão geral da segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [\<>de credenciais de clientes](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
