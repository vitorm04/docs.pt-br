---
title: Visão geral de modelo de canal
ms.date: 03/30/2017
helpviewer_keywords:
- channel model [WCF]
ms.assetid: 07a81e11-3911-4632-90d2-cca99825b5bd
ms.openlocfilehash: 13fe07d1521832ed12ba5770e0bd069ff9b917d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043570"
---
# <a name="channel-model-overview"></a>Visão geral de modelo de canal
A pilha de canais do Windows Communication Foundation (WCF) é uma pilha de comunicação em camadas com um ou mais canais que processam mensagens. Na parte inferior da pilha é um canal de transporte que é responsável pela adaptação a pilha de canais de transporte subjacente (por exemplo, TCP, HTTP, SMTP e outros tipos de transporte.). Canais fornecem um modelo de programação de nível baixo para enviar e receber mensagens. Esse modelo de programação se baseia em várias interfaces e outros tipos conhecidos coletivamente como o modelo de canal WCF. Este tópico discute as formas de canal, a construção de um ouvinte de canais básica (no serviço) e a fábrica de canais (no cliente).  
  
## <a name="channel-stack"></a>Pilha de canais  
 Pontos de extremidade WCF se comunicar com o mundo usando uma pilha de comunicação chamada a pilha de canais. O diagrama a seguir compara a pilha de canais com outras pilhas de comunicação, por exemplo TCP/IP.  
  
 ![Channel Model](../../../../docs/framework/wcf/extending/media/wcfc-channelstackhighlevelc.gif "wcfc_ChannelStackHighLevelc")  
  
 Primeiro, as semelhanças: Em ambos os casos, cada camada da pilha fornece alguma abstração do mundo abaixo da camada e exposta dessa abstração somente à camada diretamente acima dele. Cada camada usa a abstração de apenas a camada diretamente abaixo dela. Também em ambos os casos, quando duas pilhas se comunicam, cada camada se comunica com a camada correspondente em outra pilha, por exemplo, a camada IP se comunica com a camada IP e a camada TCP com a camada TCP e assim por diante.  
  
 Agora, as diferenças: Enquanto a pilha TCP foi projetada para fornecer uma abstração de rede física, a pilha de canais é projetada para fornecer uma abstração de não apenas como a mensagem é entregue, ou seja, o transporte, mas também outros recursos, como o que está na mensagem ou o que protocolo é usado para comunicação, incluindo o transporte, mas muito mais do que isso. Por exemplo, o elemento de associação de sessão confiável faz parte da pilha de canais, mas não estiver abaixo de transporte ou no próprio transporte. Essa abstração é obtida ao exigir que o canal inferior na pilha para adaptar o protocolo de transporte subjacente para a arquitetura de pilha de canal e de terceira parte confiável em ainda mais canais up na pilha para fornecer recursos de comunicação, como confiabilidade garantias e segurança.  
  
 Fluxo de mensagens passa a pilha de comunicação como <xref:System.ServiceModel.Channels.Message> objetos. Conforme mostrado na figura acima, o canal inferior é chamado de um canal de transporte. É o canal que é responsável por enviar e receber mensagens para e de outras partes. Isso inclui a responsabilidade de transformar o <xref:System.ServiceModel.Channels.Message> objeto e para o formato usado para se comunicar com outras partes. Acima do canal de transporte pode haver qualquer número de canais de protocolo cada responsável por fornecer uma função de comunicação como garantias de entrega confiável. Canais de protocolo operam em mensagens que passam por eles na forma do <xref:System.ServiceModel.Channels.Message> objeto. Eles normalmente a transform a mensagem, por exemplo, adicionando cabeçalhos ou criptografando o corpo, ou enviar e recebem suas próprias mensagens de controle de protocolo, por exemplo, as confirmações de recebimento.  
  
## <a name="channel-shapes"></a>Formas de canal  
 Cada canal implementa uma ou mais interfaces, conhecidos como interfaces de forma de canal ou formas de canal. Essas formas de canal fornecem os métodos orientado pelas comunicações, como enviar e recebem ou solicitarem e responder que implementa o canal e chama o usuário do canal. Na base das formas de canal é o <xref:System.ServiceModel.Channels.IChannel> interface, que é uma interface que fornece uma `GetProperty` \<T > método se destina como um mecanismo em camadas para acessar recursos arbitrários expostos pelos canais na pilha. Cinco formas que se estendem de canal <xref:System.ServiceModel.Channels.IChannel> são:  
  
- <xref:System.ServiceModel.Channels.IInputChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestChannel>  
  
- <xref:System.ServiceModel.Channels.IReplyChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexChannel>  
  
 Além disso, cada uma dessas formas tem um equivalente que estende <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType> para dar suporte a sessões. Elas são:  
  
