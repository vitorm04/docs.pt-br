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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="6b2ec-102">Como configurar um serviço do Windows Communication Foundation para utilizar o compartilhamento de porta</span><span class="sxs-lookup"><span data-stu-id="6b2ec-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="6b2ec-103">A maneira mais fácil de usar o compartilhamento de portas net.tcp://em seu aplicativo <xref:System.ServiceModel.NetTcpBinding>Windows Communication Foundation (WCF) é expor um serviço usando o .</span><span class="sxs-lookup"><span data-stu-id="6b2ec-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="6b2ec-104">Essa vinculação <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> fornece uma propriedade que controla se o compartilhamento de porta net.tcp://está habilitado para que o serviço esteja configurado com essa vinculação.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="6b2ec-105">O procedimento a seguir <xref:System.ServiceModel.NetTcpBinding> mostra como usar a classe para abrir um ponto final no Uniform Resource Identifier (URI) net.tcp://localhost/MyService, primeiro em código e depois usando elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="6b2ec-106">Para habilitar net.tcp:// compartilhamento de porta em um NetTcpBinding em código</span><span class="sxs-lookup"><span data-stu-id="6b2ec-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="6b2ec-107">Crie um serviço para `IMyService` implementar um `MyService`contrato chamado e chamá-lo de . .</span><span class="sxs-lookup"><span data-stu-id="6b2ec-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="6b2ec-108">Crie uma instância <xref:System.ServiceModel.NetTcpBinding> da classe <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> e `true`defina a propriedade para .</span><span class="sxs-lookup"><span data-stu-id="6b2ec-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="6b2ec-109">Crie <xref:System.ServiceModel.ServiceHost> e adicione o ponto final `MyService` do serviço para que <xref:System.ServiceModel.NetTcpBinding> use o compartilhamento de portas ativado e que ouça no endereço final URI "net.tcp://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="6b2ec-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="6b2ec-110">Este exemplo usa a porta TCP padrão de 808 porque o uri de endereço de ponto final não especifica um número de porta diferente.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="6b2ec-111">Como o compartilhamento portuário está explicitamente habilitado na vinculação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="6b2ec-112">Se o compartilhamento portuário não fosse permitido e outro aplicativo já <xref:System.ServiceModel.AddressAlreadyInUseException> estivesse usando a porta 808, este serviço seria um quando fosse aberto.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="6b2ec-113">Para habilitar net.tcp:// compartilhamento de porta em um NetTcpBinding na configuração</span><span class="sxs-lookup"><span data-stu-id="6b2ec-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="6b2ec-114">O exemplo a seguir mostra como ativar o compartilhamento de portas e adicionar o ponto final do serviço usando elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="6b2ec-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b2ec-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="6b2ec-115">See also</span></span>

- [<span data-ttu-id="6b2ec-116">Compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="6b2ec-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="6b2ec-117">Como habilitar o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="6b2ec-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
