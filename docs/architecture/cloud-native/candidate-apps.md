---
title: Aplicativos candidatos para nuvem nativa
description: Saiba quais tipos de aplicativos se beneficiam de uma abordagem nativa de nuvem
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: a06ecdd9bfb3bd50757c484115eb123862a1bb9e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214011"
---
# <a name="candidate-apps-for-cloud-native"></a>Aplicativos candidatos para nuvem nativa

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Examine os aplicativos em seu portfólio. Quantas delas se qualificam para uma arquitetura nativa de nuvem? Todos eles? Talvez alguns?

Aplicando uma análise de custo/benefício, há uma boa chance de que a maioria não dê suporte à marca de preço pesada necessária para ser nativa na nuvem. O custo de ser nativo na nuvem excedeu muito o valor comercial do aplicativo.

Que tipo de aplicativo pode ser um candidato para a nuvem nativa?

- Um sistema empresarial grande e estratégico que precisa desenvolver constantemente recursos/recursos de negócios

- Um aplicativo que requer uma velocidade de liberação alta – com alta confiança

- Um sistema com o qual os recursos individuais devem ser liberados *sem* uma reimplantação completa de todo o sistema

- Um aplicativo desenvolvido por equipes com experiência em diferentes pilhas de tecnologia

- Um aplicativo com componentes que devem ser dimensionados de forma independente

Em seguida, há sistemas herdados. Embora todos gostaríamos de criar novos aplicativos, muitas vezes somos responsáveis por modernizar cargas de trabalho herdadas que são críticas para os negócios. Ao longo do tempo, um aplicativo herdado poderia ser decomposto em microserviços, em contêineres e, por fim, "replataforma" em uma arquitetura nativa de nuvem.  

### <a name="modernizing-legacy-apps"></a>Modernizando aplicativos herdados

O Microsoft e-book gratuito [modernizar aplicativos .net existentes com a nuvem do Azure e contêineres do Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) fornece orientação para migrar cargas de trabalho locais para a nuvem. A Figura 1-8 mostra que não há uma estratégia única de um único tamanho para modernizar aplicativos herdados.

![Estratégias para migrar cargas de](./media/strategies-for-migrating-legacy-workloads.png)
trabalho herdadas**Figura 1-8**. Estratégias para migrar cargas de trabalho herdadas

Aplicativos monolíticos que não são críticos amplamente se beneficiam de uma migração rápida de comparação de precisão e mudança ([pronta para a infraestrutura de nuvem](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)). Aqui, a carga de trabalho local é rehospedada para uma VM baseada em nuvem, sem alterações. Essa abordagem usa o [modelo IaaS (infraestrutura como serviço)](https://azure.microsoft.com/overview/what-is-iaas/). O Azure inclui várias ferramentas como ([migrações para Azure](https://aka.ms/azuremigrate), [Azure site Recovery](https://azure.microsoft.com/services/site-recovery/)e serviço de migração de [banco de dados do Azure](https://azure.microsoft.com/campaigns/database-migration/)) para facilitar a movimentação. Embora essa estratégia possa gerar alguma economia de custos, esses aplicativos normalmente não eram arquitetados para desbloquear e aproveitar os benefícios da computação em nuvem. 

Os aplicativos monolíticos que são essenciais para os negócios muitas vezes se beneficiam de uma migração avançada de comparação de precisão e deslocamento (*otimizada para nuvem*). Essa abordagem inclui otimizações de implantação que habilitam os principais serviços de nuvem, sem alterar a arquitetura principal do aplicativo. Por exemplo, você pode colocar o aplicativo em [contêiner](https://docs.microsoft.com/virtualization/windowscontainers/about/) e implantá-lo em um orquestrador de contêiner, como os [Serviços Kubernetess do Azure](https://azure.microsoft.com/services/kubernetes-service/), discutidos posteriormente neste livro. Uma vez na nuvem, o aplicativo poderia consumir outros serviços de nuvem, como bancos de dados, filas de mensagens, monitoramento e Caching distribuído.

Por fim, os aplicativos monolíticos que executam funções empresariais estratégicas podem se beneficiar melhor de uma abordagem *nativa de nuvem* , o assunto deste livro. Essa abordagem fornece agilidade e velocidade. Mas, ele vem a um custo de replataforma, rearquitetura e reescrita de código.

Se você e sua equipe acreditarem que uma abordagem nativa de nuvem é apropriada, ela convém você a racionalizar a decisão com sua organização. O que é exatamente o problema de negócios que uma abordagem nativa de nuvem resolverá? Como ele se alinharia com as necessidades dos negócios?

- Versões rápidas de recursos com maior confiança?

- Escalabilidade refinada-uso mais eficiente de recursos?

- Maior resiliência do sistema?

- Melhor desempenho do sistema?

- Mais visibilidade de operações?

- As plataformas de desenvolvimento de Blend e armazenamentos de dados chegam à melhor ferramenta para o trabalho?

- Investimento de aplicativos à prova de futuro?

A estratégia de migração certa depende das prioridades organizacionais e dos sistemas que você está direcionando. Para muitos, pode ser mais econômico para otimizar a nuvem um aplicativo monolítico ou adicionar serviços de alta granularidade a um aplicativo de N camadas. Nesses casos, você ainda pode fazer uso completo de recursos de PaaS de nuvem como os oferecidos pelo serviço Azure App.

## <a name="summary"></a>Resumo

Neste capítulo, introduzimos a computação nativa de nuvem. Fornecemos uma definição junto com os principais recursos que orientam um aplicativo nativo de nuvem. Nós examinamos os tipos de aplicativos que podem justificar esse investimento e esforço.

Com a introdução por trás, agora nos aprofundamos em uma visão muito mais detalhada na nuvem nativa.

### <a name="references"></a>Referências

- [Computação nativa da nuvem Foundation](https://www.cncf.io/)

- [Microsserviços do .NET: Arquitetura para aplicativos .NET em contêineres](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [Padrões de nuvem nativa por Cornelia Davis](https://www.manning.com/books/cloud-native-patterns)

- [Além do aplicativo de doze fatores](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [O que é infraestrutura como código](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [Micro Deploy de engenharia de Uber: Implantando diariamente com confiança](https://eng.uber.com/micro-deploy/)

- [Como o Netflix implanta o código](https://www.infoq.com/news/2013/06/netflix/)

- [Controle de sobrecarga para dimensionar microserviços WeChat](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

- [O Raygun-estudo de caso](https://raygun.com/case-study/ovation)

>[!div class="step-by-step"]
>[Anterior](definition.md)
>[Próximo](introduce-eshoponcontainers-reference-app.md)
