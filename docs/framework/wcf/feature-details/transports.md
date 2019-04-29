---
title: Transportes no Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933725"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="797b3-102">Transportes no Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="797b3-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="797b3-103">A camada de transporte é o nível mais baixo da pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="797b3-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="797b3-104">Os transportes principais usados no Windows Communication Foundation (WCF) são HTTP, HTTPS, TCP e pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="797b3-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="797b3-105">Os tópicos nesta seção abordam a escolher entre esses transportes, configurando o transporte e definir propriedades de ajuste.</span><span class="sxs-lookup"><span data-stu-id="797b3-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="797b3-106">O WCF inclui transportes adicionais.</span><span class="sxs-lookup"><span data-stu-id="797b3-106">WCF includes additional transports.</span></span> <span data-ttu-id="797b3-107">Para obter informações sobre o transporte de enfileiramento de mensagens (também conhecido como MSMQ), consulte [sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="797b3-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="797b3-108">Para obter informações sobre o transporte peer-to-peer, consulte [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="797b3-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="797b3-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="797b3-109">In This Section</span></span>  
 [<span data-ttu-id="797b3-110">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="797b3-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="797b3-111">Descreve os três principais transportes e considerações no selecionando uma.</span><span class="sxs-lookup"><span data-stu-id="797b3-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="797b3-112">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="797b3-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="797b3-113">Descreve os fatores a considerar ao escolher um elemento de associação de codificação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="797b3-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="797b3-114">Transferência de mensagem de streaming</span><span class="sxs-lookup"><span data-stu-id="797b3-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="797b3-115">Descreve como configurar a camada de transporte para fazer o streaming.</span><span class="sxs-lookup"><span data-stu-id="797b3-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="797b3-116">Configurando HTTP e HTTPS</span><span class="sxs-lookup"><span data-stu-id="797b3-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="797b3-117">Descreve como configurar o transporte HTTP e HTTPS, elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="797b3-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="797b3-118">Como: Substitua a reserva de URL do WCF com uma reserva restrita</span><span class="sxs-lookup"><span data-stu-id="797b3-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="797b3-119">Descreve como usar reservas WCFURL restringido.</span><span class="sxs-lookup"><span data-stu-id="797b3-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="797b3-120">Cotas de transporte</span><span class="sxs-lookup"><span data-stu-id="797b3-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="797b3-121">Descreve as considerações em definir as cotas disponíveis na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="797b3-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="797b3-122">Trabalhando com NATs e Firewalls</span><span class="sxs-lookup"><span data-stu-id="797b3-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="797b3-123">Descreve como configurar a camada de transporte quando as mensagens são enviadas ou recebidas por trás de um firewall ou quando a conversão de endereços de rede (NAT) estiver presente.</span><span class="sxs-lookup"><span data-stu-id="797b3-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="797b3-124">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="797b3-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="797b3-125">Descreve como usar o componente de compartilhamento de porta NET. TCP do WCF.</span><span class="sxs-lookup"><span data-stu-id="797b3-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="797b3-126">Referência</span><span class="sxs-lookup"><span data-stu-id="797b3-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="797b3-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="797b3-127">Related Sections</span></span>  
 [<span data-ttu-id="797b3-128">Associações</span><span class="sxs-lookup"><span data-stu-id="797b3-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="797b3-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="797b3-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
