---
title: "Cenários de canal par"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 62ea53cf5a96519c864e48dc48e28ed81e3b6d8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="peer-channel-scenarios"></a>Cenários de canal par
As APIs de canal par suporte aos seguintes cenários de desenvolvimento.  
  
## <a name="publicationsubscription-messaging"></a>Mensagens de publicação/assinatura  
 As empresas que criam aplicativos de publicação/assinatura (por exemplo, cotações de ações e editores de títulos de notícias, tem pontuações e relatórios de clima) podem usar o canal par para aplicativos de servidor. Por exemplo, os usuários podem obter as mais recentes pontuações de esportes unindo uma malha comum (ou grupo de clientes) e propagar grande quantidade de dados atualizados de jogos sem aumentar a carga do servidor. Isso ajuda o provedor de dados para fornecer alta qualidade de serviço sem aumentar substancialmente o investimento em tecnologias de servidor.  
  
## <a name="collaboration"></a>Colaboração  
 Fornecedores de software independentes (ISVs) podem criar aplicativos que permitem que pessoas criar grupos perfeitos para participação em atividades de ponto a ponto. Por exemplo, isso pode incluir as equipes de trabalhar em projetos de colaboração, compartilhamento de imagem entre amigos, planejamento de terceiros atividades e muito mais. Tradicionalmente, essas atividades sempre envolvem servidores; No entanto, o canal par fornece uma maneira de fazer isso de maneira mais eficiente, permitindo cenários de acesso offline que não são implementados como facilmente em um modelo cliente-servidor tradicional.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Processamento distribuído e Clusters de computação  
 Clusters de computação e de processamento distribuído normalmente são usadas para cálculos em larga escala, como financeiros/clima modelagem e decodificação de DNA humana. Normalmente, isso é feito com servidores individualmente atribuir tarefas a todos os clientes participando do cluster de computação. Esses servidores também podem ter demandas adicionais; Por exemplo, todas as tarefas precisará ser concluída dentro de um determinado tempo, a necessidade de mais de uma máquina para cada tarefa. Além disso, se qualquer cliente que está executando uma tarefa falhar, outro cliente deve ser capaz de assumir a tarefa e executar o trabalho. Da mesma forma, mais de um cliente pode ter que executar a mesma tarefa para garantir resultados consistentes. Embora os servidores podem executar esse tipo de coordenação de cliente, você pode criar uma solução de ponto a ponto em que os clientes que recebem uma tarefa de forma independente determinam os requisitos de servidor a tarefa e usam uma malha de computação para determinar como concluir essa tarefa.  
  
## <a name="gaming"></a>Jogos  
 Usando o canal de mesmo nível, os desenvolvedores de aplicativos podem criar versões de servidor dos seus jogos onde move jogo obter transmitidas para o e sincronizadas com outros jogadores por um mecanismo de ponto a ponto, em vez de através de um servidor central. Para ISVs pequenos, isso ajuda a remover os custos operacionais associados à implantação, manutenção e os servidores centrais de manutenção. Jogos escritos usando uma arquitetura de ponto a ponto podem ser executados com a Internet, ou em redes locais com ou sem fio. Atividades de jogos secundário, como corredor e jogo bate-papo podem ser desenvolvidas usando uma rede ponto a ponto.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de canal par](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
