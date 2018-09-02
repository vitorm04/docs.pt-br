---
title: Limitando a distribuição de mensagens
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: bec5a28abeff23929d2c0f1c363f4e08872a63fa
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397921"
---
# <a name="limiting-message-distribution"></a>Limitando a distribuição de mensagens
Canal par ocorre por design, uma malha de difusão. Modelo básico de inundação envolve a distribuição de cada mensagem enviada por qualquer membro de uma malha para todos os outros membros dessa malha. Isso é ideal em situações em que cada mensagem gerada por um membro é útil e relevante para todos os outros membros (por exemplo, uma sala de bate-papo). No entanto, muitos aplicativos têm uma necessidade ocasional para limitar a distribuição de mensagens. Por exemplo, se um novo membro une uma malha e quiser recuperar a última mensagem enviada por meio da malha, esta solicitação não precisa ser inundados para todos os membros da malha. A solicitação pode ser limitada a quase vizinhos ou mensagens geradas localmente podem ser filtradas. As mensagens também podem ser enviadas a um nó individual da malha. Este tópico discute o uso de contagem de salto, um filtro de propagação de mensagem, um filtro local ou uma conexão direta para controlar como as mensagens são encaminhadas em toda a malha e fornece diretrizes gerais para escolher uma abordagem.  
  
## <a name="hop-counts"></a>Contagens de saltos  
 O conceito de `PeerHopCount` é semelhante à TTL (Time-To-Live) usado no protocolo IP. O valor de `PeerHopCount` está vinculado a uma instância de mensagem, e especifica quantas vezes uma mensagem deve ser encaminhada antes de ser descartado. Sempre que uma mensagem é recebida por um cliente de canal par, o cliente examina a mensagem para ver se `PeerHopCount` for especificado. Se for especificado, em seguida, o cliente diminui o salto contagem de valor em um antes de encaminhar a mensagem para nós vizinhos. Quando um cliente recebe uma mensagem com um valor de contagem de saltos igual a zero, o cliente processa a mensagem, mas não encaminhar a mensagem para vizinhos.  
  
 Contagem de saltos pode ser adicionada a uma mensagem com a adição de `PeerHopCount` como um atributo à propriedade aplicável ou campo na implementação da classe de mensagem. Você pode definir isso como um valor específico antes de enviar a mensagem para a malha. Dessa forma, você pode usar a contagem de saltos para limitar a distribuição de mensagens em toda a malha, quando necessário, potencialmente evitando duplicação desnecessária de mensagem. Isso é útil em casos em que a malha contém uma grande quantidade de dados redundantes ou para enviar uma mensagem para vizinhos imediatos, ou vizinhos dentro de alguns saltos.  
  
-   Para trechos de código e informações relacionadas, consulte o [blog de canal par](https://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>Filtro de propagação de mensagem  
 `MessagePropagationFilter` pode ser usado para o controle personalizado de inundação de mensagens, especialmente quando a propagação de determinar o conteúdo da mensagem ou outros cenários específicos. O filtro toma decisões de propagação para cada mensagem que passa por meio do nó. Isso é verdadeiro para as mensagens originadas em outro lugar da malha que seu nó tenha recebido, bem como mensagens criadas pelo seu aplicativo. O filtro tem acesso para a mensagem e sua origem, para que as decisões sobre encaminhamento ou descartar a mensagem podem ser baseadas nas informações completas disponíveis.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter> é uma classe base abstrata com uma única função, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. O primeiro argumento da chamada de método passa uma cópia completa da mensagem. Todas as alterações feitas a mensagem não afetam a mensagem real. O último argumento da chamada de método identifica a origem da mensagem (`PeerMessageOrigination.Local` ou `PeerMessageOrigination.Remote`). Implementações concretas desse método devem retornar uma constante do <xref:System.ServiceModel.PeerMessagePropagation> enumeração que indica que a mensagem deve ser encaminhado para o aplicativo local (`Local`), encaminhados para os clientes remotos (`Remote`), ambos (`LocalAndRemote`), ou nenhum (`None`). Esse filtro pode ser aplicado, acessando correspondente `PeerNode` objeto e especificando uma instância da propagação derivada filtram classe no `PeerNode.MessagePropagationFilter` propriedade. Certifique-se de que o filtro de propagação é anexado antes de abrir o canal par.  
  
-   Para trechos de código e informações relacionadas, consulte o [blog de canal par](https://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Entrando em contato com um nó Individual da malha  
 Um nó individual em uma malha pode ser contatado pela configuração de um filtro local, ou configurando uma conexão direta.  
  
 Se os nós em uma malha tem uma ID individual, uma ID de destino pode ser especificada na implementação de sua mensagem. Um filtro local pode ser configurado por escrever uma função em seu contrato de mensagem que apenas exibirá a mensagem para o nó atual se sua ID corresponde à ID do destino especificado. A malha transporta a mensagem, portanto, a sobrecarga de configurar uma conexão nova não precisa ser cobradas. No entanto, há uma perda de eficiência, pois a mensagem é enviada várias vezes em toda a malha. Isso funciona bem para enviar mensagens para membros individuais de uma malha, desde que as mensagens não são grandes demais nem muito frequentes.  
  
 Para conexões de alta largura de banda, de longa duração, conexões diretas são preferíveis. Você pode enviar informações de conexão pela malha e, em seguida, configurar uma conexão direta de sua escolha para enviar/receber mensagens.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Escolhendo uma abordagem para limitar a distribuição de mensagens  
 Quando você descobre um cenário em que você precisa limitar a distribuição de mensagens, faça as seguintes perguntas:  
  
-   **Quem** precisa receber a mensagem? Nó vizinho apenas um? Um nó em algum lugar na malha? Metade a malha?  
  
-   **A frequência com que** esta mensagem ser enviada?  
  
-   Que tipo de **largura de banda** usará esta mensagem?  
  
 As respostas a essas perguntas podem ajudá-lo a determinar se é necessário usar um filtro de propagação de mensagem, contagem de salto, um filtro local ou uma conexão direta. Considere as seguintes diretrizes gerais:  
  
-   **Quem**  
  
    -   *Nó individual*: filtro Local ou conexão direta.  
  
    -   *Vizinhos dentro de um determinado ambiente de rede*: PeerHopCount.  
  
    -   *Subconjuntos complexos da malha*: MessagePropagationFilter.  
  
-   **A frequência com que**  
  
    -   *Muito frequente*: direcionar a conexão, PeerHopCount, MessagePropagationFilter.  
  
    -   *Ocasional*: filtro Local.  
  
-   **Uso de largura de banda**  
  
    -   *Alta*: direcionar a conexão, menor é aconselhável usar MessagePropagationFilter ou um filtro local.  
  
    -   *Baixa*: qualquer, conexão direta provavelmente não é necessária.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando um aplicativo de canal par](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
