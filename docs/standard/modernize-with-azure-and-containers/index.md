---
title: Modernizar .NET aplicativos com Azure nuvem existente e contêineres do Windows (2ª edição)
description: Aprenda a comparação de precisão e shift e modernizar aplicativos existentes para a nuvem do Azure e os contêineres com este livro eletrônico.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 4/28/2018
ms.openlocfilehash: 3fcfdca68e05494785148cbbe149cdc2f812c577
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956377"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure (2ª edição)

![imagem da capa](./media/cover.png)

PUBLICADO POR  
Microsoft Press e Microsoft DevDiv  
Divisões da Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018 pela Microsoft Corporation  

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

Quando você decidir modernizar seus aplicativos ou serviços e movê-los para a nuvem, você não precisa necessariamente totalmente Refaça a arquitetura de seus aplicativos. Rearchitecting um aplicativo usando uma abordagem avançada como microservices nem sempre é uma opção devido a restrições de custo e tempo. Dependendo do tipo de aplicativo, rearchitecting um aplicativo também pode não ser necessário. Para otimizar o custo-benefício da estratégia de migração de nuvem da sua organização, é importante considerar as necessidades do seu negócio e os requisitos dos seus aplicativos. Você precisará determinar:

- Quais aplicativos exigem uma transformação ou rearchitecting.

- Quais aplicativos precisam ser modernizado apenas parcialmente.

- Quais aplicativos podem usar a “migração lift-and-shift” diretamente para a nuvem.

## <a name="about-this-guide"></a>Sobre este guia

Este guia se concentra principalmente nos modernização inicial da web do Microsoft .NET Framework existente ou aplicativos orientados a serviços, que significa que a ação de movimentação de uma carga de trabalho para um ambiente mais recente ou mais moderno sem alterar significativamente o código do aplicativo e a arquitetura básica. 

Este guia também destaca os benefícios de mover seus aplicativos para a nuvem e parcialmente modernizar aplicativos usando um conjunto específico de novas tecnologias e abordagens, como contêineres do Windows e plataformas de computação relacionadas no Azure com suporte a contêineres do Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Caminho para a nuvem para aplicativos .NET existentes

As organizações normalmente optam por mover para a nuvem devido à agilidade e à velocidade oferecida aos seus aplicativos. Você pode configurar milhares de servidores (VMs) na nuvem em questão de minutos, em comparação com as semanas de configuração de servidores locais normais.

Não há uma estratégia única e padronizada para migrar aplicativos para a nuvem. A estratégia de migração certa para você depende das necessidades e prioridades da sua organização, bem como o tipo de aplicativos que você está migrando. Nem todos os aplicativos valem o investimento de mudar para um modelo de [PaaS](https://azure.microsoft.com/overview/what-is-paas/) (plataforma como serviço) ou de desenvolver um modelo de aplicativo [nativo de nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Em muitos casos, você pode adotar uma abordagem em fases ou incremental para investir na movimentação de seus ativos para a nuvem, dependendo das suas necessidades de negócios.

Para aplicativos modernos com o valor para a organização e agilidade melhor a longo prazo, você pode se beneficiar de investir em *nuvem nativo* arquiteturas de aplicativo. No entanto, para aplicativos existentes ou herdados ativos, a chave é gastar mínimo de tempo e dinheiro (nenhuma alteração de código ou rearchitecting) ao movê-los para a nuvem, a perceber os benefícios significativos.

A Figura 1-1 mostra os caminhos possíveis que podem ser escolhidos ao mover os aplicativos .NET existente para a nuvem em fases incrementais.

 ![Caminhos de modernização para aplicativos e serviços .NET existentes](./media/image1-1.png)

> **Figura 1-1**. Caminhos de modernização para aplicativos e serviços .NET existentes

Cada abordagem de migração traz diferentes vantagens e motivos para usá-la. Você pode escolher uma abordagem única ao migrar aplicativos para a nuvem ou escolher certos componentes de várias abordagens. Aplicativos individuais não estão limitados a uma única abordagem ou estado de maturidade. Por exemplo, uma abordagem híbrida comum teria determinados componentes locais e outros componentes na nuvem.

A definição e uma breve explicação para cada nível de maturidade do aplicativo são os seguintes:

**Nível 1: Infraestrutura de nuvem pronto** aplicativos: essa abordagem de migração, você simplesmente migrar ou novo host seus aplicativos no local atual para uma infraestrutura como serviço ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) plataforma. Os aplicativos têm quase a mesma composição de antes, mas agora você os implanta em VMs na nuvem.
Esse tipo simple de migração é conhecido no setor como "Comparação de precisão & Shift".

