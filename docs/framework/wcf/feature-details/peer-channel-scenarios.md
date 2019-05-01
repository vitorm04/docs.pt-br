---
title: Cenários de canal par
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: 610668e5f3625c638fc1e814e0116df87970773b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62046378"
---
# <a name="peer-channel-scenarios"></a>Cenários de canal par
As APIs de canal par suportam os seguintes cenários de desenvolvimento.  
  
## <a name="publicationsubscription-messaging"></a>Mensagens de publicação/assinatura  
 As empresas que criam aplicativos de publicação/assinatura (por exemplo, cotações de ações e editores de manchetes de notícias, esportes pontuações e relatórios de clima) podem usar o Peer Channel para aplicativos sem servidor. Por exemplo, os usuários podem obter os resultados mais recentes de esportes unindo uma malha comuns (ou grupo de clientes) e propagar a grande quantidade de dados atualizados de jogos sem aumentar a carga do servidor. Isso ajuda o provedor de dados para dar maior qualidade de serviço sem aumentar substancialmente o investimento em tecnologias baseadas em servidor.  
  
## <a name="collaboration"></a>Colaboração  
 Fornecedores de software independentes (ISVs) podem criar aplicativos que permitem que as pessoas criar grupos de estreitos para participação em atividades de ponto a ponto. Por exemplo, isso pode incluir as equipes que trabalham em projetos de colaboração, compartilhamento de imagem entre amigos, planejamento de terceiros atividades e muito mais. Tradicionalmente, essas atividades sempre envolvem servidores; No entanto, o canal par fornece uma maneira de fazer isso de forma mais eficiente, habilitando cenários de acesso offline que não são tão facilmente implementados em um modelo de servidor-cliente tradicionais.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Processamento distribuído e Clusters de computação  
 Clusters de computação e processamento distribuído normalmente são usados para cálculos em larga escala, tais como o financeiro/clima de modelagem e decodificação de DNA humana. Normalmente, isso é feito fazendo com que os servidores individualmente atribuir tarefas a todos os clientes que participam do cluster de computação. Esses servidores também podem ter exigências adicionais; Por exemplo, todas as tarefas talvez precise ser concluída dentro de uma determinada duração que exigem mais de um computador para cada tarefa. Além disso, se qualquer cliente executar uma tarefa falhar, outro cliente deve ser capaz de assumir que a tarefa e executar o trabalho nele. Da mesma forma, mais de um cliente pode ter que executar a mesma tarefa para garantir resultados consistentes. Embora os servidores podem executar esse tipo de coordenação de cliente, você pode criar uma solução de ponto a ponto em que os clientes que recebem uma tarefa de forma independente determinam os requisitos de servidor para a tarefa e usam uma malha de computação para determinar como concluir essa tarefa.  
  
## <a name="gaming"></a>Jogos  
 Usando o canal de mesmo nível, os desenvolvedores de aplicativos podem criar versões sem servidor de seus jogos, onde as movimentações de jogos obterem transmitidas para e sincronizadas com outros jogadores por um mecanismo de ponto a ponto em vez de por meio de um servidor central. Para ISVs pequeno, isso ajuda a remover os custos operacionais associados à implantação, manutenção e manutenção de servidores centrais. Jogos escritos usando uma arquitetura ponto a ponto podem ser executados com a Internet ou em redes locais com ou sem fio. Atividades de jogos secundária, como lobby e bate-papo de jogos podem ser desenvolvidas usando uma rede ponto a ponto.  
  
## <a name="see-also"></a>Consulte também

- [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
