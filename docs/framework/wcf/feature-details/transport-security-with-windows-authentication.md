---
title: Segurança de transporte com autenticação do Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: d335cd47de68dccdbb6af7f402d1182fcd811a7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184308"
---
# <a name="transport-security-with-windows-authentication"></a>Segurança de transporte com autenticação do Windows
O cenário a seguir mostra um cliente e serviço da Windows Communication Foundation (WCF) protegido pela segurança do Windows. Para obter mais informações sobre programação, consulte [Como: Proteger um serviço com credenciais do Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).  
  
 Um serviço web intranet exibe informações sobre recursos humanos. O cliente é um aplicativo do Windows Form. O aplicativo é implantado em um domínio com um controlador Kerberos protegendo o domínio.  
  
 ![Segurança de transporte com autenticação do Windows](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Transporte|  
|Interoperabilidade|Somente WCF|  
|Autenticação (Servidor)<br /><br /> Autenticação (Cliente)|Sim (usando autenticação integrada do Windows)<br /><br /> Sim (usando autenticação integrada do Windows)|  
|Integridade|Sim|  
|Confidencialidade|Sim|  
|Transporte|Net. Tcp|  
|Associação|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a>Serviço  
 O seguinte código e configuração devem ser executados independentemente. Realize um dos seguintes procedimentos:  
  
- Crie um serviço autônomo usando o código sem configuração.  
  
- Crie um serviço usando a configuração fornecida, mas não defina nenhum ponto final.  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto final de serviço que usa uma segurança do Windows.  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a>Configuração  
 A configuração a seguir pode ser usada em vez do código para configurar o ponto final do serviço:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
 O seguinte código e configuração devem ser executados independentemente. Realize um dos seguintes procedimentos:  
  
- Crie um cliente autônomo usando o código (e o código do cliente).  
  
- Crie um cliente que não defina nenhum endereço de ponto final. Em vez disso, use o construtor cliente que toma o nome da configuração como argumento. Por exemplo:   
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Código  
 O código a seguir cria o cliente. A vinculação é configurada para usar a segurança do modo transporte, com o transporte TCP, com o tipo de credencial do cliente definido como Windows.  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a>Configuração  
 A configuração a seguir pode ser usada em vez do código para criar o cliente.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Visão geral da segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Como proteger um serviço com credenciais Windows](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- [Modelo de segurança para a malha do aplicativo do Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
