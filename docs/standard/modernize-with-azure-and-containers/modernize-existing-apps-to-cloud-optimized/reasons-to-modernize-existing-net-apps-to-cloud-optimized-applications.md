---
title: Motivos para modernizar aplicativos existentes do .NET para aplicativos otimizados para a nuvem
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Motivos para modernizar aplicativos existentes do .NET para aplicativos otimizados para a nuvem
ms.date: 04/28/2018
ms.openlocfilehash: 5aa9828f65f76138461c18711fe03bdbe6a70ffd
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758751"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Motivos para modernizar aplicativos existentes do .NET para aplicativos otimizados para a nuvem

Com um aplicativo de otimização para nuvem, você pode rapidamente e repetidamente entregar aplicativos confiáveis aos seus clientes. Obtenha agilidade essencial e a confiabilidade, adiando muito da complexidade operacional do seu aplicativo para a plataforma.

Se você não conseguir obter seus aplicativos no mercado rapidamente, no momento em que você enviar seu aplicativo, o mercado que alvo fosse terá evoluído. Você pode estar muito tarde, não importa quão bem o aplicativo foi projetado ou engenharia. Você pode estar falhando ou não atingir seu pleno potencial porque você não pode sincronizar a entrega de aplicativos com as necessidades do mercado.

A necessidade de inovação de negócios contínuos envia as equipes de desenvolvimento e operações para o limite. É a única maneira de atingir a agilidade que você precisa na inovação de negócios contínua ao modernizar seus aplicativos com tecnologias como contêineres e princípios específicos de aplicativos otimizados para a nuvem.

O resultado final é que, quando uma organização cria e gerencia os aplicativos que são otimizados para a nuvem, ele pode colocar soluções nas mãos dos clientes mais cedo e traga novas ideias no mercado quando eles forem relevantes.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Filosofias e princípios de aplicativos otimizados para a nuvem 

Melhorias na nuvem concentram-se principalmente em atender a dois objetivos: Reduzir custos e aprimorar o crescimento dos negócios, aprimorando a agilidade. Essas metas são atingidas, simplificando os processos e reduzindo o atrito ao soltar e lançar aplicativos.

Seu aplicativo é otimizada para a nuvem se can na maneira-desenvolver seu aplicativo de forma independente de outros aplicativos de locais de um ágil e, em seguida, liberar, implantar, dimensionamento automático, monitorar e solucionar problemas do aplicativo na nuvem.

A chave é *agilidade*. Você não pode ser enviado com a agilidade, a menos que você reduza ao mínimo absoluto qualquer implantação de produção problemas e problemas de ambiente de desenvolvimento/teste. Serviços gerenciados e contêineres (especificamente, Docker, como um padrão de fato) foram projetados especificamente para essa finalidade.

Para alcançar a agilidade, você também precisa de processos automatizados de DevOps se baseiam em pipelines de CI/CD que liberam a plataformas escalonáveis na nuvem. Plataformas de CI/CD (como serviços de DevOps do Azure ou Jenkins) que implanta em uma plataforma de nuvem escalonável e flexível (como o serviço de aplicativo do Azure ou serviço Kubernetes do Azure) são tecnologias-chave para alcançar a agilidade na nuvem.

A lista a seguir descreve os principais princípios ou práticas recomendadas para aplicativos otimizados para a nuvem. Observe que você pode adotar uma todos ou apenas alguns desses princípios, uma abordagem progressiva ou incremental:

- **Contêineres**. Contêineres oferecem a capacidade de incluir as dependências de aplicativo com o aplicativo em si. Uso de contêineres reduz significativamente o número de problemas que você pode encontrar quando você implantar em ambientes de produção ou de teste em ambientes de preparo. Por fim, contêineres de melhorar a agilidade da entrega de aplicativos.

- **Nuvem flexível e escalável**. A nuvem fornece uma plataforma que é gerenciado, Elástico, escalonáveis e resilientes. Essas características são fundamentais para obter melhorias de custo e enviar altamente disponíveis e confiáveis de aplicativos em uma entrega contínua. Serviços gerenciados, como bancos de dados gerenciados, gerenciados armazenar em cache como um serviço (CaaS) e armazenamento gerenciado são partes fundamentais no diminuindo os custos de manutenção do seu aplicativo.

