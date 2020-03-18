---
title: Razões para modernizar os aplicativos .NET existentes para aplicativos otimizados para nuvem
description: Modernizar os aplicativos .NET existentes com contêineres Azure Cloud e Windows | Razões para modernizar os aplicativos .NET existentes para aplicativos otimizados para nuvem
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093627"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Razões para modernizar os aplicativos .NET existentes para aplicativos otimizados para nuvem

Com um aplicativo otimizado para nuvem, você pode fornecer aplicativos confiáveis e rápidas e rápidas aos seus clientes. Você ganha agilidade e confiabilidade essenciais adiando grande parte da complexidade operacional do seu aplicativo para a plataforma.

Se você não conseguir colocar seus aplicativos no mercado rapidamente, no momento em que você enviar seu aplicativo, o mercado que você estava mirando terá evoluído. Você pode ser tarde demais, não importa o quão bem a aplicação foi arquitetada ou projetada. Você pode estar falhando ou não atingindo todo o seu potencial porque você não pode sincronizar a entrega de aplicativos com as necessidades do mercado.

A necessidade de inovação contínua dos negócios leva as equipes de desenvolvimento e operações ao limite. A única maneira de alcançar a agilidade que você precisa na inovação contínua dos negócios é modernizando suas aplicações com tecnologias como contêineres e princípios específicos de aplicação otimizada para nuvem.

A conclusão é que quando uma organização constrói e gerencia aplicativos que são otimizados para nuvem, ele pode colocar soluções nas mãos dos clientes mais cedo e trazer novas ideias ao mercado quando elas forem relevantes.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Princípios e princípios de aplicação otimizados na nuvem

As melhorias na nuvem estão focadas principalmente no cumprimento de duas metas: reduzir custos e melhorar o crescimento dos negócios, melhorando a agilidade. Essas metas são alcançadas simplificando processos e reduzindo o atrito quando você libera e enviam aplicativos.

Seu aplicativo é otimizado para a nuvem se você puder desenvolver seu aplicativo de forma ágil de forma autônoma a partir de outros aplicativos locais e, em seguida, liberar, implantar, escalar automaticamente, monitorar e solucionar problemas do seu aplicativo na nuvem.

A chave é *a agilidade.* Você não pode enviar com agilidade a menos que você reduza a um mínimo absoluto quaisquer problemas de implantação para produção e problemas de ambiente de desenvolvimento/teste. Os contêineres (especificamente, Docker, como padrão de fato) e os serviços gerenciados foram projetados especificamente para este fim.

Para obter agilidade, você também precisa de processos automatizados de DevOps baseados em pipelines de CI/CD que são liberados para plataformas escaláveis na nuvem. Plataformas de CI/CD (como Azure DevOps Services ou Jenkins) que implantam em uma plataforma de nuvem escalável e resiliente (como o Azure App Service ou o Azure Kubernetes Service) são tecnologias-chave para alcançar agilidade na nuvem.

A lista a seguir descreve os principais princípios ou práticas para aplicativos otimizados para nuvem. Observe que você pode adotar todos ou apenas alguns desses princípios, em uma abordagem progressiva ou incremental:

- **Contêineres**. Os contêineres lhe dão a capacidade de incluir dependências de aplicativos com o próprio aplicativo. A contêinerização reduz significativamente o número de problemas que você pode encontrar quando você implanta em ambientes de produção ou teste em ambientes de preparação. Em última análise, os contêineres melhoram a agilidade da entrega do aplicativo.

- **Nuvem resistente e escalável.** A nuvem fornece uma plataforma gerenciada, elástica, escalável e resistente. Essas características são fundamentais para obter melhorias de custos e enviar aplicações altamente disponíveis e confiáveis em uma entrega contínua. Serviços gerenciados como bancos de dados gerenciados, cache gerenciado como serviço (CaaS) e armazenamento gerenciado são peças fundamentais para aliviar os custos de manutenção do seu aplicativo.