**Nível 2: Otimização de nuvem** aplicativos: nesse nível e ainda sem rearchitecting ou alteração significativa de código, você pode obter benefícios adicionais de execução do seu aplicativo na nuvem com tecnologias modernas como contêineres e adicionais serviços gerenciados de nuvem. Melhore a agilidade dos seus aplicativos para distribuição mais rápida refinando seus processos de DevOps (operações de desenvolvimento) corporativas. Para fazer isso por meio de tecnologias como contêineres do Windows, que é baseado no mecanismo do Docker. Contêineres de remover a fricção que é causada pelas dependências de aplicativo ao implantar em várias fases. Nesse modelo de vencimento, você pode implantar os contêineres no IaaS ou PaaS durante o uso adicional serviços gerenciados de nuvem relacionados a bancos de dados, armazenar em cache como um serviço, o monitoramento e a implantação de integração contínua/contínua pipelines CI/CD ().

O terceiro nível de maturidade é a meta final na nuvem, mas é opcional para muitos aplicativos e não é o foco principal deste guia:

**Nível 3: Nuvem nativo** aplicativos: esse método de migração normalmente é orientado por necessidade comercial e destinos modernizar seus aplicativos de missão crítica. Nesse nível, você pode usar os serviços de PaaS para mover seus aplicativos para plataformas de computação de PaaS. Implemente aplicativos [nativos da nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) e arquitetura de microsserviços para desenvolver aplicativos com agilidade de longo prazo e dimensionar para novos limites. Esse tipo de modernização normalmente requer arquitetura específica para a nuvem. Geralmente é necessário escrever novo código, especialmente ao mover aplicativos nativos de nuvem e modelos baseados em microsserviços. Essa abordagem pode ajudar a obter os benefícios que são difíceis de obter no seu ambiente de aplicativo local e monolítico.

A Tabela 1-1 descreve as principais vantagens e motivos para escolher cada abordagem de migração ou modernização.

