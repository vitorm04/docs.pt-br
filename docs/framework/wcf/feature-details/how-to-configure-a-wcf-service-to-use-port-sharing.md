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
# <a name="how-to-configure-a-windows-communication-foundation-service-to-use-port-sharing"></a><span data-ttu-id="b731c-102">Como: Configurar um serviço de Windows Communication Foundation para usar o compartilhamento de porta</span><span class="sxs-lookup"><span data-stu-id="b731c-102">How to: Configure a Windows Communication Foundation Service to Use Port Sharing</span></span>
<span data-ttu-id="b731c-103">A maneira mais fácil de usar net. TCP://compartilhamento de porta em seu aplicativo Windows Communication Foundation (WCF) é expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="b731c-103">The easiest way to use net.tcp:// port sharing in your Windows Communication Foundation (WCF) application is to expose a service using the <xref:System.ServiceModel.NetTcpBinding>.</span></span>  
  
 <span data-ttu-id="b731c-104">Essa associação fornece uma <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade que controla se o compartilhamento de porta Net. TCP://está habilitado para o serviço que está sendo configurado com essa associação.</span><span class="sxs-lookup"><span data-stu-id="b731c-104">This binding provides a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property that controls whether net.tcp:// port sharing is enabled for the service being configured with this binding.</span></span>  
  
 <span data-ttu-id="b731c-105">O procedimento a seguir mostra como usar a <xref:System.ServiceModel.NetTcpBinding> classe para abrir um ponto de extremidade no Uniform Resource Identifier (URI) net. TCP://localhost/MyService, primeiro no código e, em seguida, usando elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b731c-105">The following procedure shows how to use the <xref:System.ServiceModel.NetTcpBinding> class to open an endpoint at the Uniform Resource Identifier (URI) net.tcp://localhost/MyService, first in code and then by using configuration elements.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-code"></a><span data-ttu-id="b731c-106">Para habilitar o compartilhamento net. TCP://porta em um NetTcpbinding no código</span><span class="sxs-lookup"><span data-stu-id="b731c-106">To enable net.tcp:// port sharing on a NetTcpBinding in code</span></span>  
  
1. <span data-ttu-id="b731c-107">Crie um serviço para implementar um contrato chamado `IMyService` e chamá- `MyService`lo,.</span><span class="sxs-lookup"><span data-stu-id="b731c-107">Create a service to implement a contract called `IMyService` and call it `MyService`, .</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2. <span data-ttu-id="b731c-108">Crie uma instância da <xref:System.ServiceModel.NetTcpBinding> classe e defina a <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> Propriedade como `true`.</span><span class="sxs-lookup"><span data-stu-id="b731c-108">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3. <span data-ttu-id="b731c-109">Crie um <xref:System.ServiceModel.ServiceHost> e adicione o ponto de extremidade de serviço `MyService` a ele para que use o compartilhamento <xref:System.ServiceModel.NetTcpBinding> de porta habilitado e que escuta no URI do endereço do ponto de extremidade "net. TCP://localhost/MyService".</span><span class="sxs-lookup"><span data-stu-id="b731c-109">Create a <xref:System.ServiceModel.ServiceHost> and add the service endpoint to it for `MyService` that uses the port sharing-enabled <xref:System.ServiceModel.NetTcpBinding> and that listens at the endpoint address URI "net.tcp://localhost/MyService".</span></span>  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    > <span data-ttu-id="b731c-110">Este exemplo usa a porta TCP padrão de 808 porque o URI do endereço do ponto de extremidade não especifica um número de porta diferente.</span><span class="sxs-lookup"><span data-stu-id="b731c-110">This example uses the default TCP port of 808 because the endpoint address URI does not specify a different port number.</span></span> <span data-ttu-id="b731c-111">Como o compartilhamento de porta está explicitamente habilitado na associação de transporte, esse serviço pode compartilhar a porta 808 com outros serviços em outros processos.</span><span class="sxs-lookup"><span data-stu-id="b731c-111">Because port sharing is explicitly enabled on the transport binding, this service can share port 808 with other services in other processes.</span></span> <span data-ttu-id="b731c-112">Se o compartilhamento de porta não fosse permitido e outro aplicativo já estava usando a porta 808, esse serviço <xref:System.ServiceModel.AddressAlreadyInUseException> geraria um quando fosse aberto.</span><span class="sxs-lookup"><span data-stu-id="b731c-112">If port sharing were not allowed and another application were already using port 808, this service would throw an <xref:System.ServiceModel.AddressAlreadyInUseException> when it was opened.</span></span>  
  
### <a name="to-enable-nettcp-port-sharing-on-a-nettcpbinding-in-configuration"></a><span data-ttu-id="b731c-113">Para habilitar o compartilhamento de porta Net. TCP://em uma NetTcpbinding na configuração</span><span class="sxs-lookup"><span data-stu-id="b731c-113">To enable net.tcp:// port sharing on a NetTcpBinding in configuration</span></span>  
  
1. <span data-ttu-id="b731c-114">O exemplo a seguir mostra como habilitar o compartilhamento de porta e adicionar o ponto de extremidade de serviço usando elementos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b731c-114">The following example shows how to enable port sharing and add the service endpoint using configuration elements.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b731c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b731c-115">See also</span></span>

- [<span data-ttu-id="b731c-116">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="b731c-116">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="b731c-117">Como: Habilitar o serviço de compartilhamento de porta Net. TCP</span><span class="sxs-lookup"><span data-stu-id="b731c-117">How to: Enable the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
