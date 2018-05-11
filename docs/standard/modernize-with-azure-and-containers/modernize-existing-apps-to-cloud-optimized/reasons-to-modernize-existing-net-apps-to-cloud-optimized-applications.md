---
title: Razões para modernizar aplicativos existentes do .NET para aplicativos com otimização de nuvem
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Razões para modernizar aplicativos existentes do .NET para aplicativos com otimização de nuvem
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: a874a742f6a5b32e15040ad0a237f0e0fa7908dc
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Razões para modernizar aplicativos existentes do .NET para aplicativos com otimização de nuvem

Com um aplicativo com otimização de nuvem, você pode rapidamente e repetidamente entregar aplicativos confiáveis aos seus clientes. Você ganha agilidade essencial e a confiabilidade, adiando muito a complexidade operacional do seu aplicativo para a plataforma.

Se você não pode obter seus aplicativos para o mercado rapidamente, quando que você enviar seu aplicativo, o mercado que foram direcionamento será evoluíram. É tarde demais, independentemente de como o aplicativo foi projetado ou de engenharia. Você pode falhar ou não atingir seu pleno potencial porque não é possível sincronizar a entrega de aplicativos com as necessidades do mercado.

A necessidade de inovação de negócios contínuos envia as equipes de desenvolvimento e operações para o limite. É a única maneira de obter a agilidade que necessários na inovação dos negócios contínuos por modernizar seus aplicativos com tecnologias como contêineres e princípios de aplicativo específico otimizada para a nuvem.

O resultado é que, quando uma organização cria e gerencia os aplicativos que são otimizados para nuvem, ele pode colocar soluções nas mãos de clientes mais cedo e colocar novas ideias no mercado quando forem relevantes.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Princípios e princípios de aplicativo com otimização de nuvem 

Melhorias na nuvem geralmente são voltadas para atender a dois objetivos: reduzir custos e aumentar o crescimento da empresa, melhorando a agilidade. Essas metas são alcançadas simplificar processos e reduzindo a fricção ao soltar e fornecer aplicativos.

Seu aplicativo é otimizada para a nuvem se você pode em um agile maneira-desenvolver seu aplicativo de forma independente de outros aplicativos de locais e, em seguida, solte, implantar, dimensionamento automático, monitorar e solucionar problemas de seu aplicativo na nuvem.

A chave é *agilidade*. Você não pode enviar com agilidade, a menos que você reduza ao mínimo absoluto qualquer implantação de produção problemas e problemas de ambiente de desenvolvimento e teste. Serviços gerenciados e contêineres (especificamente, Docker, como um padrão de fato) foram projetados especificamente para essa finalidade.

Para obter a agilidade, você também precisa de processos automatizados de DevOps com base em pipelines de CI/CD versão para plataformas dimensionáveis na nuvem. Plataformas de CI/CD (como o Visual Studio Team Services ou Jenkins) que implanta em uma plataforma de nuvem escalonáveis e resilientes (como o serviço de aplicativo do Azure, Azure Service Fabric ou serviço do Azure Kubernetes) são as principais tecnologias para alcançar a agilidade na nuvem.

A lista a seguir descreve os principais princípios ou práticas recomendadas para aplicativos com otimização de nuvem. Observe que você pode adotar todos ou apenas alguns desses princípios, uma abordagem progressiva ou incremental:

-   **Contêineres**. Contêineres oferecem a capacidade de incluir as dependências do aplicativo com o aplicativo em si. Enormemente reduz significativamente o número de problemas que pode ocorrer quando você implanta em ambientes de produção ou de teste em ambientes de preparo. Por fim, contêineres de melhoram a agilidade de entrega do aplicativo.

-   **Nuvem flexível e escalável**. A nuvem fornece uma plataforma que é gerenciado, Elástico, escalonável e flexível. Essas características são fundamentais para obter melhorias de custo e enviar altamente disponíveis e confiáveis de aplicativos em uma entrega contínua. Serviços gerenciados, como bancos de dados gerenciados, gerenciados como um serviço (CaaS) e armazenamento gerenciado são partes fundamentais na diminuindo os custos de manutenção de seu aplicativo de cache.