- <xref:System.ServiceModel.Channels.IInputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IOutputSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IRequestSessionChannel>  
  
- <xref:System.ServiceModel.Channels.IReplySessionChannel>  
  
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel>  
  
 As formas de canal são padronizadas depois de alguns da mensagem fundamental de padrões de troca de protocolos de transporte existentes com suporte. Por exemplo, mensagens unidirecionais corresponde a um <xref:System.ServiceModel.Channels.IInputChannel> / <xref:System.ServiceModel.Channels.IOutputChannel> par de solicitação-resposta corresponde à <xref:System.ServiceModel.Channels.IRequestChannel> / <xref:System.ServiceModel.Channels.IReplyChannel> pares e comunicações duplex bidirecionais corresponde à <xref:System.ServiceModel.Channels.IDuplexChannel> (que estende ambos <xref:System.ServiceModel.Channels.IInputChannel> e <xref:System.ServiceModel.Channels.IOutputChannel>).  
  
## <a name="programming-with-the-channel-stack"></a>Programando com a pilha de canais  
 Pilhas de canais normalmente são criadas usando um padrão de fábrica onde uma associação cria a pilha de canais. No lado do envio, uma associação é usada para criar um <xref:System.ServiceModel.ChannelFactory>, que por sua vez, compilações de um canal de pilha e retorna uma referência à parte superior do canal na pilha. O aplicativo pode usar esse canal para enviar mensagens. Para obter mais informações, consulte [programação de nível de canal do cliente](../../../../docs/framework/wcf/extending/client-channel-level-programming.md).  
  
 No lado do recebimento uma associação é usada para criar um <xref:System.ServiceModel.Channels.IChannelListener>, que escuta mensagens de entrada. O <xref:System.ServiceModel.Channels.IChannelListener> fornece mensagens para o aplicativo de escuta criando pilhas de canais e por entregar a referência de aplicativo para o canal superior. O aplicativo, em seguida, usa esse canal para receber mensagens de entrada. Para obter mais informações, consulte [programação de nível de serviço canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md).  
  
## <a name="the-channel-object-model"></a>O modelo de objeto de canal  
 O modelo de objeto de canal é o conjunto principal de interfaces necessárias para implementar canais, ouvintes de canais e fábricas de canais. Também há algumas classes base fornecidas para auxiliar na implementações personalizadas.  
  
 Ouvintes de canais serão responsáveis por escutar as mensagens de entrada, em seguida, entregá-los para a camada acima por meio de canais criada pelo ouvinte de canais.  
  
 Fábricas de canais são responsáveis por criar canais que são usados para enviar mensagens e para fechar todos os canais criados quando a fábrica de canais é fechada.  
  
 <xref:System.ServiceModel.ICommunicationObject> é a interface principal que define a máquina de estado básica que implementam todos os objetos de comunicação. <xref:System.ServiceModel.Channels.CommunicationObject> Fornece uma implementação desta interface de núcleo que outras classes de canal podem derivar em vez de reimplementar a interface. No entanto, isso não é necessário: um canal personalizado pode implementar <xref:System.ServiceModel.ICommunicationObject> diretamente e não são herdados do <xref:System.ServiceModel.Channels.CommunicationObject>. Nenhuma das classes na Figura 3 são consideradas parte do modelo de canal. eles são auxiliares disponíveis para os implementadores de canal personalizado que desejam criar canais.  
  
 ![Modelo de canal](../../../../docs/framework/wcf/extending/media/wcfc-wcfcchannelsigure3omumtreec.gif "wcfc_WCFCChannelsigure3OMUMTreec")  
  
 Os tópicos a seguir descrevem o modelo de objeto de canal, bem como várias áreas de desenvolvimento que ajudam a criar canais personalizados.  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Serviço: Canais e ouvintes de canais](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)|Descreve os ouvintes de canais que escuta para canais de entrada em um aplicativo de serviço.|  
|[Cliente: Fábricas de canais e canais](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)|Descreve as fábricas de canais que criam canais para se conectar a um aplicativo de serviço.|  
|[Entendendo mudanças de estado](../../../../docs/framework/wcf/extending/understanding-state-changes.md)|Descreve como o <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> alterações de estado em canais de modelos de interface.|  
|[Escolhendo um padrão de troca de mensagem](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)|Descreve os seis padrões de troca de mensagem básica que podem dar suporte a canais.|  
|[Tratamento de exceções e falhas](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)|Descreve como lidar com falhas e exceções em canais personalizados.|  
|[Configuração e suporte a metadados](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)|Descreve como dar suporte o uso de canais personalizados do modelo de aplicativo e como exportar e importar metadados usando associações e elementos de associação.|
