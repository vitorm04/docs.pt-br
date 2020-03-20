---
title: Como configurar um serviço do Windows Communication Foundation para utilizar o compartilhamento de porta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: cd8d76137ac195e452a7d66fb6ddbeda405a922f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185099"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Como configurar um serviço do Windows Communication Foundation para utilizar o compartilhamento de porta
A maneira mais fácil de usar o compartilhamento de portas net.tcp://em seu aplicativo <xref:System.ServiceModel.NetTcpBinding>Windows Communication Foundation (WCF) é expor um serviço usando o .  
  
 Essa vinculação <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> fornece uma propriedade que controla se o compartilhamento de porta net.tcp://está habilitado para que o serviço esteja configurado com essa vinculação.  
  
 O procedimento a seguir <xref:System.ServiceModel.NetTcpBinding> mostra como usar a classe para abrir um ponto final no Uniform Resource Identifier (URI) net.tcp://localhost/MyService, primeiro em código e depois usando elementos de configuração.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Para habilitar net.tcp:// compartilhamento de porta em um NetTcpBinding em código  
  
1. Crie um serviço para `IMyService` implementar um `MyService`contrato chamado e chamá-lo de . .  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Crie uma instância <xref:System.ServiceModel.NetTcpBinding> da classe <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> e `true`defina a propriedade para .  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Crie <xref:System.ServiceModel.ServiceHost> e adicione o ponto final `MyService` do serviço para que <xref:System.ServiceModel.NetTcpBinding> use o compartilhamento de portas ativado e que ouça no endereço final URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > Este exemplo usa a porta TCP padrão de 808 porque o uri de endereço de ponto final não especifica um número de porta diferente. Como o compartilhamento portuário está explicitamente habilitado na vinculação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos. Se o compartilhamento portuário não fosse permitido e outro aplicativo já <xref:System.ServiceModel.AddressAlreadyInUseException> estivesse usando a porta 808, este serviço seria um quando fosse aberto.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Para habilitar net.tcp:// compartilhamento de porta em um NetTcpBinding na configuração  
  
1. O exemplo a seguir mostra como ativar o compartilhamento de portas e adicionar o ponto final do serviço usando elementos de configuração.  
  
```xml  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Confira também

- [Compartilhamento de porta Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Como habilitar o serviço de compartilhamento de porta Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
