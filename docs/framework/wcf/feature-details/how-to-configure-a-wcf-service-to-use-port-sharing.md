---
title: Como configurar um serviço do Windows Communication Foundation para utilizar o compartilhamento de porta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 0a3aca2bac546c9142137afc025133bc1154ff90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Como configurar um serviço do Windows Communication Foundation para utilizar o compartilhamento de porta
É a maneira mais fácil de usar em seu aplicativo do Windows Communication Foundation (WCF) de compartilhamento de porta net.tcp:// para expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding>.  
  
 Essa associação fornece um <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade que controla se o compartilhamento de porta net.tcp:// está habilitado para o serviço que está sendo configurado com essa associação.  
  
 O procedimento a seguir mostra como usar o <xref:System.ServiceModel.NetTcpBinding> classe para abrir um ponto de extremidade em net.tcp://localhost/MyService o identificador de recurso uniforme (URI), primeiro no código e, em seguida, usando os elementos de configuração.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Para habilitar a porta net.tcp:// compartilhamento em um NetTcpBinding no código  
  
1.  Criar um serviço para implementar um contrato denominado `IMyService` e chamá-lo `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina o <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  Criar um <xref:System.ServiceModel.ServiceHost> e adicione o ponto de extremidade de serviço, para `MyService` que usa a porta habilitado compartilhamento <xref:System.ServiceModel.NetTcpBinding> e que escuta no ponto de extremidade endereço URI "net.tcp://localhost/MyService".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  Este exemplo usa a porta padrão TCP 808 porque o endereço de ponto de extremidade URI não especificar um número de porta diferente. Porque o compartilhamento de porta é explicitamente habilitado na associação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos. Se o compartilhamento de porta não eram permitidos e outro aplicativo já estava usando a porta 808, esse serviço lançaria uma <xref:System.ServiceModel.AddressAlreadyInUseException> quando ela foi aberta.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a>Para habilitar o compartilhamento em um NetTcpBinding na configuração de porta de net.tcp://  
  
1.  O exemplo a seguir mostra como habilitar o compartilhamento de porta e adicionar o ponto de extremidade de serviço usando os elementos de configuração.  
  
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
 [Compartilhamento de porta do NET.TCP](http://msdn.microsoft.com/library/f13692ee-a179-4439-ae72-50db9534eded)  
 [Como habilitar o serviço de compartilhamento de porta do NET.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
