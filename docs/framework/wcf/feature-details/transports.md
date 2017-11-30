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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Transportes no Windows Communication Foundation
A camada de transporte é o nível mais baixo da pilha de canais. Os transportes principais usados em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] são HTTP, HTTPS, TCP e pipes nomeados. Os tópicos nesta seção abordam escolhendo entre esses transportes, configurando o transporte e definir propriedades de ajuste.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]inclui transportes adicionais. Para obter informações sobre o transporte de enfileiramento de mensagens (também conhecido como MSMQ), consulte [sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Para obter informações sobre o transporte de ponto a ponto, consulte [rede ponto a ponto](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Descreve os três principais transportes e considerações ao selecionar um.  
  
 [Escolhendo um codificador de mensagem](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Descreve os fatores a considerar ao escolher um elemento de associação de codificação de mensagens.  
  
 [Transferência de mensagem de streaming](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Descreve como configurar a camada de transporte para fazer o streaming.  
  
 [Configurando HTTP e HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Descreve como configurar o transporte HTTP e HTTPS, elementos de associação.  
  
 [Como: substituir a reserva de URL do WCF com uma reserva restrita](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Descreve como usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restrito reservas.  
  
 [Cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Descreve considerações ao configurar as cotas disponíveis na camada de transporte.  
  
 [Trabalhando com NATs e Firewalls](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Descreve como configurar a camada de transporte quando mensagens são enviadas ou recebidas por trás de um firewall ou a conversão de endereços de rede (NAT) está presente.  
  
 [Compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Descreve como usar o componente de compartilhamento de porta NET. TCP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Bindings](../../../../docs/framework/wcf/feature-details/bindings.md) (Associações)  
  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)
