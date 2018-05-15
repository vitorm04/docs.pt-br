---
title: Associações personalizadas
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
ms.openlocfilehash: 6880b04a3f8a82c1e109c32674804c5241913a8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-bindings"></a><span data-ttu-id="d53d8-102">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d53d8-102">Custom Bindings</span></span>
<span data-ttu-id="d53d8-103">Você pode usar o <xref:System.ServiceModel.Channels.CustomBinding> classe quando uma das associações fornecidas pelo sistema não atende aos requisitos de seu serviço.</span><span class="sxs-lookup"><span data-stu-id="d53d8-103">You can use the <xref:System.ServiceModel.Channels.CustomBinding> class when one of the system-provided bindings does not meet the requirements of your service.</span></span> <span data-ttu-id="d53d8-104">Todas as associações são construídas a partir de um conjunto ordenado de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="d53d8-104">All bindings are constructed from an ordered set of binding elements.</span></span> <span data-ttu-id="d53d8-105">Associações personalizadas podem ser criadas a partir de um conjunto de elementos de associação fornecida pelo sistema ou podem incluir elementos de associação personalizada definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d53d8-105">Custom bindings can be built from a set of system-provided binding elements or can include user-defined custom binding elements.</span></span> <span data-ttu-id="d53d8-106">Você pode usar elementos de associação personalizada, por exemplo, para habilitar o uso de novos transportes ou codificadores em um ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="d53d8-106">You can use custom binding elements, for example, to enable the use of new transports or encoders at a service endpoint.</span></span> <span data-ttu-id="d53d8-107">Para obter exemplos de funcionamento, consulte [amostras de associação personalizado](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span><span class="sxs-lookup"><span data-stu-id="d53d8-107">For working examples, see [Custom Binding Samples](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08).</span></span> <span data-ttu-id="d53d8-108">Para obter mais informações, consulte [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="d53d8-108">For more information, see [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
## <a name="construction-of-a-custom-binding"></a><span data-ttu-id="d53d8-109">Construção de uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="d53d8-109">Construction of a Custom Binding</span></span>  
 <span data-ttu-id="d53d8-110">Uma associação personalizada é criada usando o <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> construtor de uma coleção de elementos que estão "empilhados" em uma ordem específica de associação:</span><span class="sxs-lookup"><span data-stu-id="d53d8-110">A custom binding is constructed using the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor from a collection of binding elements that are "stacked" in a specific order:</span></span>  
  
-   <span data-ttu-id="d53d8-111">Na parte superior é um recurso opcional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> classe que permite que o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="d53d8-111">At the top is an optional <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> class that allows flowing transactions.</span></span>  
  
-   <span data-ttu-id="d53d8-112">Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> classe que fornece uma sessão e mecanismos de ordenação, conforme definido na especificação WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="d53d8-112">Next is an optional <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> class that provides a session and ordering mechanisms as defined in the WS-ReliableMessaging specification.</span></span> <span data-ttu-id="d53d8-113">Uma sessão pode cruzar com intermediários SOAP e transporte.</span><span class="sxs-lookup"><span data-stu-id="d53d8-113">A session can cross SOAP and transport intermediaries.</span></span>  
  
-   <span data-ttu-id="d53d8-114">Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.SecurityBindingElement> classe que fornece recursos de segurança como autenticação, autorização, proteção e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="d53d8-114">Next is an optional <xref:System.ServiceModel.Channels.SecurityBindingElement> class that provides security features such as authorization, authentication, protection, and confidentiality.</span></span>  
  
-   <span data-ttu-id="d53d8-115">Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> classe que fornece a capacidade de ter dois comunicação duplex forma com um protocolo de transporte que não oferecem suporte à comunicação duplex nativamente, como HTTP.</span><span class="sxs-lookup"><span data-stu-id="d53d8-115">Next is an optional <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> class that provides the ability to have two way duplex communication with a transport protocol that does not support duplex communication natively, such as HTTP.</span></span>  
  
-   <span data-ttu-id="d53d8-116">Em seguida, é um recurso opcional <xref:System.ServiceModel.Channels.OneWayBindingElement>) classe que fornece comunicação unidirecional.</span><span class="sxs-lookup"><span data-stu-id="d53d8-116">Next is an optional <xref:System.ServiceModel.Channels.OneWayBindingElement>) class that provides one-way communication.</span></span>  
  
