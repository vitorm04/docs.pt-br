---
title: Visão geral de modelo de canal
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 362a7392d9dbaedb1942280a6c3b6c8f2139afe5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795893"
---
# <a name="channel-model-overview"></a>Visão geral de modelo de canal
A pilha de canais do Windows Communication Foundation (WCF) é uma pilha de comunicação em camadas com um ou mais canais que processam mensagens. Na parte inferior da pilha há um canal de transporte que é responsável por adaptar a pilha de canais ao transporte subjacente (por exemplo, TCP, HTTP, SMTP e outros tipos de transporte). Os canais fornecem um modelo de programação de baixo nível para enviar e receber mensagens. Esse modelo de programação depende de várias interfaces e outros tipos coletivamente conhecidos como o modelo de canal do WCF. Este tópico discute as formas de canal, a construção de um ouvinte de canal básico (no serviço) e a fábrica de canais (no cliente).  
  
## <a name="channel-stack"></a>Pilha de canais  
 Os pontos de extremidade do WCF se comunicam com o mundo usando uma pilha de comunicação chamada pilha de canais. O diagrama a seguir compara a pilha de canais com outras pilhas de comunicação, por exemplo, TCP/IP.  
  
 ![Channel Model](./media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Primeiro, as semelhanças: Em ambos os casos, cada camada da pilha fornece uma abstração do mundo abaixo dessa camada e expô essa abstração somente para a camada diretamente acima dela. Cada camada usa a abstração apenas da camada diretamente abaixo dela. Também em ambos os casos, quando duas pilhas se comunicam, cada camada comunica-se com a camada correspondente na outra pilha, por exemplo, a camada de IP se comunica com a camada IP e a camada TCP com a camada TCP e assim por diante.  
  
 Agora, as diferenças: Embora a pilha TCP tenha sido projetada para fornecer uma abstração da rede física, a pilha de canais foi projetada para fornecer uma abstração de não apenas como a mensagem é entregue, ou seja, o transporte, mas também outros recursos, como o que está na mensagem ou o que o protocolo é usado para comunicação, incluindo o transporte, mas muito mais do que isso. Por exemplo, o elemento de associação de sessão confiável faz parte da pilha de canais, mas não está abaixo do transporte ou do próprio transporte. Essa abstração é obtida exigindo o canal inferior na pilha para adaptar o protocolo de transporte subjacente à arquitetura da pilha de canais e, em seguida, depender dos canais mais adiante na pilha para fornecer recursos de comunicação, como confiabilidade garantias e segurança.  
  
 As mensagens fluem pela pilha de comunicação <xref:System.ServiceModel.Channels.Message> como objetos. Como mostrado na figura acima, o canal inferior é chamado de canal de transporte. É o canal que é responsável por enviar e receber mensagens de e para outras partes. Isso inclui a responsabilidade de transformar o <xref:System.ServiceModel.Channels.Message> objeto de e para o formato usado para se comunicar com outras partes. Acima do canal de transporte, pode haver qualquer número de canais de protocolo responsáveis por fornecer uma função de comunicação, como garantias de entrega confiáveis. Os canais de protocolo operam em mensagens que fluem por eles na <xref:System.ServiceModel.Channels.Message> forma do objeto. Normalmente, eles transformam a mensagem, por exemplo, adicionando cabeçalhos ou criptografando o corpo, ou enviam e recebem suas próprias mensagens de controle de protocolo, por exemplo, confirmações de recebimento.  
  
## <a name="channel-shapes"></a>Formas de canal  
 Cada canal implementa uma ou mais interfaces conhecidas como interfaces de forma de canal ou formas de canal. Essas formas de canal fornecem métodos orientados a comunicação, como enviar e receber ou solicitar e responder que o canal implementa e o usuário das chamadas de canal. Na base das formas de canal está a <xref:System.ServiceModel.Channels.IChannel> interface, que é uma interface que fornece um `GetProperty` \<método T > destinado a um mecanismo em camadas para acessar recursos arbitrários expostos por canais na pilha. As cinco formas de canal que <xref:System.ServiceModel.Channels.IChannel> se estendem são:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Além disso, cada uma dessas formas tem um equivalente que <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> se estende para oferecer suporte a sessões. Elas são:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 As formas de canal são padronizadas após alguns dos padrões de troca de mensagens fundamentais com suporte pelos protocolos de transporte existentes. Por exemplo, mensagens unidirecionais correspondem a um <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> par, a solicitação-resposta corresponde a pares e a comunicação duplex bidirecional corresponde a <xref:System.ServiceModel.Channels.IDuplexChannel> (que estende <xref:System.ServiceModel.Channels.IInputChannel> e <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programando com a pilha de canais  
 As pilhas de canal normalmente são criadas usando um padrão de fábrica em que uma associação cria a pilha de canais. No lado do envio, uma associação é usada para criar um <xref:System.ServiceModel.ChannelFactory>, que, por sua vez, cria uma pilha de canais e retorna uma referência ao canal superior na pilha. O aplicativo pode usar esse canal para enviar mensagens. Para obter mais informações, consulte [programação de nível de canal do cliente](client-channel-level-programming.md).  
  
 No lado de recebimento, uma associação é usada para criar <xref:System.ServiceModel.Channels.IChannelListener>um, que escuta mensagens de entrada. O <xref:System.ServiceModel.Channels.IChannelListener> fornece mensagens ao aplicativo de escuta criando pilhas de canal e entregando a referência do aplicativo ao canal superior. O aplicativo usa esse canal para receber mensagens de entrada. Para obter mais informações, consulte [programação de nível de canal de serviço](service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>O modelo de objeto do canal  
 O modelo de objeto de canal é o conjunto principal de interfaces necessárias para implementar canais, ouvintes de canal e fábricas de canal. Também há algumas classes base fornecidas para auxiliar nas implementações personalizadas.  
  
 Os ouvintes de canal são responsáveis por escutar mensagens recebidas e, em seguida, entregá-las à camada acima por meio de canais criados pelo ouvinte de canal.  
  
 As fábricas de canal são responsáveis pela criação de canais que são usados para enviar mensagens e para fechar todos os canais criados quando a fábrica de canais é fechada.  
  
 <xref:System.ServiceModel.ICommunicationObject>é a interface principal que define o computador de estado básico que todos os objetos de comunicação implementam. <xref:System.ServiceModel.Channels.CommunicationObject>fornece uma implementação dessa interface principal que outras classes de canal podem derivar, em vez de implementar a interface novamente. No entanto, isso não é necessário: um canal personalizado <xref:System.ServiceModel.ICommunicationObject> pode implementar diretamente e não <xref:System.ServiceModel.Channels.CommunicationObject>herdar de. Nenhuma das classes da Figura 3 é considerada parte do modelo de canal; Eles são auxiliares disponíveis para implementadores de canal personalizados que desejam criar canais.  
  
 ![Modelo de canal](./media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Os tópicos a seguir descrevem o modelo de objeto de canal, bem como várias áreas de desenvolvimento que ajudam a criar canais personalizados.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Serviço Ouvintes de canal e canais](service-channel-listeners-and-channels.md)|Descreve ouvintes de canal, que escutam canais de entrada em um aplicativo de serviço.|  
|[Cliente Fábricas de canais e canais](client-channel-factories-and-channels.md)|Descreve as fábricas de canal, que criam canais para se conectar a um aplicativo de serviço.|  
|[Entendendo mudanças de estado](understanding-state-changes.md)|Descreve como o <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> estado dos modelos de interface é alterado em canais.|  
|[Escolhendo um padrão de troca de mensagem](choosing-a-message-exchange-pattern.md)|Descreve os seis padrões de troca de mensagens básicos aos quais os canais podem dar suporte.|  
|[Tratamento de exceções e falhas](handling-exceptions-and-faults.md)|Descreve como lidar com falhas e exceções em canais personalizados.|  
|[Configuração e suporte a metadados](configuration-and-metadata-support.md)|Descreve como dar suporte ao uso de canais personalizados do modelo de aplicativo e como exportar e importar metadados usando associações e elementos de associação.|
