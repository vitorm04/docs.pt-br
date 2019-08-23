---
title: 'Como: Configurar um serviço de Windows Communication Foundation para usar o compartilhamento de porta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: e92ce3468bd43456ac3f838cfc44ea7c6624502b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912216"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Como: Configurar um serviço de Windows Communication Foundation para usar o compartilhamento de porta
A maneira mais fácil de usar net. TCP://compartilhamento de porta em seu aplicativo Windows Communication Foundation (WCF) é expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding>.  
  
 Essa associação fornece uma <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade que controla se o compartilhamento de porta Net. TCP://está habilitado para o serviço que está sendo configurado com essa associação.  
  
 O procedimento a seguir mostra como usar a <xref:System.ServiceModel.NetTcpBinding> classe para abrir um ponto de extremidade no Uniform Resource Identifier (URI) net. TCP://localhost/MyService, primeiro no código e, em seguida, usando elementos de configuração.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Para habilitar o compartilhamento net. TCP://porta em um NetTcpbinding no código  
  
1. Crie um serviço para implementar um contrato chamado `IMyService` e chamá- `MyService`lo,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. Crie uma instância da <xref:System.ServiceModel.NetTcpBinding> classe e defina a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> Propriedade como `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. Crie um <xref:System.ServiceModel.ServiceHost> e adicione o ponto de extremidade de serviço `MyService` a ele para que use o compartilhamento <xref:System.ServiceModel.NetTcpBinding> de porta habilitado e que escuta no URI do endereço do ponto de extremidade "net. TCP://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > Este exemplo usa a porta TCP padrão de 808 porque o URI do endereço do ponto de extremidade não especifica um número de porta diferente. Como o compartilhamento de porta está explicitamente habilitado na associação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos. Se o compartilhamento de porta não fosse permitido e outro aplicativo já estava usando a porta 808, esse serviço <xref:System.ServiceModel.AddressAlreadyInUseException> geraria um quando fosse aberto.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Para habilitar o compartilhamento de porta Net. TCP://em uma NetTcpbinding na configuração  
  
1. O exemplo a seguir mostra como habilitar o compartilhamento de porta e adicionar o ponto de extremidade de serviço usando elementos de configuração.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Compartilhamento de porta do NET.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Como: Habilitar o serviço de compartilhamento de porta Net. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
