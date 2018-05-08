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
---
# <a name="transports-in-windows-communication-foundation"></a>Transportes no Windows Communication Foundation
A camada de transporte é o nível mais baixo da pilha de canais. Os transportes principais usados no Windows Communication Foundation (WCF) são HTTP, HTTPS, TCP e pipes nomeados. Os tópicos nesta seção abordam escolhendo entre esses transportes, configurando o transporte e definir propriedades de ajuste.  
  
 O WCF inclui transportes adicionais. Para obter informações sobre o transporte de enfileiramento de mensagens (também conhecido como MSMQ), consulte [sessões confiáveis e filas](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Para obter informações sobre o transporte de ponto a ponto, consulte [rede ponto a ponto](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Descreve os três principais transportes e considerações ao selecionar um.  
  
 [Escolhendo um codificador de mensagem](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Descreve os fatores a considerar ao escolher um elemento de associação de codificação de mensagens.  
  
 [Transferência de mensagem de streaming](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Descreve como configurar a camada de transporte para fazer o streaming.  
  
 [Configurando HTTP e HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Descreve como configurar o transporte HTTP e HTTPS, elementos de associação.  
  
 [Como substituir a reserva de URL do WCF com uma reserva restrita](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Descreve como usar reservas WCFURL restringido.  
  
 [Cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Descreve considerações ao configurar as cotas disponíveis na camada de transporte.  
  
 [Trabalhando com NATs e Firewalls](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Descreve como configurar a camada de transporte quando mensagens são enviadas ou recebidas por trás de um firewall ou a conversão de endereços de rede (NAT) está presente.  
  
 [Compartilhamento de porta do NET.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Descreve como usar o componente de compartilhamento de porta NET. TCP do WCF.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Associações](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)
