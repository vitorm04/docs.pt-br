---
title: "Visão geral de modelo de canal"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f6f45b788d825fed3c8f5d627190dd8911ec4c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-model-overview"></a>Visão geral de modelo de canal
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pilha de canais é uma pilha de comunicação em camadas com um ou mais canais que processar mensagens. Na parte inferior da pilha é um canal de transporte é responsável para adaptar a pilha de canais de transporte subjacente (por exemplo, TCP, HTTP, SMTP e outros tipos de transporte.). Canais fornecem um modelo de programação de nível baixo para enviar e receber mensagens. Este modelo de programação se baseia em várias interfaces e outros tipos de coletivamente conhecidos como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de canal. Este tópico discute as formas de canal, a construção de um ouvinte de canal básica (no serviço) e a fábrica de canais (no cliente).  
  
## <a name="channel-stack"></a>Pilha de canais  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pontos de extremidade de se comunicar com o mundo usando uma pilha de comunicação chamada a pilha de canais. O diagrama a seguir compara a pilha de canais com outros pilhas de comunicação, como TCP/IP.  
  
 ![Modelo de canal](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Primeiro, as semelhanças: em ambos os casos, cada camada da pilha fornece algumas abstração do mundo abaixo da camada e expostos essa abstração apenas para a camada imediatamente acima dela. Cada camada usa a abstração de apenas a camada diretamente abaixo dela. Também em ambos os casos, quando duas pilhas se comunicam, cada camada se comunica com a camada correspondente da pilha, por exemplo, a camada IP se comunica com a camada IP e a camada TCP com a camada TCP e assim por diante.  
  
 Agora, as diferenças: pilha TCP a enquanto foi projetada para fornecer uma abstração de rede física, a pilha de canais é projetada para fornecer uma abstração de não apenas como a mensagem é entregue, ou seja, o transporte, mas também outros recursos como o que está em a mensagem ou o protocolo que é usado para comunicação, incluindo o transporte mas muito mais. Por exemplo, elemento de associação de sessão confiável é parte da pilha de canais, mas não está abaixo do transporte ou a própria. Essa abstração é obtida, exigindo o canal inferior na pilha de adaptar o protocolo de transporte subjacente para a arquitetura de pilha de canal e de, em seguida, contar com mais canais up na pilha para fornecer recursos de comunicação, como confiabilidade garantias e segurança.  
  
 Fluxo de mensagens passa a pilha de comunicação como <xref:System.ServiceModel.Channels.Message> objetos. Conforme mostrado na figura acima, o canal inferior é chamado de um canal de transporte. É o canal que é responsável por enviar e receber mensagens para e de outras pessoas. Isso inclui a responsabilidade de transformar o <xref:System.ServiceModel.Channels.Message> objeto de e para o formato usado para se comunicar com outras pessoas. Acima do canal de transporte pode haver qualquer número de canais de protocolo cada responsável por fornecer uma função de comunicação como garantias de entrega confiável. Canais de protocolo operam em mensagens que passam por-los na forma do <xref:System.ServiceModel.Channels.Message> objeto. Eles normalmente a transform a mensagem, por exemplo, adicionando cabeçalhos ou criptografando o corpo, ou enviar e recebem suas próprias mensagens de controle de protocolo, por exemplo, as confirmações de recebimento.  
  
## <a name="channel-shapes"></a>Formas de canal  
 Cada canal implementa uma ou mais interfaces conhecidos como interfaces de forma de canal ou formas de canal. Essas formas de canal fornecem os métodos voltados para comunicações como enviar e recebem ou de solicitação e respondam que implementa o canal e chama o usuário do canal. É a base das formas de canal de <xref:System.ServiceModel.Channels.IChannel> interface, que é uma interface que fornece um `GetProperty` \<T > método planejado como um mecanismo em camadas para acessar recursos arbitrários expostos pelos canais na pilha. Os cinco formas que se estendem de canal <xref:System.ServiceModel.Channels.IChannel> são:  
  
-   <xref:System.ServiceModel.Channels.IInputChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplyChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Além disso, cada uma dessas formas tem um equivalente que estende o <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> para oferecer suporte a sessões. Elas são:  
  
-   <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
-   <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 As formas de canal são padronizadas depois de alguns a mensagem fundamental padrões com suporte pelos protocolos de transporte existente do exchange. Por exemplo, mensagens unidirecionais corresponde a um <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> solicitação-resposta de par, corresponde ao <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> pares e comunicação duplex bidirecional corresponde ao <xref:System.ServiceModel.Channels.IDuplexChannel> (que estende ambos <xref:System.ServiceModel.Channels.IInputChannel> e <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programando com a pilha de canais  
 Pilhas de canal são tipicamente criadas usando um padrão de fábrica em que uma associação cria a pilha de canais. No lado de envio, uma associação é usada para criar um <xref:System.ServiceModel.ChannelFactory>, que por sua vez compilações um canal de pilha e retorna uma referência para a parte superior do canal na pilha. O aplicativo, em seguida, pode usar esse canal para enviar mensagens. Para obter mais informações, consulte [programação de nível de canal cliente](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 No lado de recebimento uma associação é usada para criar um <xref:System.ServiceModel.Channels.IChannelListener>, que verifica se há mensagens de entrada. O <xref:System.ServiceModel.Channels.IChannelListener> fornece mensagens para o aplicativo de escuta criando pilhas de canal e manipulação a referência do aplicativo para o canal superior. Em seguida, o aplicativo usa esse canal para receber mensagens de entrada. Para obter mais informações, consulte [programação de nível de serviço de canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>O modelo de objeto do canal  
 O modelo de objeto do canal é o conjunto principal de interfaces necessárias para implementar os canais, ouvintes de canais e fábricas de canais. Também há algumas classes base fornecidas para auxiliar em implementações personalizadas.  
  
 Ouvintes de canais são responsáveis por escutar mensagens de entrada e entregá-los para a camada superior por meio de canais criados pelo ouvinte de canal.  
  
 Fábricas de canais são responsáveis por criar canais que são usados para enviar mensagens e para fechar todos os canais criados quando a fábrica de canais é fechada.  
  
 <xref:System.ServiceModel.ICommunicationObject>é a interface principal que define a máquina de estado básica que todos os objetos de comunicação implementar. <xref:System.ServiceModel.Channels.CommunicationObject>Fornece uma implementação desta interface principal que outras classes de canal podem derivar em vez de re-implementar a interface. No entanto, isso não é obrigatório: um canal personalizado pode implementar <xref:System.ServiceModel.ICommunicationObject> diretamente e não herda de <xref:System.ServiceModel.Channels.CommunicationObject>. Nenhuma das classes na Figura 3 são consideradas parte do modelo de canal. eles estão disponíveis para os implementadores de canal personalizado que desejam criar canais de auxiliares.  
  
 ![Modelo de canal](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Os tópicos a seguir descrevem o modelo de objeto do canal, bem como várias áreas de desenvolvimento que ajudam a criar canais personalizados.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Serviço: ouvintes de canais e canais](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|Descreve os ouvintes de canais que escuta canais de entrada em um aplicativo de serviço.|  
|[Cliente: fábricas de canais e canais](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|Descreve as fábricas de canais que criam canais para se conectar a um aplicativo de serviço.|  
|[Entendendo mudanças de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Descreve como o <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> alterações de estado em canais de modelos de interface.|  
|[Escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Descreve os seis padrões de troca de mensagem básica que podem dar suporte a canais.|  
|[Tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Descreve como lidar com falhas e exceções em canais personalizados.|  
|[Configuração e suporte a metadados](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Descreve como suporte ao uso de canais personalizados do modelo de aplicativo e como exportar e importar metadados usando associações e elementos de associação.|
