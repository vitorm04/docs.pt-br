---
title: Canais de desenvolvimento
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: def60ec0cce8da71e7e2d98ff456420949360aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="developing-channels"></a>Canais de desenvolvimento
Para desenvolver um canal de transporte ou protocolo que pode ser usado com o Windows Communication Foundation (WCF) a camada de aplicativo requer várias etapas. Este tópico descreve as etapas e direciona para tópicos específicos para obter mais informações. Para entender o modelo de canal e os vários tipos que são mencionados neste tópico, consulte [visão geral do modelo de canal](../../../../docs/framework/wcf/extending/channel-model-overview.md). Para obter um exemplo de canal de transporte completa, consulte [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>A lista de tarefas de desenvolvimento de canal  
 As etapas para criar um canal definido pelo usuário são da seguinte maneira. Todos os canais devem:  
  
1.  Decidir qual o canal de padrões de troca de mensagem (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, ou <xref:System.ServiceModel.Channels.IReplyChannel>) seu <xref:System.ServiceModel.Channels.IChannelFactory> e <xref:System.ServiceModel.Channels.IChannelListener> darão suporte, bem como se a sessão oferecerá suporte variações dessas interfaces. Para obter detalhes, consulte [escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Criar uma fábrica de canal e ouvinte (<xref:System.ServiceModel.Channels.IChannelFactory> e <xref:System.ServiceModel.Channels.IChannelListener>) que suporte o padrão de troca de mensagem. Para obter detalhes sobre como desenvolver fábricas, consulte [cliente: fábricas de canais e canais](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Para obter detalhes sobre como desenvolver ouvintes, consulte [serviço: ouvintes de canais e canais](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Certifique-se de que todas as exceções específicas de rede são normalizadas para o <xref:System.TimeoutException?displayProperty=nameWithType> ou apropriado classe derivada de <xref:System.ServiceModel.CommunicationException>. Para obter detalhes, consulte [tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Para habilitar o uso da camada de aplicativo, adicione um <xref:System.ServiceModel.Channels.BindingElement> que adiciona o canal personalizado para uma pilha de canais. Para obter mais informações, consulte [criando um BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 As seguintes etapas adicionais são necessárias para habilitar o suporte a mais completo na camada de aplicativo:  
  
1.  Adicione uma seção de extensão do elemento de associação para expor o novo elemento de associação para o sistema de configuração. Para obter mais informações, consulte [configuração e suporte a metadados](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Adicione extensões de metadados para recursos para outros pontos de extremidade de comunicação. Para obter mais informações, consulte [configuração e suporte a metadados](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Adicione uma associação que pré-configura em uma pilha de elementos de associação de acordo com um perfil bem definido. Para obter mais informações, consulte [Criando associações](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Adicione uma seção de associação e o elemento de configuração de associação para expor a associação para o sistema de configuração. Para obter mais informações, consulte [configuração e suporte a metadados](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo associações](../../../../docs/framework/wcf/extending/extending-bindings.md)