- **Monitoramento**. Você não pode ter um aplicativo confiável sem a necessidade de uma boa maneira de detectar e diagnosticar exceções e problemas de desempenho do aplicativo. Você precisa obter insights acionáveis por meio do gerenciamento de desempenho do aplicativo e análises instantâneas.

- **DevOps a entrega contínua e cultura**. Adotar práticas de DevOps exige uma mudança cultural em que as equipes não trabalham em silos independentes. Pipelines de CI/CD são possíveis somente quando há uma maior colaboração entre desenvolvimento e as equipes de operações de TI, com suporte por contêineres e ferramentas de CI/CD.

Figura 4-2 mostra os pilares principais opcionais de um aplicativo de otimização para nuvem. Os pilares mais implementar, readier de seu aplicativo tenha êxito atender às expectativas de seus clientes.

> ![Principais pilares de um aplicativo de otimização para nuvem](./media/image2.png)
>
> **Figura 4-2.** Principais pilares de um aplicativo de otimização para nuvem

Para resumir, um aplicativo de otimização de nuvem é uma abordagem para criar e gerenciar aplicativos que aproveita a computação em nuvem modelo, e usando uma combinação de contêineres, infraestrutura de nuvem gerenciado, técnicas de aplicativo resiliente, monitoramento, a entrega contínua e DevOps, tudo sem a necessidade de refazer a arquitetura e recodificar aplicativos existentes.

Sua organização pode adotar gradualmente essas tecnologias e abordagens. Você não precisa adotar todos eles, ao mesmo tempo. Você pode adotá-las de forma incremental, dependendo de prioridades de enterprise e necessidades dos usuários.

## <a name="benefits-of-a-cloud-optimized-application"></a>Benefícios de um aplicativo de otimização para nuvem

Você pode obter os seguintes benefícios ao converter um aplicativo existente para um aplicativo de otimização para nuvem (sem rearquitetura ou de codificação):

- **Redução de custos, porque a infraestrutura gerenciada é tratada pelo provedor de nuvem**. Otimização para nuvem aplicativos obtém os benefícios da nuvem usando a alta disponibilidade, dimensionamento automático e elasticidade de out-of-the-box da nuvem. Benefícios relacionados não apenas para os recursos de computação (VMs e contêineres), mas também dependem de recursos na nuvem, como DBaaS, CaaS e qualquer infraestrutura de um aplicativo talvez seja necessária.

- **Aplicativo resiliente e infraestrutura**. Quando você migra para a nuvem, você precisa adotar falhas transitórias; falhas ocorrerão na nuvem. Além disso, hardware e infraestrutura de nuvem são "substituíveis," que aumenta as oportunidades de tempo de inatividade temporário. Ao mesmo tempo, recursos de nuvem interna e determinadas técnicas de desenvolvimento de aplicativo que implementam a resiliência e automatizam a recuperação tornam muito mais fácil para se recuperar de falhas inesperadas na nuvem.

- **Desempenho do aplicativo insights mais aprofundados**. Ferramentas de monitoramento, como Azure Application Insights fornecem visualização para gerenciamento de saúde, registro em log e notificações de nuvem. Os logs de auditoria tornam os aplicativos mais fácil depurar e auditoria, fundamentais para um aplicativo de nuvem confiáveis.

- **Portabilidade do aplicativo, com implantações do agile**. Contêineres (contêineres Linux ou Windows, com base no mecanismo do Docker) oferecem a melhor solução para evitar um aplicativo bloqueado de nuvem. Ao usar orquestradores de várias nuvens, hosts do Docker e contêineres, você pode facilmente mover de um ambiente ou na nuvem para outro. Contêineres de eliminam a fricção que normalmente ocorre em implantações em qualquer ambiente (estágio/teste/produção).

Todos esses benefícios, por fim, fornecem reduções de custo de chave para seu ciclo de vida do aplicativo de ponta a ponta.

Nas seções a seguir, esses benefícios são explicados em mais detalhes e são vinculados a tecnologias específicas.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](microsoft-technologies-in-cloud-optimized-applications.md)
