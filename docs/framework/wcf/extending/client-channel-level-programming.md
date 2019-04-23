---
title: Programação de nível de canal cliente
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772577"
---
# <a name="client-channel-level-programming"></a>Programação de nível de canal cliente
Este tópico descreve como escrever um aplicativo de cliente do Windows Communication Foundation (WCF) sem usar o <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> classe e seu modelo de objeto associado.  
  
## <a name="sending-messages"></a>Envio de mensagens  
 Para estar pronto para enviar mensagens e receber e processar as respostas, são necessárias as seguintes etapas:  
  
1. Crie uma associação.  
  
2. Crie uma fábrica de canais.  
  
3. Crie um canal.  
  
4. Envie uma solicitação e ler a resposta.  
  
5. Feche todos os objetos de canal.  
  
#### <a name="creating-a-binding"></a>Criar uma associação  
 Semelhante ao caso de recebimento (consulte [programação de nível de serviço canal](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), enviando mensagens começa criando uma associação. Este exemplo cria um novo <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> e adiciona um <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> à sua coleção de elementos.  
  
#### <a name="building-a-channelfactory"></a>Criação de uma ChannelFactory  
 Em vez de criar uma <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, desta vez, criamos um <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> chamando <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na associação em que o parâmetro de tipo é <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Embora os ouvintes de canais sejam usados pelo lado que aguarda as mensagens de entrada, fábricas de canais são usadas pelo lado que inicia a comunicação para criar um canal. Assim como os ouvintes de canais, fábricas de canais devem ser abertas pela primeira vez antes que possam ser usados.  
  
#### <a name="creating-a-channel"></a>Criação de um canal  
 Em seguida, chamamos <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> para criar um <xref:System.ServiceModel.Channels.IRequestChannel>. Essa chamada usa o endereço do ponto de extremidade com a qual queremos para se comunicar usando o novo canal que está sendo criado. Assim que tivermos um canal, chamamos Open-la para colocá-lo em um estado pronto para comunicação. Dependendo da natureza do transporte, essa chamada para Open pode iniciar uma conexão com o ponto de extremidade de destino ou pode não fazer nada em todos os na rede.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Enviar uma solicitação e ler a resposta  
 Assim que tivermos um canal aberto, podemos criar uma mensagem e use o método de solicitação do canal para enviar a solicitação e esperar a resposta antes de voltar. Quando este método retorna, temos uma mensagem de resposta que podemos ler para descobrir qual foi a resposta do ponto de extremidade.  
  
#### <a name="closing-objects"></a>Fechando objetos  
 Para evitar a perda de recursos, vamos fechar objetos usados nas comunicações quando eles não são mais necessários.  
  
 O exemplo de código a seguir mostra um cliente básico usando a fábrica de canais para enviar uma mensagem e ler a resposta.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