-   <span data-ttu-id="d53d8-117">Em seguida, é um elemento de associação de segurança de fluxo opcional que pode ser um destes procedimentos.</span><span class="sxs-lookup"><span data-stu-id="d53d8-117">Next is an optional stream security binding element which can be one of the following.</span></span>  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   <span data-ttu-id="d53d8-118">Em seguida, é um elemento de associação de codificação de mensagem necessário.</span><span class="sxs-lookup"><span data-stu-id="d53d8-118">Next is a required message encoding binding element.</span></span> <span data-ttu-id="d53d8-119">Você pode usar seu próprio codificador de mensagem ou uma das três associações de codificação de mensagem:</span><span class="sxs-lookup"><span data-stu-id="d53d8-119">You can use your own message encoder or one of the three message encoding bindings:</span></span>  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 <span data-ttu-id="d53d8-120">Na parte inferior é um elemento de transporte necessário.</span><span class="sxs-lookup"><span data-stu-id="d53d8-120">At the bottom is a required transport element.</span></span> <span data-ttu-id="d53d8-121">Você pode usar seu próprio transporte ou um dos seguintes elementos de associação de transporte Windows Communication Foundation (WCF) fornece:</span><span class="sxs-lookup"><span data-stu-id="d53d8-121">You can use your own transport or one of the following transport binding elements Windows Communication Foundation (WCF) provides:</span></span>  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 <span data-ttu-id="d53d8-122">A tabela a seguir resume as opções para cada camada.</span><span class="sxs-lookup"><span data-stu-id="d53d8-122">The following table summarizes the options for each layer.</span></span>  
  
|<span data-ttu-id="d53d8-123">Camada</span><span class="sxs-lookup"><span data-stu-id="d53d8-123">Layer</span></span>|<span data-ttu-id="d53d8-124">Opções</span><span class="sxs-lookup"><span data-stu-id="d53d8-124">Options</span></span>|<span data-ttu-id="d53d8-125">Necessária</span><span class="sxs-lookup"><span data-stu-id="d53d8-125">Required</span></span>|  
|-----------|-------------|--------------|  
|<span data-ttu-id="d53d8-126">Transações</span><span class="sxs-lookup"><span data-stu-id="d53d8-126">Transactions</span></span>|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|<span data-ttu-id="d53d8-127">Não</span><span class="sxs-lookup"><span data-stu-id="d53d8-127">No</span></span>|  
|<span data-ttu-id="d53d8-128">Confiabilidade</span><span class="sxs-lookup"><span data-stu-id="d53d8-128">Reliability</span></span>|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|<span data-ttu-id="d53d8-129">Não</span><span class="sxs-lookup"><span data-stu-id="d53d8-129">No</span></span>|  
|<span data-ttu-id="d53d8-130">Segurança</span><span class="sxs-lookup"><span data-stu-id="d53d8-130">Security</span></span>|<xref:System.ServiceModel.Channels.SecurityBindingElement>|<span data-ttu-id="d53d8-131">Não</span><span class="sxs-lookup"><span data-stu-id="d53d8-131">No</span></span>|  
|<span data-ttu-id="d53d8-132">Codificando</span><span class="sxs-lookup"><span data-stu-id="d53d8-132">Encoding</span></span>|<span data-ttu-id="d53d8-133">Texto, personalizada de binário, mensagem de transmissão de otimização do mecanismo (MTOM)</span><span class="sxs-lookup"><span data-stu-id="d53d8-133">Text, binary, Message Transmission Optimization Mechanism (MTOM), custom</span></span>|<span data-ttu-id="d53d8-134">Sim</span><span class="sxs-lookup"><span data-stu-id="d53d8-134">Yes</span></span>|  
|<span data-ttu-id="d53d8-135">Transporte</span><span class="sxs-lookup"><span data-stu-id="d53d8-135">Transport</span></span>|<span data-ttu-id="d53d8-136">TCP, HTTP, HTTPS, chamado pipes (também conhecido como IPC), ponto a ponto (P2P), o serviço de enfileiramento de mensagens (também conhecido como MSMQ), personalizado</span><span class="sxs-lookup"><span data-stu-id="d53d8-136">TCP, HTTP, HTTPS, named pipes (also known as IPC), Peer-to-Peer (P2P), Message Queuing (also known as MSMQ), Custom</span></span>|<span data-ttu-id="d53d8-137">Sim</span><span class="sxs-lookup"><span data-stu-id="d53d8-137">Yes</span></span>|  
  
 <span data-ttu-id="d53d8-138">Além disso, você pode definir seus próprios elementos de associação e inseri-los entre qualquer uma das camadas de definido anteriores.</span><span class="sxs-lookup"><span data-stu-id="d53d8-138">In addition, you can define your own binding elements and insert them between any of the preceding defined layers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53d8-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d53d8-139">See Also</span></span>  
 [<span data-ttu-id="d53d8-140">Visão geral de criação de ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="d53d8-140">Endpoint Creation Overview</span></span>](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="d53d8-141">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d53d8-141">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="d53d8-142">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d53d8-142">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="d53d8-143">Como personalizar uma associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d53d8-143">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [<span data-ttu-id="d53d8-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="d53d8-144">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="d53d8-145">Associação personalizada</span><span class="sxs-lookup"><span data-stu-id="d53d8-145">Custom Binding</span></span>](../../../../docs/framework/wcf/samples/custom-binding.md)
