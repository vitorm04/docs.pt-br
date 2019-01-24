---
title: 'Como: Configurar um serviço do Windows Communication Foundation para usar compartilhamento de porta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
ms.openlocfilehash: 942dea9b745d3dd7cda366ad3e855ddaed0473db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582546"
---
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a>Como: Configurar um serviço do Windows Communication Foundation para usar compartilhamento de porta
A maneira mais fácil de usar em seu aplicativo do Windows Communication Foundation (WCF) de compartilhamento de porta net.tcp:// é expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding>.  
  
 Essa associação fornece uma <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade que controla se o compartilhamento de porta net.tcp:// está habilitado para o serviço que está sendo configurado com essa associação.  
  
 O procedimento a seguir mostra como usar o <xref:System.ServiceModel.NetTcpBinding> classe para abrir um ponto de extremidade em net.tcp://localhost/MyService o identificador de recurso uniforme (URI), pela primeira vez no código e, em seguida, usando os elementos de configuração.  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a>Para habilitar a porta net.tcp:// compartilhamento em um NetTcpBinding no código  
  
1.  Criar um serviço para implementar um contrato denominado `IMyService` e chamá-lo `MyService`,.  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade `true`.  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  Criar uma <xref:System.ServiceModel.ServiceHost> e adicione o ponto de extremidade de serviço a ele para `MyService` que usa a porta de compartilhamento habilitado <xref:System.ServiceModel.NetTcpBinding> e que escuta no ponto de extremidade de endereço net.tcp://localhost/MyService"URI".  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  Este exemplo usa a porta padrão TCP 808 porque o URI de endereço do ponto de extremidade não especifica um número de porta diferente. Como o compartilhamento de porta é habilitado explicitamente na associação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos. Se o compartilhamento de porta não eram permitidas e o outro aplicativo já estava usando a porta 808, esse serviço lançaria um <xref:System.ServiceModel.AddressAlreadyInUseException> quando ela foi aberta.  
  
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
- [Compartilhamento de porta do NET.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Como: Habilitar o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
