---
title: Modernizar os aplicativos existentes do .NET com a nuvem do Azure e Contêineres do Windows
description: Saiba como comparar e deslocar aplicativos existentes para a nuvem do Azure e os contêineres com este livro eletrônico.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 3109cac1bd64587bb096a057f6f4ae99b055352a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-v10"></a>Modernizar aplicativos .NET existentes com contêineres do Windows e da Nuvem do Azure (v1.0)

![imagem da capa](./media/cover.png)

PUBLICADO POR  
Microsoft Press e Microsoft DevDiv  
Divisões da Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2017, Microsoft Corporation  

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida de nenhuma forma, nem por nenhum meio, sem a permissão por escrito do distribuidor.

Este livro está disponível gratuitamente na forma de um livro eletrônico (e-book) disponível por meio de diversos canais da Microsoft, como http://dot.net/architecture.

Se você tiver dúvidas relacionadas a esse livro, envie-as por email para [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor. Os modos de exibição, opiniões e informações expressada nesse catálogo, incluindo URLs e outras referências a sites da Internet, podem ser alteradas sem aviso prévio.

Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser deduzida.

Microsoft e marcas comerciais listadas no http://www.microsoft.com na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft. Todas as outras marcas são propriedade de seus respectivos proprietários.

Autor:
> **Cesar de la Torre**. PM, Equipe de Produto do .NET, Microsoft Corp.

Participantes e revisores:
> **Scott Hunter**, PM Diretor de Parceiro, equipe do .NET, Microsoft  
> **Paul Yuknewicz**, gerente de PM Principal, equipe das Ferramentas do Visual Studio, Microsoft  
> **Lisa Guthrie**, Sr. PM, equipe das Ferramentas do Visual Studio, Microsoft  
> **Ankit Asthana**, Gerente de PM Principal, equipe do .NET, Microsoft  
> **Unai Zorrilla**, líder de desenvolvimento, conceitos simples  
> **Javier Valero**, Diretor Executivo de Operações no Grupo Solutio  

## <a name="introduction"></a>Introdução

Quando você decidir modernizar seus aplicativos Web e movê-los para a nuvem, não é necessário refazer totalmente a arquitetura deles. Refazer a arquitetura de um aplicativo usando uma abordagem avançada como microsserviços nem sempre é uma opção devido a restrições de custo e tempo. Dependendo do tipo de aplicativo, refazer a arquitetura dele também pode não ser necessário. Para otimizar o custo-benefício da estratégia de migração de nuvem da sua organização, é importante considerar as necessidades do seu negócio e os requisitos dos seus aplicativos. Você precisará determinar:

- Quais aplicativos exigem uma transformação ou reformulação da arquitetura.

- Quais aplicativos precisam ser modernizado apenas parcialmente.

- Quais aplicativos podem usar a “migração lift-and-shift” diretamente para a nuvem.

## <a name="about-this-guide"></a>Sobre este guia

Este guia se concentra principalmente nos cenários de “lift-and-shift” e na modernização inicial de aplicativos Web ou orientados a serviços do Microsoft .NET Framework. Lift-and-shift é a ação de mover uma carga de trabalho para um ambiente mais novo e moderno sem alterar o código e a arquitetura básica do aplicativo.

Este guia descreve como mover seus aplicativos do servidor do .NET Framework existentes diretamente para a nuvem por áreas específicas de modernização sem refazer a arquitetura ou o código inteiro dos aplicativos.

Este guia também destaca os benefícios de mover seus aplicativos para a nuvem e modernizar parcialmente os aplicativos usando um conjunto específico de novas tecnologias e abordagens, como Contêineres do Windows e orquestradores no Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Caminho para a nuvem para aplicativos .NET existentes

As organizações normalmente optam por mover para a nuvem devido à agilidade e à velocidade oferecida aos seus aplicativos. Você pode configurar milhares de servidores (VMs) na nuvem em questão de minutos, em comparação com as semanas de configuração de servidores locais normais.

Não há uma estratégia única e padronizada para migrar aplicativos para a nuvem. A estratégia de migração certa para você depende das necessidades e prioridades da sua organização, bem como o tipo de aplicativos que você está migrando. Nem todos os aplicativos valem o investimento de mudar para um modelo de [PaaS](https://azure.microsoft.com/overview/what-is-paas/) (plataforma como serviço) ou de desenvolver um modelo de aplicativo [nativo de nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Em muitos casos, você pode adotar uma abordagem em fases ou incremental para investir na movimentação de seus ativos para a nuvem, dependendo das suas necessidades de negócios.

Para aplicativos modernos com a melhor agilidade e valor a longo prazo para a organização, você pode se beneficiar de investir em arquiteturas de aplicativo *otimizadas para a nuvem* e *nativas da nuvem*. No entanto, para aplicativos que são ativos existentes ou herdados, é essencial gastar o mínimo possível de tempo e dinheiro (sem nova arquitetura ou alterações de código) ao movê-los para a nuvem, para perceber benefícios significativos.

A Figura 1-1 mostra os caminhos possíveis que podem ser escolhidos ao mover os aplicativos .NET existente para a nuvem em fases incrementais.

 ![Caminhos de modernização para aplicativos e serviços .NET existentes](./media/image1-1.png)

> **Figura 1-1**. Caminhos de modernização para aplicativos e serviços .NET existentes

Cada abordagem de migração traz diferentes vantagens e motivos para usá-la. Você pode escolher uma abordagem única ao migrar aplicativos para a nuvem ou escolher certos componentes de várias abordagens. Aplicativos individuais não estão limitados a uma única abordagem ou estado de maturidade. Por exemplo, uma abordagem híbrida comum teria determinados componentes locais e outros componentes na nuvem.

Nos dois primeiros níveis de migração, basta migrar seus aplicativos por lift-and-shift:

**Nível 1: pronto para infraestrutura de nuvem**: nessa abordagem de migração, você simplesmente realoca para um novo host ou muda os aplicativos locais atuais para uma plataforma [IaaS](https://azure.microsoft.com/overview/what-is-iaas/) (infraestrutura como serviço). Os aplicativos têm quase a mesma composição de antes, mas agora você os implanta em VMs na nuvem.

**Nível 2: pronto para DevOps na Nuvem**: nesse nível, depois do lift-and-shift inicial e ainda sem refazer a arquitetura ou alterar o código, você pode obter ainda mais benefícios ao executar seu aplicativo na nuvem. Melhore a agilidade dos seus aplicativos para distribuição mais rápida refinando seus processos de DevOps (operações de desenvolvimento) corporativas. Você pode fazer isso usando uma tecnologia como Contêineres do Windows, que é baseada no Mecanismo do Docker. Contêineres removem a fricção que é causada pelas dependências de aplicativo ao implantar em vários estágios. Contêineres também usam serviços de nuvem gerenciados adicionais relacionados a dados, monitoramento e integração contínua/contínua pipelines de implantação (CI/CD).

O terceiro nível de maturidade é a meta final na nuvem, mas é opcional para muitos aplicativos e não é o foco principal deste guia:

**Nível 3: otimização para nuvem**: essa abordagem de migração é geralmente ocasionada por necessidade de negócio e é voltada para modernização de seus aplicativos críticos. Nesse nível, você pode usar os serviços de PaaS para mover seus aplicativos para plataformas de computação de PaaS. Implemente aplicativos [nativos da nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) e arquitetura de microsserviços para desenvolver aplicativos com agilidade de longo prazo e dimensionar para novos limites. Esse tipo de modernização normalmente requer arquitetura específica para a nuvem. Geralmente é necessário escrever novo código, especialmente ao mover aplicativos nativos de nuvem e modelos baseados em microsserviços. Essa abordagem pode ajudar a obter os benefícios que são difíceis de obter no seu ambiente de aplicativo local e monolítico.

A Tabela 1-1 descreve as principais vantagens e motivos para escolher cada abordagem de migração ou modernização.

| **Pronto para infraestrutura de nuvem** <br /> *Lift-and-shift* | **Pronto para DevOps na Nuvem** <br /> *Lift-and-shift* | **Otimização para nuvem** *Modernizar/refatorar/reescrever* |
|---|---|---|
| **Destino de computação do aplicativo** |
| Aplicativos implantados em VMs no Azure | Aplicativos monolíticos em contêineres ou de N camadas implantados em VMs, no Azure Service Fabric ou no Serviço de Contêiner do Azure (ou seja, Kubernetes) | Microsserviços em contêineres ou aplicativos regulares baseados em PaaS no Serviço de Aplicativo do Azure, Azure Service Fabric, Serviço de Contêiner do Azure (ou seja, Kubernetes) |
| **Destino de dados** |
| SQL ou qualquer banco de dados relacional em uma VM | Instância Gerenciada do Banco de Dados SQL do Azure | Banco de Dados SQL do Azure, Azure Cosmos DB ou outros NoSQL |
| **Vantagens**|
| <li>Sem refazer a arquitetura, sem novo código <li> Mínimo de esforço para migração rápida <li> Mínimo denominador comum com suporte no Azure <li> Garantias básicas de disponibilidade <li> Depois de mudar para a nuvem, é mais fácil modernizar ainda mais | <li>Sem refazer a arquitetura, sem novo código <li> Contêineres oferecem um esforço incremental pequeno em comparação a VMs <li> Melhoria na implantação e agilidade de DevOps para liberação devido a contêineres <li> Aumento da densidade e redução dos custos de implantação <li> Portabilidade de aplicativos e dependências <li> Com o Serviço de Contêiner do Azure (ou Kubernetes) e o Azure Service Fabric, fornece alta disponibilidade e orquestração <li> Nós/aplicação de patches em VM no Service Fabric <li> Flexibilidade de destinos de host: conjuntos de escala de máquinas virtuais do Azure ou da máquina virtual, serviço de contêiner do Azure (ou Kubernetes), Service Fabric e futuras opções baseadas no contêiner | <li>Arquitetura de nuvem, refatorar, necessidade de novo código <li> Abordagens de microsserviços nativos de nuvem <li> Novos aplicativos Web, monolíticos, de N camadas, resilientes e otimizados para nuvem <li> Serviços totalmente gerenciados <li> Aplicação de patch automática <li> Otimizado para escala <li> Otimizado para agilidade autônoma por subsistema <li> Baseado em implantação e DevOps <li> DevOps avançado, como estratégias de slots e de implantação <li> Destinos de PaaS e orquestrador: Serviço de Aplicativo do Azure, Serviço de Contêiner do Azure (ou Kubernetes), Azure Service Fabric e futuros PaaS baseadas em contêiner |
| **Desafios** |
| <li> Menor valor de nuvem, diferente da mudança no custo de operação ou o fechamento de datacenters <li> Pouquíssimo gerenciamento: nenhuma aplicação de patch de sistema operacional ou de middleware; é possível usar soluções de infraestrutura como Terraform, Spinnaker ou Puppet | <li> O desenvolvimento de contêineres é uma etapa adicional na curva de aprendizado que exige imutabilidade | <li> Pode ser necessário refatorar ou rescrever o código significativamente (aumento no tempo e no orçamento) |
> **Tabela 1-1.** Benefícios e desafios de caminhos de modernização para serviços e aplicativos .NET existentes

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Principais tecnologias e arquiteturas por nível de maturidade

Aplicativos do .NET Framework inicialmente começavam com o .NET Framework versão 1.0, que foi lançado no final de 2001. Assim, as empresas são movidas para versões mais recentes (como 2.0, 3.5 e .NET 4.x). A maioria dos aplicativos executados no Windows Server e o servidor de informações da Internet (IIS) e usado um banco de dados relacional, como o SQL Server, Oracle, MySQL ou quaisquer outros RDBMS.

A maioria dos aplicativos .NET existentes hoje em dia se baseia no .NET Framework 4.x ou até mesmo no .NET Framework 3.5 e usa estruturas da Web como o ASP.NET MVC, Web Forms do ASP.NET, API Web ASP.NET, WCF (Windows Communication Foundation), ASP.NET SignalR e Páginas da Web ASP.NET. Esses tecnologias estabelecidas do .NET Framework dependem do Windows. É importante considerar essa dependência se você estiver migrando simplesmente migrando aplicativos herdados e deseja realizar o mínimo de alterações na sua infraestrutura de aplicativo.

A Figura 1-2 mostra as principais tecnologias e estilos de arquitetura usados em cada um dos três níveis de maturidade de nuvem:

![Principais tecnologias para cada nível de maturidade para modernizar aplicativos Web .NET existentes](./media/image1-2.png)

> **Figura 1-2.** Principais tecnologias para cada nível de maturidade para modernizar aplicativos Web .NET existentes

A Figura 1-2 realça os cenários mais comuns, mas muitas variações híbridas e mistas são possíveis quando se trata de arquitetura. Por exemplo, os modelos de maturidade se aplicam não apenas a arquiteturas monolíticas em aplicativos Web existentes, mas também a arquiteturas com orientação de serviço, de N camadas e outras variações de estilo de arquiteturas.

Cada nível de maturidade no processo de modernização está associado às seguintes tecnologias e abordagens principais:

- **Pronto para infraestrutura de nuvem** (novo host ou lift-and-shift básico ): como uma primeira etapa, muitas organizações desejam apenas executar rapidamente uma estratégia de migração de nuvem. Nesse caso, os aplicativos são simplesmente hospedados novamente. A maioria da nova hospedagem pode ser automatizada usando as [Migrações para Azure](https://aka.ms/azuremigrate), um serviço que fornece as diretrizes, os insights e os mecanismos necessários para ajudar você a migrar para o Azure com base em ferramentas de nuvem como o [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) e o [Serviço de Migração do Banco de Dados do Azure](https://azure.microsoft.com/campaigns/database-migration/). Você também pode definir a nova hospedagem manualmente, para que seja possível conhecer os detalhes da infraestrutura sobre seus ativos ao mover aplicativos herdados para a nuvem. Por exemplo, você pode mover seus aplicativos para VMs no Azure com pouquíssimas modificações, provavelmente com apenas alterações simples de configuração. Nesse caso, a rede é semelhante a um ambiente local, especialmente se você criar redes virtuais no Azure.

- **Pronto para DevOps na Nuvem** (lift-and-shift aprimorado): esse modelo fará algumas otimizações de implantação importante para obter alguns benefícios significativos da nuvem, sem mudar a arquitetura principal do aplicativo. A etapa fundamental aqui é adicionar suporte a [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) aos seus aplicativos .NET Framework existentes. Essa importante etapa (colocação em contêineres) não requer alteração no código, portanto, o esforço de lift-and-shift geral é muito baixo. Você pode usar ferramentas como [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ou o Visual Studio, com as suas ferramentas para [Docker](https://www.docker.com/). O Visual Studio escolhe automaticamente padrões inteligentes para aplicativos ASP.NET e imagens de Contêineres do Windows. Essas ferramentas oferecem um loop interno ágil e um caminho rápido para levar os contêineres para o Azure. A agilidade é melhorada ao implantar em vários ambientes. Assim, passando para a produção, você pode implantar os Contêineres do Windows para orquestradores como [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) ou o [Serviço de Contêiner do Azure](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS ou Swarm). Durante essa modernização inicial, também é possível adicionar ativos da nuvem, como monitoramento com ferramentas como o [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); pipelines de CI/CD para o ciclo de vida dos aplicativo com o [Visual Studio Team Services](https://www.visualstudio.com/team-services/) e muitos outros serviços de recurso de dados que estão disponíveis no Azure. Por exemplo, é possível modificar um aplicativo Web monolítico que foi originalmente desenvolvido usando [Web Forms do ASP.NET](https://www.asp.net/web-forms) ou [ASP.NET MVC](https://www.asp.net/mvc) tradicionais, mas agora ele é implantado usando os Contêineres do Windows. Se você usar Contêineres do Windows, também deverá migrar os dados para um banco de dados em uma [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/), tudo sem alterar a arquitetura principal do seu aplicativo.

- **Otimização para nuvem**: conforme observado, a meta final ao modernizar aplicativos na nuvem é basear seu sistema em plataformas PaaS como o [Serviço de Aplicativo do Azure](https://azure.microsoft.com/services/app-service/). Plataformas de PaaS se concentram em aplicativos Web modernos e estendem seus aplicativos com novos serviços baseados em [computação sem servidor](https://azure.microsoft.com/overview/serverless-computing/) e plataformas como o [Azure Functions](https://azure.microsoft.com/services/functions/). O segundo cenário nesse modelo de maturidade, mais avançado, é sobre arquiteturas de microsserviços e aplicativos [nativos da nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications), que normalmente usam orquestradores como o [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) ou o [Serviço de Contêiner do Azure](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS ou Swarm). Esses orquestradores são feitos especificamente para microsserviços e aplicativos com vários contêineres. Todas essas abordagens (como microsserviços e PaaS) geralmente requerem que você escreva novo código, que deverá ser adaptado a plataformas específicas do PaaS ou alinhado a arquiteturas específicas, como microsserviços.

A Figura 1-3 mostra as tecnologias internas que você pode usar para cada nível de maturidade:

![Tecnologias internas para cada nível de maturidade de modernização](./media/image1-3.png)

> **Figura 1-3.** Tecnologias internas para cada nível de maturidade de modernização

## <a name="lift-and-shift-scenarios"></a>Cenários de lift-and-shift

Para usar migrações lift-and-shift, lembre-se que é possível usar muitas variações diferentes de migração lift-and-shift nos seus cenários de aplicativo. Se você é apenas o novo host do seu aplicativo, você pode ter um cenário semelhante ao mostrado na Figura 1-4, em que as VMs na nuvem são usadas apenas para seu aplicativo e para o servidor de banco de dados.

![Exemplo de um cenário de IaaS puro na nuvem](./media/image1-4.png)

> **Figura 1-4**. Exemplo de um cenário de IaaS puro na nuvem

Mais adiante, você poderá ter um aplicativo puramente pronto para DevOps na Nuvem que usa elementos apenas do nível de maturidade em questão. Ou, talvez você tenha um aplicativo de estado intermediário com alguns elementos Prontos para Infraestrutura de Nuvem e outros elementos Prontos para DevOps na Nuvem (uma modelo misto de “escolha”), como na Figura 1-5.

![Cenário de exemplo de "Escolha", com o banco de dados no IaaS, DevOps e ativos em contêineres](./media/image1-5.png)

> **Figura 1-5.** Cenário de exemplo de "Escolha", com o banco de dados no IaaS, DevOps e ativos em contêineres

Em seguida, como o cenário ideal para muitos aplicativos do .NET Framework a migração, você pode migrar para um aplicativo pronta para a nuvem DevOps, para obter benefícios significativos de pouco de trabalho. Essa abordagem também prepara você para otimização de nuvem como uma possível etapa futura. A Figura 1-6 mostra um exemplo.

![Cenário de exemplo de aplicativos para DevOps na Nuvem, com Contêineres do Windows e serviços gerenciados](./media/image1-6.png)

> **Figura 1-6.** Cenário de exemplo de aplicativos para DevOps na Nuvem, com Contêineres do Windows e serviços gerenciados

Indo ainda mais além, você poderia estender o seu aplicativo pronto para DevOps na Nuvem adicionando alguns microsserviços para cenários específicos. Isso moverá você parcialmente para o nível nativo de nuvem no modelo de Otimização para Nuvem, que não é o foco deste guia.


## <a name="what-this-guide-does-not-cover"></a>O que este guia não cobre

Este guia abrange um subconjunto específico de cenários de exemplo, conforme mostrado na Figura 1-7. Este guia se concentra apenas em cenários de lift-and-shift e, por fim, no modelo pronto para DevOps na Nuvem. No modelo pronto para DevOps na Nuvem, um aplicativo do .NET Framework é modernizado usando os Contêineres do Windows, além de componentes adicionais como o monitoramento e pipelines de CI/CD. Cada componente é fundamental para implantar aplicativos na nuvem de maneira mais rápida e ágil.

![Migração lift-and-shift e modernização inicial para aplicativos prontos para DevOps na Nuvem](./media/image1-7.png)

> **Figura 1-7.** Migração lift-and-shift e modernização inicial para aplicativos prontos para DevOps na Nuvem

O foco deste guia é específico. Ele mostra o caminho que você pode tomar para obter uma comparação de precisão e a mudança de seus aplicativos existentes do .NET, sem refazer a arquitetura e sem alterações de código. Por fim, ele mostra como tornar seu aplicativo pronta para a nuvem DevOps.

Este guia não mostra como trabalhar com aplicativos de nuvem nativo, por exemplo, como desenvolver uma arquitetura de microservices. Para refazer a arquitetura de seus aplicativos ou criar novos aplicativos baseados em microsserviços, consulte o livro eletrônico [.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook) (Microsserviços do .NET: arquitetura para aplicativos em contêineres do .NET).

### <a name="additional-resources"></a>Recursos adicionais

- **Em contêineres de Docker o ciclo de vida do aplicativo com o Microsoft platform e ferramentas** (que pode ser baixado e-book): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET Microservices: Arquitetura para aplicativos .NET em contêineres** (que pode ser baixado e-book): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **Arquitetura de aplicativos web modernos com ASP.NET Core e o Azure** (que pode ser baixado e-book): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

Este guia foi elaborado para desenvolvedores e arquitetos de solução que deseja modernizar aplicativos ASP.NET baseados em .NET Framework, para aumento da agilidade no envio e liberação de aplicativos.

Você também pode achar este guia útil se for um tomador de decisões técnicas, como um arquiteto corporativo ou um líder de desenvolvimento/diretor que deseja ter apenas uma visão geral dos benefícios que podem ser alcançados usando Contêineres do Windows e implantando na nuvem ao usar o Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Como usar este guia

Este guia aborda “o porquê”, isto é, por que modernizar seus aplicativos existentes e os benefícios específicos obtidos ao usar os Contêineres do Windows ao mover seus aplicativos para a nuvem. O conteúdo dos primeiros capítulos do guia destina-se a arquitetos e tomadores de decisões técnicas que desejam obter uma visão geral, mas que não precisam se concentrar nos detalhes técnicos passo a passo nem na implementação.

O último capítulo deste guia apresenta vários tutoriais passo a passo que se concentram em cenários de implantação específicos. Este guia oferece versões de instruções passo a passo, menores para resumir os cenários e realçar os seus benefícios. Os tutoriais passo a passo completos detalham a configuração e a implementação e são publicados como um conjunto de [postagens de wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) no mesmo [repositório do GitHub](https://github.com/dotnet-architecture/eShopModernizing) público em que residem os aplicativos de exemplo relacionados (discutido na próxima seção). O último capítulo e os tutoriais da wiki passo a passo no GitHub serão mais interessantes para desenvolvedores e arquitetos que desejam se concentrar nos detalhes de implementação.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Aplicativos de exemplo para modernização de aplicativos herdados: eShopModernizing

O repositório [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) no GitHub oferece dois aplicativos de exemplo que simulam aplicativos Web monolíticos herdados. Um aplicativo Web é desenvolvido usando o ASP.NET MVC; o segundo aplicativo Web desenvolvido usando o Web Forms do ASP.NET. Ambos os aplicativos Web são baseados no .NET Framework tradicional. Esses aplicativos de exemplo não usam o .NET Core ou o ASP.NET Core, pois eles se destinam a aplicativos do .NET Framework existentes/herdados que serão modernizados.

Os dois aplicativos de exemplo têm uma segunda versão, com o código modernizado e que são bastante simples. A diferença mais importante entre as versões do aplicativo é que as segundas versões usam Contêineres do Windows como a opção de implantação. Também há algumas adições para as segundas versões, como Blobs de Armazenamento do Microsoft Azure para gerenciar imagens, Azure Active Directory para gerenciar a segurança e o Azure Application Insights para monitorar e auditar os aplicativos.

## <a name="send-your-feedback"></a>Envie seus comentários

Este guia foi elaborado para ajudá-lo a entender as opções para melhorar e modernizar os aplicativos web .NET existentes. O guia e os aplicativos de exemplo relacionados estão em evolução. Seus comentários são bem-vindo! Se você tiver comentários sobre como este guia poderia ser mais útil, envie-os para [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Avançar](lift-and-shift-existing-apps-azure-iaas.md)