| **Pronto para infraestrutura de nuvem** <br /> *Lift-and-shift* | **Otimização de nuvem** <br /> *Modernizar* | **Nuvem nativo** <br /> *Modernizar, refaça a arquitetura e regravar* |
|---|---|---|
| **Destino de computação do aplicativo** |
| Aplicativos implantados em VMs no Azure | Monolítico ou aplicativos de N camadas implantados para o serviço de aplicativo do Azure, a instância de contêiner do Azure (ACI), máquinas virtuais com contêineres, Azure Service Fabric ou AKS (serviço de Kubernetes do Azure) | Microservices em contêineres no Azure Kubernetes serviço (AKS), serviço de malha e/ou microservices sem servidor com base em funções do Azure. |
| **Destino de dados** |
| SQL ou qualquer banco de dados relacional em uma VM | Instância de gerenciados do banco de dados de SQL do Azure ou outro banco de dados gerenciado na nuvem. | Bancos de dados de granularidade multas por microsserviço, com base no banco de dados do SQL Azure, o banco de dados do Azure Cosmos ou outro banco de dados gerenciado na nuvem |
| **Vantagens**|
| <li>Nenhum código rearchitecting, nenhuma <li> Mínimo de esforço para migração rápida <li> Mínimo denominador comum com suporte no Azure <li> Garantias básicas de disponibilidade <li> Depois de mudar para a nuvem, é mais fácil modernizar ainda mais | <li> Nenhum rearchitecting <li> Alterações de código/configuração mínima <li> Melhoria na implantação e agilidade de DevOps para liberação devido a contêineres <li> Aumento da densidade e redução dos custos de implantação <li> Portabilidade de aplicativos e dependências <li> Flexibilidade de destinos de host: PaaS abordagens ou IaaS | <li> Arquiteto novo código é necessária, mas para a nuvem, você obter os melhores benefícios da nuvem <li> Abordagens de microsserviços nativos de nuvem <li> Aplicativos de missão crítica modernos, nuvem resilientes hyper escalonável <li> Serviços totalmente gerenciados <li> Otimizado para escala <li> Otimizado para agilidade autônoma por subsistema <li> Baseado em implantação e DevOps |
| **Desafios** |
| <li> Menor valor de nuvem, diferente da mudança no custo de operação ou o fechamento de datacenters <li> Pouco gerenciado: nenhum sistema operacional ou middleware a aplicação de patch; pode usar soluções de infraestrutura, como Terraform, Spinnaker, | <li> Containerizing é uma etapa adicional na curva de aprendizado para desenvolvedores e as operações de TI <li> Pipelines de CI/CD e DevOps é geralmente '' para essa abordagem. Se não estiver presente no momento da cultura da organização, pode ser um desafio adicional| <li> Requer reestruturação para aplicativos nativos de nuvem e arquiteturas de microsserviço e geralmente requer código significativo refatoração ou reescrevendo quando modernizar (aumento no tempo e orçamento) <li> Pipelines de CI/CD e DevOps é geralmente '' para essa abordagem. Se não estiver presente no momento da cultura da organização, pode ser um desafio adicional|
> **Tabela 1-1.** Benefícios e desafios de caminhos de modernização para serviços e aplicativos .NET existentes

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Principais tecnologias e arquiteturas por nível de maturidade

Aplicativos do .NET Framework inicialmente começavam com o .NET Framework versão 1.0, que foi lançado no final de 2001. Assim, as empresas são movidas para versões mais recentes (como 2.0, 3.5 e .NET 4.x). A maioria dos aplicativos executados no Windows Server e o servidor de informações da Internet (IIS) e usado um banco de dados relacional, como o SQL Server, Oracle, MySQL ou quaisquer outros RDBMS.

A maioria dos aplicativos .NET existentes hoje em dia se baseia no .NET Framework 4.x ou até mesmo no .NET Framework 3.5 e usa estruturas da Web como o ASP.NET MVC, Web Forms do ASP.NET, API Web ASP.NET, WCF (Windows Communication Foundation), ASP.NET SignalR e Páginas da Web ASP.NET. Esses tecnologias estabelecidas do .NET Framework dependem do Windows. É importante considerar essa dependência se você estiver migrando simplesmente migrando aplicativos herdados e deseja realizar o mínimo de alterações na sua infraestrutura de aplicativo.

A Figura 1-2 mostra as principais tecnologias e estilos de arquitetura usados em cada um dos três níveis de maturidade de nuvem:

![Principais tecnologias para cada nível de maturidade para modernizar aplicativos Web .NET existentes](./media/image1-2.png)

> **Figura 1-2.** Principais tecnologias para cada nível de maturidade para modernizar aplicativos Web .NET existentes

A Figura 1-2 realça os cenários mais comuns, mas muitas variações híbridas e mistas são possíveis quando se trata de arquitetura. Por exemplo, os modelos de maturidade se aplicam não apenas a arquiteturas monolíticas em aplicativos Web existentes, mas também a arquiteturas com orientação de serviço, de N camadas e outras variações de estilo de arquiteturas. O maior foco ou percentual no tipo de uma ou outra arquitetura e as tecnologias relacionadas determina o nível de maturidade geral de seus aplicativos.

