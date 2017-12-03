---
title: "Limitando a distribuição de mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 191baa2df4a6a5a4fe8139e8b7ad36bd1c60b40d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="limiting-message-distribution"></a>Limitando a distribuição de mensagens
Canal par ocorre por design, uma malha de difusão. Seu modelo básico de inundação envolve a distribuição de cada mensagem enviada por qualquer membro de uma malha para todos os outros membros dessa malha. Isso é ideal em situações em que cada mensagem gerada por um membro é relevantes e úteis para todos os outros membros (por exemplo, uma sala de bate-papo). No entanto, muitos aplicativos têm uma necessidade ocasional de limitando a distribuição de mensagem. Por exemplo, se um novo membro une uma malha e deseja recuperar a última mensagem enviada por meio da malha, esta solicitação não precisa ser inundados para todos os membros da malha. A solicitação pode ser limitada a perto vizinhos ou mensagens geradas localmente podem ser filtradas. As mensagens também podem ser enviadas a um nó individual na malha. Este tópico discute o uso de contagem de salto, um filtro de propagação de mensagem, um filtro local ou uma conexão direta para controlar como as mensagens são encaminhadas em toda a malha e fornece diretrizes gerais para escolher uma abordagem.  
  
## <a name="hop-counts"></a>Contagens de saltos  
 O conceito de `PeerHopCount` é semelhante a TTL (Time-To-Live) usado no protocolo IP. O valor de `PeerHopCount` está associada a uma instância de mensagem, e especifica quantas vezes uma mensagem deve ser encaminhada antes de ser descartado. Cada vez que uma mensagem é recebida por um cliente de canal par, o cliente examina a mensagem para ver se `PeerHopCount` for especificado. Se for especificado, em seguida, diminui o cliente o salto contar valor por um antes de encaminhar a mensagem para nós vizinhos. Quando um cliente recebe uma mensagem com um valor de contagem de salto de zero, o cliente processa a mensagem, mas não encaminhar a mensagem vizinhos.  
  
 Contagem de salto pode ser adicionada a uma mensagem adicionando `PeerHopCount` como um atributo para a propriedade aplicável ou o campo na implementação da classe de mensagem. Você pode definir isso como um valor específico antes de enviar a mensagem para a malha. Dessa forma, você pode usar a contagem de saltos para limitar a distribuição de mensagens em toda a malha quando necessário, potencialmente evitar a duplicação de mensagens desnecessárias. Isso é útil em casos em que a malha contém uma grande quantidade de dados redundantes, ou para enviar uma mensagem ao vizinhas ou vizinhos dentro de alguns saltos.  
  
-   Para trechos de código e informações relacionadas, consulte o [blog de canal par](http://go.microsoft.com/fwlink/?LinkID=114531) (http://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>Filtro de propagação de mensagem  
 `MessagePropagationFilter`pode ser usado para o controle personalizado de inundação de mensagens, especialmente quando a propagação de determinar o conteúdo da mensagem ou outros cenários específicos. O filtro toma decisões de propagação para cada mensagem que passa através do nó. Isso é verdadeiro para as mensagens originadas em outro lugar na malha que seu nó tenha recebido, bem como mensagens criadas pelo seu aplicativo. O filtro tem acesso à mensagem e sua origem, para que decisões sobre encaminhamento ou descartar a mensagem podem ser baseadas nas informações completas disponíveis.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter>é uma classe base abstrata com uma única função, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. O primeiro argumento da chamada de método passa em uma cópia completa da mensagem. Todas as alterações feitas a mensagem não afetam a mensagem real. O último argumento da chamada de método identifica a origem da mensagem (`PeerMessageOrigination.Local` ou `PeerMessageOrigination.Remote`). Implementações concretas desse método devem retornar uma constante do <xref:System.ServiceModel.PeerMessagePropagation> enumeração que indica que a mensagem será encaminhado para o aplicativo local (`Local`), encaminhado para clientes remotos (`Remote`), ambos (`LocalAndRemote`), ou nenhum deles (`None`). Esse filtro pode ser aplicado, acessando correspondente `PeerNode` objeto e especificando uma instância da propagação derivada filtram classe o `PeerNode.MessagePropagationFilter` propriedade. Certifique-se de que o filtro de propagação está conectado antes de abrir o canal par.  
  
-   Para trechos de código e informações relacionadas, consulte o [blog de canal par](http://go.microsoft.com/fwlink/?LinkID=114532) (http://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Entrar em contato com um nó Individual na malha  
 Um nó individual em uma malha pode ser contatado definindo um filtro local ou configurando uma conexão direta.  
  
 Se os nós em uma malha tem uma ID individual, uma ID de destino pode ser especificada na implementação de sua mensagem. Um filtro local pode ser configurado gravando uma função no seu contrato de mensagem que só exibirá a mensagem para o nó atual se sua ID corresponde à ID de destino especificado. A malha transporta a mensagem, a sobrecarga de configurar uma nova conexão precisa ser cobradas. No entanto, há uma perda de eficiência desde que a mensagem é enviada muitas vezes em toda a malha. Isso funciona bem para enviar mensagens para membros individuais de uma malha, como as mensagens são muito grande, nem muito frequentes.  
  
 Para conexões de alta largura de banda, de longa duração, conexões diretas são preferidas. Você pode enviar informações de conexão sobre a malha e, em seguida, configurar uma conexão direta de sua escolha para enviar/receber mensagens.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Escolher uma abordagem para limitar a distribuição de mensagens  
 Quando você descobrir um cenário em que é necessário limitar a distribuição de mensagens, faça as seguintes perguntas:  
  
-   **Quem** precisa receber a mensagem? Nó de um vizinho? Um nó em outro lugar na malha? Metade a malha?  
  
-   **Frequência** esta mensagem ser enviada?  
  
-   Que tipo de **largura de banda** usará esta mensagem?  
  
 As respostas a essas perguntas podem ajudá-lo a determinar se deve usar a contagem de salto, um filtro de propagação de mensagem, um filtro local ou uma conexão direta. Considere as seguintes diretrizes gerais:  
  
-   **Quem**  
  
    -   *Nó individual*: filtro Local ou conexão direta.  
  
    -   *Vizinhos dentro de um determinado ambiente*: PeerHopCount.  
  
    -   *Subconjuntos complexos da malha*: MessagePropagationFilter.  
  
-   **Frequência**  
  
    -   *Muito frequentes*: direcionar a conexão, PeerHopCount, MessagePropagationFilter.  
  
    -   *Ocasionais*: filtro Local.  
  
-   **Uso de largura de banda**  
  
    -   *Alta*: direcionar a conexão, menor é aconselhável usar MessagePropagationFilter ou filtro local.  
  
    -   *Baixo*: qualquer, conexão direta provavelmente não é necessária.  
  
## <a name="see-also"></a>Consulte também  
 [Criando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
