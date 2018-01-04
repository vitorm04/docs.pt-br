---
title: "Como fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa6f9d0b9631420013593cb44903b5451549e8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="38473-102">Como fazer intercâmbio de mensagens com pontos de extremidade do WCF e aplicativos de enfileiramento de mensagens</span><span class="sxs-lookup"><span data-stu-id="38473-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="38473-103">Você pode integrar aplicativos existentes do serviço de enfileiramento de mensagens (MSMQ) com [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativos usando a associação de integração do MSMQ para converter as mensagens MSMQ em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens.</span><span class="sxs-lookup"><span data-stu-id="38473-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="38473-104">Isso permite que você chame em aplicativos de receptor MSMQ de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes, bem como chamar em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços de aplicativos de remetente do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="38473-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="38473-105">Nesta seção, explicaremos como usar <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> para comunicação em fila entre (1) um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e um serviço de aplicativo do MSMQ gravadas usando System. Messaging e (2) um cliente de aplicativo do MSMQ e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="38473-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="38473-106">Para obter um exemplo completo que demonstra como chamar um aplicativo receptor MSMQ um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente, consulte o [Windows Communication Foundation para enfileiramento](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="38473-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="38473-107">Para obter um exemplo completo que demonstra como chamar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de serviço de um cliente do MSMQ, consulte o [enfileiramento de mensagens para o Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="38473-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="38473-108">Para criar um serviço WCF que recebe mensagens de um cliente do MSMQ</span><span class="sxs-lookup"><span data-stu-id="38473-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="38473-109">Define uma interface que define o contrato de serviço para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que recebe as mensagens na fila de um aplicativo de remetente do MSMQ, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="38473-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="38473-110">Implementa a interface e aplique o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo à classe, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="38473-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="38473-111">Criar um arquivo de configuração que especifica o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="38473-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="38473-112">Criar uma instância de um <xref:System.ServiceModel.ServiceHost> objeto que usa a associação configurada.</span><span class="sxs-lookup"><span data-stu-id="38473-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="38473-113">Para criar um cliente do WCF que envia mensagens a um aplicativo de destinatário do MSMQ</span><span class="sxs-lookup"><span data-stu-id="38473-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="38473-114">Define uma interface que define o contrato de serviço para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que envia na fila de mensagens do receptor do MSMQ, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="38473-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="38473-115">Definir um cliente de classe que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usa para chamar o receptor do MSMQ.</span><span class="sxs-lookup"><span data-stu-id="38473-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="38473-116">Crie uma configuração que especifica o uso da ligação MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="38473-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="38473-117">Criar uma instância da classe do cliente e chame o método definido pelo serviço de recebimento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="38473-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="38473-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38473-118">See Also</span></span>  
 [<span data-ttu-id="38473-119">Visão geral de filas</span><span class="sxs-lookup"><span data-stu-id="38473-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="38473-120">Como trocar mensagens na fila com pontos de extremidade do WCF</span><span class="sxs-lookup"><span data-stu-id="38473-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="38473-121">Windows Communication Foundation para Enfileiramento de Mensagens</span><span class="sxs-lookup"><span data-stu-id="38473-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="38473-122">Instalando o Enfileiramento de Mensagens (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="38473-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="38473-123">Enfileiramento de mensagens para o Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="38473-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="38473-124">Segurança de mensagem através do enfileiramento de mensagem</span><span class="sxs-lookup"><span data-stu-id="38473-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
