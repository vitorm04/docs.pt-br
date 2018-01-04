---
title: Transportes no Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62eb27919e762004667b3d5179c35cb04d9a9422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="668d8-102">Transportes no Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="668d8-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="668d8-103">A camada de transporte é o nível mais baixo da pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="668d8-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="668d8-104">Os transportes principais usados em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] são HTTP, HTTPS, TCP e pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="668d8-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="668d8-105">Os tópicos nesta seção abordam escolhendo entre esses transportes, configurando o transporte e definir propriedades de ajuste.</span><span class="sxs-lookup"><span data-stu-id="668d8-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="668d8-106">inclui transportes adicionais.</span><span class="sxs-lookup"><span data-stu-id="668d8-106"> includes additional transports.</span></span> <span data-ttu-id="668d8-107">Para obter informações sobre o transporte de enfileiramento de mensagens (também conhecido como MSMQ), consulte [sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="668d8-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="668d8-108">Para obter informações sobre o transporte de ponto a ponto, consulte [rede ponto a ponto](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="668d8-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="668d8-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="668d8-109">In This Section</span></span>  
 [<span data-ttu-id="668d8-110">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="668d8-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="668d8-111">Descreve os três principais transportes e considerações ao selecionar um.</span><span class="sxs-lookup"><span data-stu-id="668d8-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="668d8-112">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="668d8-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="668d8-113">Descreve os fatores a considerar ao escolher um elemento de associação de codificação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="668d8-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="668d8-114">Transferência de mensagem de streaming</span><span class="sxs-lookup"><span data-stu-id="668d8-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="668d8-115">Descreve como configurar a camada de transporte para fazer o streaming.</span><span class="sxs-lookup"><span data-stu-id="668d8-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="668d8-116">Configurando HTTP e HTTPS</span><span class="sxs-lookup"><span data-stu-id="668d8-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="668d8-117">Descreve como configurar o transporte HTTP e HTTPS, elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="668d8-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="668d8-118">Como substituir a reserva de URL do WCF com uma reserva restrita</span><span class="sxs-lookup"><span data-stu-id="668d8-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="668d8-119">Descreve como usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restrito reservas.</span><span class="sxs-lookup"><span data-stu-id="668d8-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="668d8-120">Cotas de transporte</span><span class="sxs-lookup"><span data-stu-id="668d8-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="668d8-121">Descreve considerações ao configurar as cotas disponíveis na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="668d8-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="668d8-122">Trabalhando com NATs e Firewalls</span><span class="sxs-lookup"><span data-stu-id="668d8-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="668d8-123">Descreve como configurar a camada de transporte quando mensagens são enviadas ou recebidas por trás de um firewall ou a conversão de endereços de rede (NAT) está presente.</span><span class="sxs-lookup"><span data-stu-id="668d8-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="668d8-124">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="668d8-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="668d8-125">Descreve como usar o componente de compartilhamento de porta NET. TCP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="668d8-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="668d8-126">Referência</span><span class="sxs-lookup"><span data-stu-id="668d8-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="668d8-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="668d8-127">Related Sections</span></span>  
 [<span data-ttu-id="668d8-128">Associações</span><span class="sxs-lookup"><span data-stu-id="668d8-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="668d8-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="668d8-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
