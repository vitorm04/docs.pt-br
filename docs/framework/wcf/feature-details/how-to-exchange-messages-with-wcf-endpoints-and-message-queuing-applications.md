---
title: Como fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 0775de90903aed27a8d0006614a4b6f2d857eee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597092"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="59366-102">Como fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="59366-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="59366-103">Você pode integrar aplicativos MSMQ (enfileiramento de mensagens) existentes com aplicativos Windows Communication Foundation (WCF) usando a associação de integração do MSMQ para converter mensagens MSMQ de e para mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="59366-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="59366-104">Isso permite chamar os aplicativos do receptor MSMQ de clientes WCF, bem como chamar serviços WCF de aplicativos de remetente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="59366-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="59366-105">Nesta seção, explicaremos como usar para a <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> comunicação em fila entre (1) um cliente WCF e um serviço de aplicativo MSMQ escrito usando System. Messaging e (2) um cliente de aplicativo MSMQ e um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="59366-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="59366-106">Para obter um exemplo completo que demonstra como chamar um aplicativo receptor MSMQ de um cliente WCF, consulte a amostra [Windows Communication Foundation para enfileiramento de mensagens](../samples/wcf-to-message-queuing.md) .</span><span class="sxs-lookup"><span data-stu-id="59366-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="59366-107">Para obter um exemplo completo que demonstra como chamar um serviço WCF de um cliente MSMQ, consulte o [enfileiramento de mensagens para Windows Communication Foundation](../samples/message-queuing-to-wcf.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="59366-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="59366-108">Para criar um serviço WCF que recebe mensagens de um cliente MSMQ</span><span class="sxs-lookup"><span data-stu-id="59366-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="59366-109">Defina uma interface que define o contrato de serviço para o serviço WCF que recebe mensagens em fila de um aplicativo remetente MSMQ, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="59366-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="59366-110">Implemente a interface e aplique o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo à classe, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="59366-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="59366-111">Crie um arquivo de configuração que especifique o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .</span><span class="sxs-lookup"><span data-stu-id="59366-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="59366-112">Crie uma instância de um <xref:System.ServiceModel.ServiceHost> objeto que usa a associação configurada.</span><span class="sxs-lookup"><span data-stu-id="59366-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="59366-113">Para criar um cliente WCF que envia mensagens para um aplicativo receptor MSMQ</span><span class="sxs-lookup"><span data-stu-id="59366-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="59366-114">Defina uma interface que define o contrato de serviço para o cliente WCF que envia mensagens enfileiradas para o receptor MSMQ, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="59366-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="59366-115">Defina uma classe de cliente que o cliente WCF usa para chamar o receptor MSMQ.</span><span class="sxs-lookup"><span data-stu-id="59366-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="59366-116">Crie uma configuração que especifique o uso da Associação MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="59366-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="59366-117">Crie uma instância da classe de cliente e chame o método definido pelo serviço de recebimento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="59366-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="59366-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59366-118">See also</span></span>

- [<span data-ttu-id="59366-119">Visão geral de filas</span><span class="sxs-lookup"><span data-stu-id="59366-119">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="59366-120">Como fazer intercâmbio de mensagens em fila com pontos de extremidade do WCF</span><span class="sxs-lookup"><span data-stu-id="59366-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="59366-121">Windows Communication Foundation para enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="59366-121">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="59366-122">Instalando o Enfileiramento de Mensagens (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="59366-122">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="59366-123">Enfileiramento de mensagens para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="59366-123">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="59366-124">Segurança de mensagem através do enfileiramento de mensagem</span><span class="sxs-lookup"><span data-stu-id="59366-124">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
