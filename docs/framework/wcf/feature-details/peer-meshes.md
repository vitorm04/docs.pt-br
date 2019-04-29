---
title: Malhas ponto a ponto
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: afd9eae36f28c28b33b74c4456feb4ba8c91314d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766786"
---
# <a name="peer-meshes"></a>Malhas ponto a ponto
Um *malha* é um conjunto nomeado (um gráfico interconectado) de nós de pares que podem se comunicar entre si e que são identificados por uma ID de malha exclusivo. Cada nó está conectado a vários outros nós. Em uma malha bem conectada, há um caminho entre dois nós, com relativamente poucos saltos entre os nós nas bordas mais distante da malha, e a malha permanecerão conectada mesmo se alguns nós ou conexões deixam o aplicativo. Nós ativos na malha publicam suas informações de ponto de extremidade com uma ID de malha correspondente para que outros pares podem encontrá-los.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Características de uma malha criado usando o canal par  
  
#### <a name="uniquely-identified"></a>Identificada exclusivamente  
  
- Uma ID exclusiva identifica cada malha. O nome de malha (ou ID de malha) está no mesmo formato que um nome de host do sistema de nome de domínio (DNS). Como tal, essa ID de malha deve ser exclusivo para o cliente pretendido do aplicativo dentro do escopo do resolvedor que está sendo usado. Um nome comum, como "MyFamilysPeers" ou "KevinsPokerTable", com facilidade entrem em conflito com outros nomes de usuário e podem retornar informações de ponto de extremidade, o que pode resultar em problemas de privacidade ou aumentar a latência de conexão de ponto a ponto não intencional. Uma maneira de evitar esses problemas pode ser adicionar uma ID exclusiva como um sufixo para o apelido para a malha (por exemplo, "KevinsPokerTable90210").  
  
#### <a name="message-flooding"></a>Inundação de mensagens  
  
- A malha permite que as mensagens de remetentes de um ou mais propagadas para todos os outros nós na mesma malha ponto a ponto. Mensagens a inundação de nós pares usam cabeçalhos especificados no namespace em `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>Conexões otimizadas  
  
- Uma malha de canal par é ajustada automaticamente quando nós que entram e saem, garantindo que todos os nós têm boa conectividade com pouca probabilidade de criação de partições (grupos de nós isolados uns dos outros). Conexões de malha também dinamicamente são otimizadas com base nos padrões de tráfego atual, para que a latência de mensagem do remetente para receptor é o menor possível.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Recursos de rede populares que não fornece um canal par  
 É importante estar ciente dos recursos populares de rede que não fornece um canal par. Esses recursos, que podem todos ser criados sobre o Peer Channel, incluem o seguinte:  
  
- **Ordenação de mensagens:** As mensagens provenientes de uma única fonte podem não chegar em todos os outros participantes na mesma ordem ou na ordem em que a fonte é enviada. Entregue aplicativos que exigem que as mensagens em uma determinada ordem deve criá-la em seus aplicativos (por exemplo, ao incluir uma ID monotônica com todas as mensagens).  
  
- **Sistema de mensagens confiável:** Canal par não inclui um mecanismo para garantir o recebimento de mensagem por todos os pares. Para garantir a entrega de mensagens, você deve escrever uma camada de confiabilidade na parte superior de canal par.
