---
title: "Razões para comparar e deslocar existente aplicativos .NET para aplicativos prontos para nuvem DevOps"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Razões para comparar e deslocar existente aplicativos .NET para aplicativos prontos para nuvem DevOps"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 941ca8d8fcb4d69f60282737851ab3e86b5782d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications"></a>Razões para comparar e deslocar existente aplicativos .NET para aplicativos prontos para nuvem DevOps

Com um aplicativo de nuvem DevOps pronto, você pode rapidamente e repetidamente entregar aplicativos confiáveis aos seus clientes. Você ganha agilidade essencial e a confiabilidade, adiando muito a complexidade operacional do seu aplicativo para a plataforma.

Se você não pode obter seus aplicativos para o mercado rapidamente, quando que você enviar seu aplicativo, o mercado que foram direcionamento será evoluíram. É tarde demais, independentemente de como o aplicativo foi projetado ou de engenharia. Você pode falhar ou não atingir seu pleno potencial porque não é possível sincronizar a entrega de aplicativos com as necessidades do mercado.

A necessidade de inovação de negócios contínuos envia as equipes de desenvolvimento e operações para o limite. É a única maneira de obter a agilidade que necessários na inovação dos negócios contínuos por modernizar seus aplicativos com tecnologias como contêineres e princípios de aplicativo pronta para a nuvem DevOps específicos.

O resultado final é que quando uma organização cria e gerencia os aplicativos que estão prontos para a nuvem DevOps, pode colocar soluções nas mãos de clientes mais cedo e colocar novas ideias no mercado quando forem relevantes.

## <a name="cloud-devops-ready-application-principles-and-tenets"></a>Noções básicas de aplicativos prontos para DevOps e princípios de nuvem 

Melhorias na nuvem geralmente são voltadas para atender a dois objetivos: reduzir os custos e melhorar o crescimento da empresa, melhorando a agilidade. Essas metas são alcançadas simplificar processos e reduzindo a fricção ao soltar e fornecer aplicativos.

Seu aplicativo está pronta para a nuvem DevOps se você pode um agile maneira-desenvolver seu aplicativo de forma independente de outros aplicativos de locais e, em seguida, versão, implantar, dimensionamento automático, monitorar e solucionar problemas de seu aplicativo na nuvem.

A chave é *agilidade*. Você não pode enviar com agilidade, a menos que você reduza ao mínimo absoluto qualquer implantação de produção problemas e problemas de ambiente de desenvolvimento e teste. Serviços gerenciados e contêineres (especificamente, Docker, como um padrão de fato) foram projetados especificamente para essa finalidade.

Para obter a agilidade, você também precisa de processos automatizados de DevOps com base em pipelines de CI/CD versão para plataformas dimensionáveis na nuvem. Plataformas de CI/CD (como o Visual Studio Team Services ou Jenkins) que implanta em uma plataforma de nuvem escalonáveis e resilientes (como o Azure Service Fabric ou Kubernetes) são as principais tecnologias para alcançar a agilidade na nuvem.

A lista a seguir descreve os principais princípios ou práticas recomendadas para aplicativos prontos para nuvem DevOps. Observe que você pode adotar todos ou apenas alguns desses princípios, uma abordagem progressiva ou incremental:

-   **Contêineres**. Contêineres oferecem a capacidade de incluir as dependências do aplicativo com o aplicativo em si. Enormemente reduz significativamente o número de problemas que pode ocorrer quando você implanta em ambientes de produção ou de teste em ambientes de preparo. Por fim, contêineres de melhoram a agilidade de entrega do aplicativo.

-   **Nuvem flexível e escalável**. A nuvem fornece uma plataforma que é gerenciado, Elástico, escalonável e flexível. Essas características são fundamentais para obter melhorias de custo e enviar altamente disponíveis e confiáveis de aplicativos em uma entrega contínua. Serviços gerenciados, como bancos de dados gerenciados, gerenciados como um serviço (CaaS) e armazenamento gerenciado são partes fundamentais na diminuindo os custos de manutenção de seu aplicativo de cache.