- **Monitoramento**. Você não pode ter um aplicativo confiável sem ter uma boa maneira de detectar e diagnosticar exceções e problemas de desempenho de aplicativos. Você precisa obter insights acionáveis através do gerenciamento de desempenho de aplicativos e análises instantâneas.

- **Cultura de DevOps e entrega contínua**. A adoção de práticas de DevOps requer uma mudança cultural na qual as equipes não trabalham mais em silos independentes. Os pipelines de CI/CD só são possíveis quando há uma colaboração maior entre as equipes de desenvolvimento e operações de TI, apoiadas por contêineres e ferramentas de CI/CD.

A Figura 4-2 mostra os principais pilares opcionais de uma aplicação otimizada para nuvem. Quanto mais pilares você implementar, mais leitura sua aplicação será para ter sucesso em atender às expectativas de seus clientes.

![Diagrama nomeando os principais pilares de uma aplicação otimizada para nuvem.](./media/main-pillars-cloud-optimized-application.png)

**Figura 4-2.** Principais pilares de uma aplicação otimizada para nuvem

Resumindo, um aplicativo otimizado para nuvem é uma abordagem para criar e gerenciar aplicativos que tira proveito do modelo de computação em nuvem, ao mesmo tempo em que usa uma combinação de contêineres, infra-estrutura de nuvem gerenciada, técnicas de aplicação resilientes, monitoramento, entrega contínua e DevOps, tudo sem a necessidade de reprojetar e recodificar seus aplicativos existentes.

Sua organização pode adotar essas tecnologias e abordagens gradualmente. Você não tem que abraçar todos eles, todos de uma vez. Você pode adotá-los gradualmente, dependendo das prioridades corporativas e das necessidades do usuário.

## <a name="benefits-of-a-cloud-optimized-application"></a>Benefícios de um aplicativo otimizado para nuvem

Você pode obter os seguintes benefícios convertendo um aplicativo existente em um aplicativo otimizado para nuvem (sem rearquitetura ou codificação):

- **Custos mais baixos, porque a infra-estrutura gerenciada é tratada pelo provedor de nuvem.** Aplicativos otimizados para nuvem obtêm os benefícios da nuvem usando a elasticidade, a escala automática e a alta disponibilidade da nuvem. Os benefícios estão relacionados não apenas aos recursos de computação (VMs e contêineres), mas também dependem de recursos na nuvem, como DBaaS, CaaS e qualquer infra-estrutura que um aplicativo possa precisar.

- **Aplicação e infra-estrutura resilientes.** Quando você migra para a nuvem, você precisa abraçar falhas transitórias; falhas ocorrerão na nuvem. Além disso, a infra-estrutura e o hardware em nuvem são "substituíveis", o que aumenta as oportunidades de inatividade transitória. Ao mesmo tempo, recursos internos em nuvem e certas técnicas de desenvolvimento de aplicativos que implementam resiliência e automatizam a recuperação tornam muito mais fácil se recuperar de falhas inesperadas na nuvem.

- **Insights mais profundos sobre o desempenho do aplicativo.** Ferramentas de monitoramento em nuvem, como o Azure Application Insights, fornecem visualização para gerenciamento de saúde, registro e notificações. Os registros de auditoria tornam os aplicativos fáceis de depurar e auditar, fundamentais para uma aplicação em nuvem confiável.

- **Portabilidade de aplicativos, com implantações ágeis.** Os contêineres (com base no Docker Engine) oferecem a melhor solução para evitar um aplicativo bloqueado na nuvem. Usando contêineres, hosts Docker e orquestradores de várias nuvens, você pode facilmente se mover de um ambiente ou nuvem para outro. Os recipientes eliminam o atrito que normalmente ocorre em implantações em qualquer ambiente (estágio/teste/produção).

Todos esses benefícios, em última análise, fornecem reduções de custos importantes para o ciclo de vida do aplicativo de ponta a ponta.

Nas seções a seguir, esses benefícios são explicados com mais detalhes e estão ligados a tecnologias específicas.

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](microsoft-technologies-in-cloud-optimized-applications.md)
