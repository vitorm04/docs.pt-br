---
title: Aplicativos candidatos para nativos da nuvem
description: Saiba quais tipos de aplicativos se beneficiam de uma abordagem nativa da nuvem
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805619"
---
# <a name="candidate-apps-for-cloud-native"></a>Aplicativos candidatos para nativos da nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Olhe para os aplicativos em seu portfólio. Quantos deles se qualificam para uma arquitetura nativa da nuvem? Todos eles? Talvez alguns?

Aplicando uma análise de custo/benefício, há uma boa chance de que a maioria não suportaria a etiqueta de preço pesada necessária para ser nativa da nuvem. O custo de ser nativo da nuvem excederia em muito o valor de negócios da aplicação.

Que tipo de candidatura pode ser um candidato para nativo da nuvem?

- Um sistema corporativo grande e estratégico que precisa evoluir constantemente os recursos/recursos dos negócios

- Um aplicativo que requer uma alta velocidade de liberação - com alta confiança

- Um sistema com onde os recursos individuais devem ser *liberados sem* uma reimplantação completa de todo o sistema

- Um aplicativo desenvolvido por equipes com expertise em diferentes pilhas de tecnologia

- Um aplicativo com componentes que devem ser dimensionados independentemente

Então há sistemas legados. Embora todos gostaríamos de construir novos aplicativos, muitas vezes somos responsáveis por modernizar cargas de trabalho legados que são fundamentais para os negócios. Com o tempo, um aplicativo legado pode ser decomposto em microsserviços, contêiner e, finalmente, "replataformado" em uma arquitetura nativa da nuvem.

### <a name="modernizing-legacy-apps"></a>Modernização de aplicativos legados

O e-book gratuito da Microsoft [Modernize os aplicativos .NET existentes com nuvem Azure e Contêineres Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fornece orientação para migrar cargas de trabalho no local para a nuvem. A Figura 1-10 mostra que não há uma única estratégia de tamanho único para modernizar aplicativos legados.

![Estratégias para migrar cargas de trabalho legados](./media/strategies-for-migrating-legacy-workloads.png)

**Figura 1-10**. Estratégias para migrar cargas de trabalho legados

Os aplicativos monolíticos que não são críticos beneficiam em grande parte de uma migração rápida de levantamento e mudança[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md) Aqui, a carga de trabalho no local é rehospedada em uma VM baseada em nuvem, sem alterações. Esta abordagem utiliza o [modelo IaaS (Infrastructure as a Service).](https://azure.microsoft.com/overview/what-is-iaas/) O Azure inclui várias ferramentas, como [o Azure Migrate,](https://azure.microsoft.com/services/azure-migrate/) [o Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)e [o Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) para facilitar esse movimento. Embora essa estratégia possa gerar alguma redução de custos, tais aplicativos normalmente não foram arquitetados para desbloquear e aproveitar os benefícios da computação em nuvem.

Aplicativos monolíticos que são críticos para os negócios muitas vezes se beneficiam de uma migração aprimorada de elevação e mudança *(Otimização da Nuvem).* Essa abordagem inclui otimizações de implantação que permitem os principais serviços de nuvem - sem alterar a arquitetura principal do aplicativo. Por exemplo, você pode [contêiner](https://docs.microsoft.com/virtualization/windowscontainers/about/) o aplicativo e implantá-lo em um orquestrador de [contêineres, como o Azure Kubernetes Services,](https://azure.microsoft.com/services/kubernetes-service/)discutido mais tarde neste livro. Uma vez na nuvem, o aplicativo poderia consumir outros serviços em nuvem, como bancos de dados, filas de mensagens, monitoramento e cache distribuído.

Finalmente, aplicativos monolíticos que executam funções corporativas estratégicas podem se beneficiar melhor de uma abordagem *Cloud-Native,* o tema deste livro. Essa abordagem proporciona agilidade e velocidade. Mas, ele vem a um custo de replataforma, rearquiteto e reescrever código.

Se você e sua equipe acreditam que uma abordagem nativa da nuvem é apropriada, cabe a você racionalizar a decisão com sua organização. Qual é exatamente o problema de negócios que uma abordagem nativa da nuvem resolverá? Como isso se alinharia às necessidades dos negócios?

- Lançamentos rápidos de recursos com maior confiança?

- Escalabilidade de grãos finos - uso mais eficiente de recursos?

- Melhor resiliência do sistema?

- Melhor desempenho do sistema?

- Mais visibilidade nas operações?

- Misturar plataformas de desenvolvimento e data stores para chegar à melhor ferramenta para o trabalho?

- Investimento em aplicações à prova de futuro?

A estratégia de migração correta depende das prioridades organizacionais e dos sistemas que você está mirando. Para muitos, pode ser mais econômico otimizar uma aplicação monolítica na nuvem ou adicionar serviços de grãos grossos a um aplicativo N-Tier. Nesses casos, você ainda pode fazer uso total dos recursos do PaaS na nuvem, como os oferecidos pelo Azure App Service.

## <a name="summary"></a>Resumo

Neste capítulo, introduzimos a computação nativa em nuvem. Fornecemos uma definição juntamente com os principais recursos que impulsionam um aplicativo nativo da nuvem. Analisamos os tipos de aplicações que podem justificar esse investimento e esforço.

Com a introdução por trás, agora mergulhamos em um olhar muito mais detalhado sobre os nativos das nuvens.

### <a name="references"></a>Referências

- [Fundação de Computação Nativa da Nuvem](https://www.cncf.io/)

- [.NET Microservices: Arquitetura para aplicativos .NET contêiner](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Modernize os aplicativos .NET existentes com a nuvem DoZure e os contêineres windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Padrões nativos da nuvem por Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Além da aplicação de doze fatores](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [O que é Infra-estrutura como Código](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Micro Implantação da Uber Engineering: Implantação diária com confiança](https://eng.uber.com/micro-deploy/)

- [Como a Netflix implanta código](https://www.infoq.com/news/2013/06/netflix/)

- [Controle de sobrecarga para dimensionamento de microserviços wechat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
>[Próximo](definition.md)
>[anterior](introduce-eshoponcontainers-reference-app.md)
