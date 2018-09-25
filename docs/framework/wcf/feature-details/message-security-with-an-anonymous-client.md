---
title: Mensagem de segurança com um cliente anônimo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
author: BrucePerlerMS
ms.openlocfilehash: f488d2e840ec2524f0cde8dc4b3e6c1cd10c554e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090020"
---
# <a name="message-security-with-an-anonymous-client"></a>Mensagem de segurança com um cliente anônimo
O cenário a seguir mostra um cliente e serviço protegidos pela segurança de mensagem do Windows Communication Foundation (WCF). Uma meta de design é usar segurança de mensagem em vez de segurança de transporte, para que no futuro ele pode dar suporte a um modelo mais avançado baseado em declarações. Para obter mais informações sobre como usar rica de declarações para autorização, consulte [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Para um aplicativo de exemplo, consulte [mensagem de segurança anônima](../../../../docs/framework/wcf/samples/message-security-anonymous.md).  
  
 ![Segurança com um cliente anônimo da mensagem](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Mensagem|  
|Interoperabilidade|Somente o WCF|  
|Autenticação (servidor)|Negociação inicial exige a autenticação do servidor, mas não a autenticação do cliente|  
|Autenticação (cliente)|Nenhum|  
|Integridade|Sim, usando o contexto de segurança compartilhado|  
|Confidencialidade|Sim, usando o contexto de segurança compartilhado|  
|Transporte|HTTP|  
  
## <a name="service"></a>Serviço  
 O código e a configuração a seguir destinam-se para executar de forma independente. Realize um dos seguintes procedimentos:  
  
-   Crie um serviço autônomo usando o código sem nenhuma configuração.  
  
-   Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto de extremidade de serviço que usa segurança de mensagem.  
  
 [!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
 [!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]  
  
### <a name="configuration"></a>Configuração  
 A configuração a seguir pode ser usada em vez do código. O elemento de comportamento de serviço é usado para especificar um certificado que é usado para autenticar o serviço ao cliente. O elemento de serviço deve especificar o comportamento usando o `behaviorConfiguration` atributo. O elemento de associação Especifica que o tipo de credencial de cliente `None`, permitindo que os clientes anônimos usar o serviço.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="CalculatorService"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
 O código e a configuração a seguir destinam-se para executar de forma independente. Realize um dos seguintes procedimentos:  
  
-   Crie um cliente autônomo usando o código (e o código do cliente).  
  
-   Crie um cliente que não define os endereços de ponto de extremidade. Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento. Por exemplo:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Código  
 O código a seguir cria uma instância do cliente. A associação usa segurança de modo de mensagem e o tipo de credencial de cliente é definido como none.  
  
 [!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
 [!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]  
  
### <a name="configuration"></a>Configuração  
 O código a seguir configura o cliente.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_ICalculator"   
        contract="ICalculator"  
        name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Segurança de aplicativos distribuídos](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)  
 [Segurança de mensagem anônima](../../../../docs/framework/wcf/samples/message-security-anonymous.md)  
 [Autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