-   **Monitoramento**. Você não pode ter um aplicativo confiável sem ter uma boa maneira de detectar e diagnosticar problemas de desempenho do aplicativo e exceções. Você precisa obter ideias acionáveis por meio do gerenciamento de desempenho do aplicativo e análise imediata.

-   **DevOps cultura e fornecimento contínuo**. Adotar práticas DevOps requer uma alteração de cultura em que as equipes deixará de funcionar em silos independentes. CI/CD pipelines são possíveis somente quando há um aumento na colaboração entre o desenvolvimento e as equipes de operações de TI, com suporte por contêineres e ferramentas de CI/CD.

Figura 4-2 mostra dos principais pilares opcionais de um aplicativo otimizada para a nuvem. Mais pilares implementar, readier de seu aplicativo atender às expectativas de seus clientes com êxito.

> ![Pilares principais de um aplicativo com otimização de nuvem](./media/image2.png)
>
> **Figura 4-2.** Pilares principais de um aplicativo com otimização de nuvem

Para resumir, um aplicativo com otimização de nuvem é uma abordagem para criar e gerenciar aplicativos que aproveita a computação de modelo, ao usar uma combinação de contêineres, infraestrutura de nuvem gerenciada, técnicas de aplicativo resiliente em nuvem monitoramento, fornecimento contínuo e DevOps, tudo sem a necessidade de Refaça a arquitetura e recodificar seus aplicativos existentes.

Sua organização pode adotar gradualmente essas tecnologias e abordagens. Não é necessário adotar todos eles, ao mesmo tempo. Você pode adotá-los incrementalmente, dependendo de prioridades de empresa e as necessidades dos usuários.

## <a name="benefits-of-a-cloud-optimized-application"></a>Benefícios de um aplicativo com otimização de nuvem

Você pode obter os seguintes benefícios convertendo um aplicativo existente para um aplicativo com otimização de nuvem (sem rearchitecting ou codificação):

-   **Redução de custos, porque a infraestrutura gerenciada é tratada pelo provedor de nuvem**. Otimização de nuvem aplicativos obtém os benefícios da nuvem usando a alta disponibilidade, dimensionamento automático e elasticidade de fora da caixa da nuvem. Benefícios relacionados não apenas para os recursos de computação (VMs e contêineres), mas também dependem de recursos na nuvem, como DBaaS, CaaS e qualquer infraestrutura, um aplicativo poderá necessária.

-   **Aplicativo resiliente e infraestrutura**. Ao migrar para a nuvem, você precisa compreender falhas transitórias; falhas ocorrerão na nuvem. Além disso, hardware e infraestrutura de nuvem são "substituíveis," que aumenta a oportunidades de tempo de inatividade temporário. Ao mesmo tempo, recursos de nuvem interna e determinadas técnicas de desenvolvimento de aplicativo que implementam a resiliência e automatizam a recuperação facilitam muito para se recuperar de falhas inesperadas na nuvem.

-   **Visões mais aprofundadas de desempenho do aplicativo**. Ferramentas de monitoramento, como informações de aplicativo do Azure fornecem visualização para notificações, registro e gerenciamento de integridade na nuvem. Logs de auditoria facilitam a aplicativos depurar e auditoria, fundamentais para um aplicativo em nuvem confiável.

-   **Portabilidade de aplicativos, com implantações agile**. Contêineres (contêineres Linux ou Windows, com base no mecanismo do Docker) oferecem a melhor solução para evitar um aplicativo bloqueado de nuvem. Usando contêineres, hosts de Docker e orchestrators várias nuvens, você pode facilmente mover de um ambiente ou na nuvem para outra. Contêineres de eliminam o conflito que ocorre normalmente em implantações a qualquer ambiente (estágio/teste/produção).

Todos esses benefícios, por fim, fornecem reduções de custos de chave para o ciclo de vida do aplicativo de ponta a ponta.

Nas seções a seguir, esses benefícios são explicados em mais detalhes, em são vinculados para tecnologias específicas.

>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](microsoft-technologies-in-cloud-optimized-applications.md)
