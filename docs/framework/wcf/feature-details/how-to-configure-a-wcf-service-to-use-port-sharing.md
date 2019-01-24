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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="9151c-102">Como: Configurar um serviço do Windows Communication Foundation para usar compartilhamento de porta</span><span class="sxs-lookup"><span data-stu-id="9151c-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="9151c-103">A maneira mais fácil de usar em seu aplicativo do Windows Communication Foundation (WCF) de compartilhamento de porta net.tcp:// é expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="9151c-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="9151c-104">Essa associação fornece uma <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade que controla se o compartilhamento de porta net.tcp:// está habilitado para o serviço que está sendo configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="9151c-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="9151c-105">O procedimento a seguir mostra como usar o <xref:System.ServiceModel.NetTcpBinding> classe para abrir um ponto de extremidade em net.tcp://localhost/MyService o identificador de recurso uniforme (URI), pela primeira vez no código e, em seguida, usando os elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="9151c-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="9151c-106">Para habilitar a porta net.tcp:// compartilhamento em um NetTcpBinding no código</span><span class="sxs-lookup"><span data-stu-id="9151c-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1.  <span data-ttu-id="9151c-107">Criar um serviço para implementar um contrato denominado `IMyService` e chamá-lo `MyService`,.</span><span class="sxs-lookup"><span data-stu-id="9151c-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <span data-ttu-id="9151c-108">Criar uma instância do <xref:System.ServiceModel.NetTcpBinding> de classe e defina a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="9151c-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <span data-ttu-id="9151c-109">Criar uma <xref:System.ServiceModel.ServiceHost> e adicione o ponto de extremidade de serviço a ele para `MyService` que usa a porta de compartilhamento habilitado <xref:System.ServiceModel.NetTcpBinding> e que escuta no ponto de extremidade de endereço net.tcp://localhost/MyService"URI".</span><span class="sxs-lookup"><span data-stu-id="9151c-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="9151c-110">Este exemplo usa a porta padrão TCP 808 porque o URI de endereço do ponto de extremidade não especifica um número de porta diferente.</span><span class="sxs-lookup"><span data-stu-id="9151c-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="9151c-111">Como o compartilhamento de porta é habilitado explicitamente na associação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos.</span><span class="sxs-lookup"><span data-stu-id="9151c-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="9151c-112">Se o compartilhamento de porta não eram permitidas e o outro aplicativo já estava usando a porta 808, esse serviço lançaria um <xref:System.ServiceModel.AddressAlreadyInUseException> quando ela foi aberta.</span><span class="sxs-lookup"><span data-stu-id="9151c-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="9151c-113">Para habilitar o compartilhamento em um NetTcpBinding na configuração de porta de net.tcp://</span><span class="sxs-lookup"><span data-stu-id="9151c-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1.  <span data-ttu-id="9151c-114">O exemplo a seguir mostra como habilitar o compartilhamento de porta e adicionar o ponto de extremidade de serviço usando os elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="9151c-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9151c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9151c-115">See also</span></span>
- [<span data-ttu-id="9151c-116">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="9151c-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="9151c-117">Como: Habilitar o serviço de compartilhamento de porta NET. TCP</span><span class="sxs-lookup"><span data-stu-id="9151c-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
