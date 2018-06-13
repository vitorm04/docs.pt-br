---
title: Transportes no Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498118"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="90830-102">Transportes no Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="90830-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="90830-103">A camada de transporte é o nível mais baixo da pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="90830-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="90830-104">Os transportes principais usados no Windows Communication Foundation (WCF) são HTTP, HTTPS, TCP e pipes nomeados.</span><span class="sxs-lookup"><span data-stu-id="90830-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="90830-105">Os tópicos nesta seção abordam escolhendo entre esses transportes, configurando o transporte e definir propriedades de ajuste.</span><span class="sxs-lookup"><span data-stu-id="90830-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="90830-106">O WCF inclui transportes adicionais.</span><span class="sxs-lookup"><span data-stu-id="90830-106">WCF includes additional transports.</span></span> <span data-ttu-id="90830-107">Para obter informações sobre o transporte de enfileiramento de mensagens (também conhecido como MSMQ), consulte [sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="90830-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="90830-108">Para obter informações sobre o transporte de ponto a ponto, consulte [rede ponto a ponto](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="90830-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90830-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="90830-109">In This Section</span></span>  
 [<span data-ttu-id="90830-110">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="90830-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="90830-111">Descreve os três principais transportes e considerações ao selecionar um.</span><span class="sxs-lookup"><span data-stu-id="90830-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="90830-112">Escolhendo um codificador de mensagem</span><span class="sxs-lookup"><span data-stu-id="90830-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="90830-113">Descreve os fatores a considerar ao escolher um elemento de associação de codificação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="90830-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="90830-114">Transferência de mensagem de streaming</span><span class="sxs-lookup"><span data-stu-id="90830-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="90830-115">Descreve como configurar a camada de transporte para fazer o streaming.</span><span class="sxs-lookup"><span data-stu-id="90830-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="90830-116">Configurando HTTP e HTTPS</span><span class="sxs-lookup"><span data-stu-id="90830-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="90830-117">Descreve como configurar o transporte HTTP e HTTPS, elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="90830-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="90830-118">Como substituir a reserva de URL do WCF com uma reserva restrita</span><span class="sxs-lookup"><span data-stu-id="90830-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="90830-119">Descreve como usar reservas WCFURL restringido.</span><span class="sxs-lookup"><span data-stu-id="90830-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="90830-120">Cotas de transporte</span><span class="sxs-lookup"><span data-stu-id="90830-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="90830-121">Descreve considerações ao configurar as cotas disponíveis na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="90830-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="90830-122">Trabalhando com NATs e Firewalls</span><span class="sxs-lookup"><span data-stu-id="90830-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="90830-123">Descreve como configurar a camada de transporte quando mensagens são enviadas ou recebidas por trás de um firewall ou a conversão de endereços de rede (NAT) está presente.</span><span class="sxs-lookup"><span data-stu-id="90830-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="90830-124">Compartilhamento de porta do NET.TCP</span><span class="sxs-lookup"><span data-stu-id="90830-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="90830-125">Descreve como usar o componente de compartilhamento de porta NET. TCP do WCF.</span><span class="sxs-lookup"><span data-stu-id="90830-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90830-126">Referência</span><span class="sxs-lookup"><span data-stu-id="90830-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="90830-127">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="90830-127">Related Sections</span></span>  
 [<span data-ttu-id="90830-128">Associações</span><span class="sxs-lookup"><span data-stu-id="90830-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="90830-129">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="90830-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
