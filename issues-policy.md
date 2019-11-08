---
ms.openlocfilehash: 33178637c4fcfb21e8190c3d2593f09326ea5995
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73554844"
---
# <a name="github-issues-process-and-policy"></a>Política e processo de problemas do GitHub

Os objetivos do processo são:

1. Verificar se os erros ou as omissões em nossos documentos não estão impedindo o sucesso do cliente.
1. Responder aos comentários e às preocupações dos clientes.
1. Melhorar continuamente a experiência do cliente.
1. Saber mais sobre as experiências do cliente por meio de um diálogo aberto sobre desafios e soluções.

O processo usa dois estágios para garantir a capacidade de resposta enquanto prioriza o trabalho. O estágio inicial diagnostica e faz a triagem do problema. O segundo estágio resolve o problema. Quando um problema é fácil e urgente, os dois estágios podem ser combinados.

O processo envolve tarefas com alocações de tempo fixas:

- Cada membro da equipe gasta até meia hora por dia útil [classificando os problemas recebidos](#diagnosis-phase), incluindo as respostas iniciais. Isso garante que possamos responder a novos problemas.
- Cada membro da equipe gasta até meio dia por semana [atualizando documentos](#resolution-phase) para resolver problemas do GitHub gerados pelo cliente.

## <a name="diagnosis-phase"></a>Fase de diagnóstico

Cada membro da equipe gasta até 30 minutos por dia útil categorizando novos problemas. Respondemos às seguintes perguntas:

- O problema é de documento ou de produto?
- Isso não é um problema, mas sim uma pergunta mais adequada para um fórum ou site de suporte?
- Qual é a prioridade do problema?
- Qual área gerencia esse problema?

Se essas perguntas não puderem ser respondidas no exame inicial, faremos perguntas de esclarecimento nos comentários.

Há tipos de problemas que são fechados durante a fase de diagnóstico e triagem:

- **Kudos**: agradecemos e fechamos o problema.
- **Problema de produto**: os problemas relacionados ao produto, e não à sua documentação, são fechados. Também podemos executar ações adicionais, como descrito abaixo.
- **Violações de CoC**: esses problemas serão fechados e relatados se a [violação de CoC](https://dotnetfoundation.org/code-of-conduct) merecer denúncia e bloqueio.
- **Duplicatas**: as duplicatas são fechadas com um comentário indicando o problema existente.
- **Doc-ok**: o cliente está errado, e o documento está correto.
- **Fórum**: os problemas que são solicitações de suporte ou do fórum são direcionados ao Stack Overflow ou outros sites de suporte e fechados.

### <a name="actions-on-product-issues"></a>Ações quanto a problemas de produto

Dependendo da natureza do problema de produto, podemos optar por:

- Transferir o problema para o repositório de produto apropriado.
- Fechar o problema como uma duplicata de solicitações de produtos existentes.
- Fechar o problema com uma recomendação para ser aberto no repositório de produto.

A avaliação do curso de ação correto é subjetiva. Os membros da equipe usam o bom senso para determinar a ação correta.

### <a name="actions-on-content-issues"></a>Ações quanto a problemas de conteúdo

Para outros problemas, a equipe:

- Atribui uma prioridade
- Atribui um marco, geralmente "Lista de pendências"
- Avalia se é um bom problema “up-for-grabs” (a distribuir) ou para os [Projetos para colaboradores da Comunidade .NET](https://github.com/dotnet/docs/projects/35)

Os níveis de prioridade são baseados nas diretrizes a seguir, mas são subjetivos. Os marcos também são subjetivos e se baseiam em outras prioridades, como agendas atuais de lançamentos de produtos e lançamentos futuros.

- **P0**: uma omissão ou um erro de documento impede que os clientes tenham sucesso em um cenário comum.
  - Os problemas **P0** são abordados nas próximas três semanas, tendo precedência sobre o trabalho agendado anteriormente.
- **P1**: uma omissão ou um erro de documento torna um cenário comum muito mais difícil ou bloqueia outros cenários conhecidos.
  - Os problemas **P1** são agendados em tempo hábil. Geralmente, os problemas P1 estão planejados para um marco futuro.
- **P2**: problemas que causam pequenos inconvenientes ou que afetam um artigo com pouca exibição de página.
  - Os problemas **P2** geralmente são corrigidos quando um artigo é atualizado por motivos de maior prioridade.
- **P3**: problemas que são solicitações para cenários de caso de borda.
  - Os problemas **P3** são colocados na lista de pendências e são considerados para atualização quando os artigos são atualizados por motivos de maior prioridade.

Os membros da equipe gastam uma quantidade limitada de tempo no diagnóstico e na triagem para que possam progredir nas tarefas agendadas. Cada membro da equipe passa no máximo 30 minutos por dia em diagnóstico e triagem.

O rótulo **up-for-grabs** (a distribuir) é aplicado quando um problema é um bom candidato para um membro da comunidade (possivelmente o autor) enviar uma correção. O membro da equipe que aplica o rótulo **up-for-grabs** (a distribuir) ajudará ou encontrará alguém para ajudar os membros da comunidade a trabalhar no processo de criação de PR. Problemas "up-for-grabs" costumam ser adicionados aos [Projetos de contribuição da comunidade](https://github.com/dotnet/docs/projects/35)

> OBSERVAÇÃO: recentemente, adotamos a convenção de precedência. A pessoa que adicionou o rótulo pode encaminhar você a outro membro da equipe, que o ajudará.

## <a name="resolution-phase"></a>Fase de resolução

Os problemas gerados pelo cliente são ponderados como parte do planejamento da tarefas agendadas. Cada membro da equipe aloca quatro horas por semana para resolver os problemas de maior prioridade do cliente.

A resolução do problema segue o nível de prioridade definido durante o diagnóstico. Os problemas recebidos dos clientes são priorizados com outro trabalho agendado de prioridade semelhante

- **P0**: assim que possível, durante as próximas três semanas.
- **P1**: agendado com outros trabalhos P1 planejados. Geralmente, isso significa nos próximos três meses.
- **P2**: agendado com outros trabalhos P2 planejados. Os problemas P2 são agendados regularmente com base na área e na visibilidade. Frequentemente, os problemas de P2 serão abordados quando um artigo for atualizado.
- **P3**: nenhuma garantia quanto à data de correção. Quando um artigo é atualizado, examinamos a lista de pendências para outros problemas no mesmo artigo.

Os problemas podem ser novamente priorizados com base nos novos comentários e dados sobre a visibilidade do artigo.