-   **Monitoramento**. Você não pode ter um aplicativo confiável sem ter uma boa maneira de detectar e diagnosticar problemas de desempenho do aplicativo e exceções. Você precisa obter ideias acionáveis por meio do gerenciamento de desempenho do aplicativo e análise imediata.

-   **DevOps cultura e fornecimento contínuo**. Adotar práticas pronta para a nuvem DevOps requer uma alteração de cultura em que as equipes deixará de funcionar em silos independentes. CI/CD pipelines são possíveis somente quando há um aumento na colaboração entre o desenvolvimento e as equipes de operações de TI, com suporte por contêineres e ferramentas de CI/CD.

Figura 4-2 mostra dos principais pilares opcionais de um aplicativo de nuvem DevOps pronto. Mais pilares implementar, readier de seu aplicativo atender às expectativas de seus clientes com êxito.

> ![Pilares principais de um aplicativo de nuvem DevOps pronto](./media/image2.png)
>
> **Figura 4-2.** Pilares principais de um aplicativo de nuvem DevOps pronto

Para resumir, um aplicativo pronto DevOps nuvem é uma abordagem para criar e gerenciar aplicativos que aproveita a computação de modelo, ao usar uma combinação de contêineres, infraestrutura de nuvem gerenciada, técnicas de aplicativo resiliente em nuvem monitoramento, fornecimento contínuo e DevOps, tudo sem a necessidade de refazer a arquitetura e recodificar seus aplicativos existentes.

Sua organização pode adotar gradualmente essas tecnologias e abordagens. Não é necessário adotar todos eles, ao mesmo tempo. Você pode adotá-los incrementalmente, dependendo de prioridades de empresa e as necessidades dos usuários.

## <a name="benefits-of-a-cloud-devops-ready-application"></a>Benefícios de um aplicativo de nuvem DevOps pronto

Você pode obter os seguintes benefícios convertendo um aplicativo existente para um aplicativo de nuvem DevOps pronto (sem rearquitetura ou codificação):

-   **Redução de custos, porque a infraestrutura gerenciada é tratada pelo provedor de nuvem**. Aplicativos em nuvem DevOps pronto obtém os benefícios da nuvem usando a alta disponibilidade, dimensionamento automático e elasticidade de fora da caixa da nuvem. Benefícios relacionados não apenas para os recursos de computação (VMs e contêineres), mas também dependem de recursos na nuvem, como DBaaS, CaaS e qualquer infraestrutura, um aplicativo poderá necessária.

-   **Aplicativo resiliente e infraestrutura**. Ao migrar para a nuvem, você precisa compreender falhas transitórias; falhas ocorrerão na nuvem. Além disso, hardware e infraestrutura de nuvem é "substituível," que aumenta a oportunidades de tempo de inatividade temporário. Ao mesmo tempo, recursos de nuvem interna e determinadas técnicas de desenvolvimento de aplicativo que implementam a resiliência e automatizam a recuperação facilitam muito para se recuperar de falhas inesperadas na nuvem.

-   **Visões mais aprofundadas de desempenho do aplicativo**. Ferramentas de monitoramento, como informações de aplicativo do Azure fornecem visualização para notificações, registro e gerenciamento de integridade na nuvem. Tornar aplicativos fácil depurar e auditar os logs de auditoria. Isso é fundamental para um aplicativo em nuvem confiável.

-   **Portabilidade de aplicativos, com implantações agile**. Contêineres (contêineres Linux ou Windows, com base no mecanismo do Docker) oferecem a melhor solução para evitar um aplicativo bloqueado de nuvem. Usando contêineres, hosts de Docker e orchestrators várias nuvens, você pode facilmente mover de um ambiente ou na nuvem para outra. Contêineres de eliminam o conflito que ocorre normalmente em implantações a qualquer ambiente (estágio/teste/produção).

Todos esses benefícios, por fim, fornecem reduções de custos de chave para o ciclo de vida do aplicativo de ponta a ponta.

Nas seções a seguir, esses benefícios são explicados em mais detalhes, em são vinculados para tecnologias específicas.

>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](microsoft-technologies-in-cloud-devops-ready-applications.md)