Cada nível de maturidade no processo de modernização está associado às seguintes tecnologias e abordagens principais:

- **Pronto para infraestrutura de nuvem** (novo host ou basic Levante & shift): como uma primeira etapa, muitas organizações desejam apenas executar rapidamente uma estratégia de migração de nuvem. Nesse caso, aplicativos são hospedado novamente. A maioria da nova hospedagem pode ser automatizada usando as [Migrações para Azure](https://aka.ms/azuremigrate), um serviço que fornece as diretrizes, os insights e os mecanismos necessários para ajudar você a migrar para o Azure com base em ferramentas de nuvem como o [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) e o [Serviço de Migração do Banco de Dados do Azure](https://azure.microsoft.com/campaigns/database-migration/). Você também pode definir a nova hospedagem manualmente, para que seja possível conhecer os detalhes da infraestrutura sobre seus ativos ao mover aplicativos herdados para a nuvem. Por exemplo, você pode mover seus aplicativos para VMs no Azure com pouca modificação provavelmente com apenas as alterações de configuração menor. Nesse caso, a rede é semelhante a um ambiente local, especialmente se você criar redes virtuais no Azure.

- **Otimização de nuvem** (serviços gerenciados e contêineres do Windows): esse modelo é focado em algumas otimizações de implantação importantes para obter alguns benefícios significativos da nuvem, sem alterar a arquitetura básica do aplicativo. A etapa fundamental aqui é adicionar suporte a [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) aos seus aplicativos .NET Framework existentes. Essa etapa (enormemente) não requer tocar no código, portanto, o esforço de comparar e deslocar geral é claro. Você pode usar ferramentas como [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ou o Visual Studio, com as suas ferramentas para [Docker](https://www.docker.com/). O Visual Studio escolhe automaticamente padrões inteligentes para aplicativos ASP.NET e imagens de Contêineres do Windows. Essas ferramentas oferecem um loop interno ágil e um caminho rápido para levar os contêineres para o Azure. A agilidade é melhorada ao implantar em vários ambientes. Em seguida, passar para a produção, você pode implantar os contêineres do Windows para [aplicativo Web do Azure para contêineres](https://azure.microsoft.com/en-us/services/app-service/containers/), [instâncias de contêiner do Azure (ACI) e VMs do Azure com o Windows Server 2016 e contêineres se você preferir uma abordagem de IaaS. Para aplicativos de multi-contêiner um pouco mais complexos, em orchestrators como [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) ou [Azure Kubernetes ACS (serviço AKS /)](https://azure.microsoft.com/en-us/services/container-service/). Durante essa modernização inicial, também é possível adicionar ativos da nuvem, como monitoramento com ferramentas como o [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); pipelines de CI/CD para o ciclo de vida dos aplicativo com o [Visual Studio Team Services](https://www.visualstudio.com/team-services/) e muitos outros serviços de recurso de dados que estão disponíveis no Azure. Por exemplo, é possível modificar um aplicativo Web monolítico que foi originalmente desenvolvido usando [Web Forms do ASP.NET](https://www.asp.net/web-forms) ou [ASP.NET MVC](https://www.asp.net/mvc) tradicionais, mas agora ele é implantado usando os Contêineres do Windows. Se você usar Contêineres do Windows, também deverá migrar os dados para um banco de dados em uma [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/), tudo sem alterar a arquitetura principal do seu aplicativo.

- **Nuvem nativo**: conforme apresentada, você deve considerar a arquitetura [nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplicativos quando você direcionar aplicativos grandes e complexos com várias equipes de desenvolvimento independentes trabalhando em microservices diferentes que podem ser desenvolvidos e implantados de forma independente. Além disso, devido à escalabilidade granularized e independente por microsserviço. Essas abordagens arquitetura enfrentam desafios muito importantes e complexidades, mas podem ser bastante simplificadas por meio da nuvem PaaS e orchestrators como [Azure Kubernetes ACS (serviço AKS /)](https://azure.microsoft.com/en-us/services/container-service/) (gerenciado Kubernetes), [serviço do Azure Malha, e [funções do Azure](https://azure.microsoft.com/services/functions/) uma abordagem sem servidor. Todas essas abordagens (como microservices e sem servidor) normalmente exigem que você criar para a nuvem e escrever novo código – código que foi adaptado para plataformas específicas do PaaS ou código que se alinha com arquiteturas específicas, como microservices.

A Figura 1-3 mostra as tecnologias internas que você pode usar para cada nível de maturidade:

![Tecnologias internas para cada nível de maturidade de modernização](./media/image1-3.png)

> **Figura 1-3.** Tecnologias internas para cada nível de maturidade de modernização

## <a name="lift-and-shift-scenario"></a>Comparar e deslocar cenário

Para usar migrações lift-and-shift, lembre-se que é possível usar muitas variações diferentes de migração lift-and-shift nos seus cenários de aplicativo. Se você é apenas o novo host do seu aplicativo, você pode ter um cenário semelhante ao mostrado na Figura 1-4, em que as VMs na nuvem são usadas apenas para seu aplicativo e para o servidor de banco de dados.

![Exemplo de um cenário de IaaS puro na nuvem](./media/image1-4.png)

> **Figura 1-4**. Exemplo de um cenário de IaaS puro na nuvem

## <a name="modernization-scenarios"></a>Cenários de modernização

Para cenários de modernização, você pode ter um aplicativo de otimização de nuvem simples que usa elementos apenas de que o nível de maturidade. Ou, talvez você tenha um aplicativo de estado intermediário com alguns elementos de pronta para a infraestrutura de nuvem e outros elementos de otimização de nuvem (um "escolher" ou um modelo misto), como na Figura 1-5.

![Cenário de exemplo de "Escolha", com o banco de dados no IaaS, DevOps e ativos em contêineres](./media/image1-5.png)

> **Figura 1-5.** Cenário de exemplo de "Escolha", com o banco de dados no IaaS, DevOps e ativos em contêineres

Em seguida, como o cenário ideal para muitos aplicativos do .NET Framework a migração, você pode migrar para um aplicativo com otimização de nuvem para obter benefícios significativos de pouco de trabalho. Essa abordagem também define você para nuvem nativo como uma possível evolução futura. A Figura 1-6 mostra um exemplo.

![Cenário de otimização de nuvem aplicativos de exemplo, com contêineres do Windows e de serviços gerenciados](./media/image1-6.png)

> **Figura 1-6.** Cenário de otimização de nuvem aplicativos de exemplo, com contêineres do Windows e de serviços gerenciados

Vai ainda mais, você pode estender o aplicativo de otimização de nuvem existente adicionando alguns microservices para cenários específicos. Isso moverá você parcialmente para o nível de modelo de nuvem nativo, que não é o principal foco do guia presente.


## <a name="what-this-guide-does-not-cover"></a>O que este guia não cobre

Este guia abrange um subconjunto específico de cenários de exemplo, conforme mostrado na Figura 1-7. Este guia se concentra somente em cenários de comparar e deslocar e por fim, no modelo de otimização de nuvem. No modelo de otimização de nuvem, um aplicativo do .NET Framework é modernizado usando contêineres do Windows, além de componentes adicionais como o monitoramento e pipelines CI/CD. Cada componente é fundamental para implantar aplicativos na nuvem de maneira mais rápida e ágil.

![Nuvem nativo não é abordado neste guia](./media/image1-7.png)

> **Figura 1-7.** Nuvem nativo não é abordado neste guia

O foco deste guia é específico. Ele mostra o caminho que você pode tomar para obter uma comparação de precisão e a mudança de seus aplicativos existentes do .NET, sem rearchitecting e sem alterações de código. Por fim, ele mostra como tornar seu aplicativo otimizada para a nuvem.

Este guia não mostra como criar aplicativos de nuvem nativo, por exemplo, como desenvolver uma arquitetura de microservices. Refaça a arquitetura de seus aplicativos ou criar novos aplicativos que são baseados em microservices, consulte o livro eletrônico [Microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Recursos adicionais

- **Em contêineres de Docker o ciclo de vida do aplicativo com o Microsoft platform e ferramentas** (que pode ser baixado e-book): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET Microservices: Arquitetura para aplicativos .NET em contêineres** (que pode ser baixado e-book): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **Arquitetura de aplicativos web modernos com ASP.NET Core e o Azure** (que pode ser baixado e-book): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

Este guia foi elaborado para desenvolvedores e arquitetos de solução que deseja modernizar aplicativos ASP.NET web ou serviços WCF com base no .NET Framework, para aumento da agilidade no envio e liberação de aplicativos.

Você também pode achar este guia útil se for um tomador de decisões técnicas, como um arquiteto corporativo ou um líder de desenvolvimento/diretor que deseja ter apenas uma visão geral dos benefícios que podem ser alcançados usando Contêineres do Windows e implantando na nuvem ao usar o Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Como usar este guia

Este guia aborda “o porquê”, isto é, por que modernizar seus aplicativos existentes e os benefícios específicos obtidos ao usar os Contêineres do Windows ao mover seus aplicativos para a nuvem. O conteúdo dos primeiros capítulos do guia destina-se a arquitetos e tomadores de decisões técnicas que desejam obter uma visão geral, mas que não precisam se concentrar nos detalhes técnicos passo a passo nem na implementação.

O último capítulo deste guia apresenta vários tutoriais passo a passo que se concentram em cenários de implantação específicos. Este guia oferece versões de instruções passo a passo, menores para resumir os cenários e realçar os seus benefícios. Os tutoriais passo a passo completos detalham a configuração e a implementação e são publicados como um conjunto de [postagens de wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) no mesmo [repositório do GitHub](https://github.com/dotnet-architecture/eShopModernizing) público em que residem os aplicativos de exemplo relacionados (discutido na próxima seção). O último capítulo e os tutoriais da wiki passo a passo no GitHub serão mais interessantes para desenvolvedores e arquitetos que desejam se concentrar nos detalhes de implementação.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Aplicativos de exemplo para modernização de aplicativos herdados: eShopModernizing

O repositório [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) no GitHub oferece dois aplicativos de exemplo que simulam aplicativos Web monolíticos herdados. Um aplicativo web é desenvolvido usando o ASP.NET MVC; o segundo aplicativo web é desenvolvido usando o Web Forms do ASP.NET e o aplicativo de terceiro é um aplicativo de N camadas com um aplicativo de área de trabalho de cliente do WinForms consumir um serviço WCF back-end. Todos esses aplicativos são baseados no .NET Framework tradicional. Esses aplicativos de exemplo não usam o .NET Core ou o ASP.NET Core, pois eles se destinam a aplicativos do .NET Framework existentes/herdados que serão modernizados.

Esses aplicativos de exemplo tem uma versão de segundo, com o código e modernizado, e quais são bastante simples. A diferença mais importante entre as versões do aplicativo é que as segundas versões usam Contêineres do Windows como a opção de implantação. Também há algumas adições para as segundas versões, como Blobs de Armazenamento do Microsoft Azure para gerenciar imagens, Azure Active Directory para gerenciar a segurança e o Azure Application Insights para monitorar e auditar os aplicativos.

## <a name="send-your-feedback"></a>Envie seus comentários

Este guia foi elaborado para ajudá-lo a entender as opções para melhorar e modernizar os aplicativos web .NET existentes. O guia e os aplicativos de exemplo relacionados estão em evolução. Seus comentários são bem-vindo! Se você tiver comentários sobre como este guia poderia ser mais útil, envie-os para [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Avançar](lift-and-shift-existing-apps-azure-iaas.md)
