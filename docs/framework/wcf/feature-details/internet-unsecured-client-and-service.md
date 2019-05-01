---
title: Serviço e cliente de internet desprotegido
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: ca6b028ef20095d6faeb125151772eedf1500fa0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038721"
---
# <a name="internet-unsecured-client-and-service"></a>Serviço e cliente de internet desprotegido
A ilustração a seguir mostra um exemplo de um público, não segura cliente do Windows Communication Foundation (WCF) e serviço:  
  
 ![Captura de tela que mostra um cenário de Internet desprotegido](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|Característica|Descrição|  
|--------------------|-----------------|  
|Modo de segurança|Nenhum|  
|Transporte|HTTP|  
|Associação|<xref:System.ServiceModel.BasicHttpBinding> no código, ou o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento na configuração.|  
|Interoperabilidade|Com os serviços e clientes de serviço Web existentes|  
|Autenticação|Nenhum|  
|Integridade|Nenhum|  
|Confidencialidade|Nenhum|  
  
## <a name="service"></a>Serviço  
 O código e a configuração a seguir destinam-se para executar de forma independente. Realize um dos seguintes procedimentos:  
  
- Crie um serviço autônomo usando o código sem nenhuma configuração.  
  
- Criar um serviço usando a configuração fornecida, mas não definir nenhum ponto de extremidade.  
  
### <a name="code"></a>Código  
 O código a seguir mostra como criar um ponto de extremidade sem segurança. Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> tem o modo de segurança definido como <xref:System.ServiceModel.BasicHttpSecurityMode.None>.  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a>Configuração de Serviço  
 O código a seguir define o mesmo ponto de extremidade usando a configuração.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"   
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>Cliente  
 O código e a configuração a seguir destinam-se para executar de forma independente. Realize um dos seguintes procedimentos:  
  
- Crie um cliente autônomo usando o código (e o código do cliente).  
  
- Crie um cliente que não define os endereços de ponto de extremidade. Em vez disso, use o construtor de cliente que usa o nome da configuração como um argumento. Por exemplo:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Código  
 O código a seguir mostra um cliente WCF básico que acessa um ponto de extremidade não seguro.  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a>Configuração do cliente  
 O código a seguir configura o cliente.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"   
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"   
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Cenários comuns de segurança](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
- [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
