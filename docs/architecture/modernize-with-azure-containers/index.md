---
title: Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure (2ª edição)
description: Saiba como migrar e deslocar e modernizar os aplicativos existentes para a nuvem do Azure e contêineres com este livro eletrônico.
ms.date: 04/28/2018
ms.openlocfilehash: ab2b58441af7aed6a8cd868751339b555a345565
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "70222841"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizar aplicativos .NET existentes com contêineres de nuvem e Windows do Azure (2ª edição)

![Imagem de capa do guia modernizar aplicativos .NET.](./media/index/web-application-guide-cover-image.png)

PUBLICADO POR  
Microsoft Press e Microsoft DevDiv  
Divisões da Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018, Microsoft Corporation  

Todos os direitos reservados. Nenhuma parte do conteúdo deste guia pode ser reproduzida de nenhuma forma, nem por nenhum meio, sem a permissão por escrito do distribuidor.

Este livro está disponível gratuitamente na forma de um livro eletrônico (e-book) disponível por meio de vários canais da Microsoft, como <https://dot.net/architecture>o.

Se você tiver dúvidas relacionadas a esse livro, envie-as por email para [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Este livro é fornecido “no estado em que se encontra” e expressa os pontos de vista e as opiniões do autor. As exibições, opiniões e informações expressas neste livro, incluindo URLs e outras referências de sites da Internet, podem ser alteradas sem aviso prévio.

Alguns exemplos aqui representados são fornecidos apenas para ilustração e são fictícios. Nenhuma associação ou conexão real é intencional ou deve ser deduzida.

A Microsoft e as marcas listadas em <https://www.microsoft.com> na página da Web "Marcas" são marcas comerciais do grupo de empresas Microsoft. Todas as outras marcas são propriedade de seus respectivos proprietários.

Autor:
> **Cesar de la Torre**, Sr. pm, equipe de produtos .net, Microsoft Corp.

Participantes e revisores:
> **Scott Hunter**, PM Diretor de Parceiro, equipe do .NET, Microsoft  
> **Paul Yuknewicz**, gerente de PM Principal, equipe das Ferramentas do Visual Studio, Microsoft  
> **Lisa Guthrie**, Sr. pm, equipe de ferramentas do Visual Studio, Microsoft  
> **Ankit Asthana**, Gerente de PM Principal, equipe do .NET, Microsoft  
> **Unai Zorrilla**, líder de desenvolvimento, conceitos simples  
> **Javier Valero**, Diretor Executivo de Operações no Grupo Solutio  

## <a name="introduction"></a>Introdução

Ao decidir modernizar seus aplicativos Web ou serviços e movê-los para a nuvem, você não precisa necessariamente rearquitetar totalmente seus aplicativos. A rearquiteturação de um aplicativo usando uma abordagem avançada como os microserviços nem sempre é uma opção por causa de restrições de custo e de tempo. Dependendo do tipo de aplicativo, a rearquitetura de um aplicativo também pode não ser necessária. Para otimizar o custo-benefício da estratégia de migração de nuvem da sua organização, é importante considerar as necessidades do seu negócio e os requisitos dos seus aplicativos. Você precisará determinar:

- Quais aplicativos exigem uma transformação ou rearquiteturaing.

- Quais aplicativos precisam ser modernizado apenas parcialmente.

- Quais aplicativos podem usar a “migração lift-and-shift” diretamente para a nuvem.

## <a name="about-this-guide"></a>Sobre este guia

Este guia se concentra principalmente na modernização inicial de aplicativos Web ou orientados a serviços existentes da estrutura de Microsoft .NET, o que significa a ação de mover uma carga de trabalho para um ambiente mais novo ou moderno sem alterar significativamente o código do aplicativo e a arquitetura básica. 

Este guia também destaca os benefícios de mover seus aplicativos para a nuvem e, parcialmente, modernizar aplicativos usando um conjunto específico de novas tecnologias e abordagens, como contêineres do Windows e plataformas de computação relacionadas no Azure com suporte a contêineres do Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Caminho para a nuvem para aplicativos .NET existentes

As organizações normalmente optam por mover para a nuvem devido à agilidade e à velocidade oferecida aos seus aplicativos. Você pode configurar milhares de servidores (VMs) na nuvem em questão de minutos, em comparação com as semanas de configuração de servidores locais normais.

Não há uma estratégia única e padronizada para migrar aplicativos para a nuvem. A estratégia de migração certa para você depende das necessidades e prioridades da sua organização, bem como o tipo de aplicativos que você está migrando. Nem todos os aplicativos valem o investimento de mudar para um modelo de [PaaS](https://azure.microsoft.com/overview/what-is-paas/) (plataforma como serviço) ou de desenvolver um modelo de aplicativo [nativo de nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Em muitos casos, você pode adotar uma abordagem em fases ou incremental para investir na movimentação de seus ativos para a nuvem, dependendo das suas necessidades de negócios.

Para aplicativos modernos com a melhor agilidade e valor de longo prazo para a organização, você pode se beneficiar do investimento em arquiteturas de aplicativos *nativos de nuvem* . No entanto, para aplicativos que são ativos existentes ou herdados, a chave é gastar tempo mínimo e dinheiro (sem rearquitetura ou alterações de código) ao movê-los para a nuvem, a fim de obter benefícios significativos.

A Figura 1-1 mostra os caminhos possíveis que podem ser escolhidos ao mover os aplicativos .NET existente para a nuvem em fases incrementais.

 ![Caminhos de modernização para aplicativos e serviços .NET existentes](./media/image1-1.png)

> **Figura 1-1**. Caminhos de modernização para aplicativos e serviços .NET existentes

Cada abordagem de migração traz diferentes vantagens e motivos para usá-la. Você pode escolher uma abordagem única ao migrar aplicativos para a nuvem ou escolher certos componentes de várias abordagens. Aplicativos individuais não estão limitados a uma única abordagem ou estado de maturidade. Por exemplo, uma abordagem híbrida comum teria determinados componentes locais e outros componentes na nuvem.

A definição e a explicação breve para cada nível de maturidade do aplicativo são as seguintes:

**Nível 1: Aplicativos prontos** para infraestrutura de nuvem: Nessa abordagem de migração, você simplesmente migra ou rehospeda seus aplicativos locais atuais para uma plataforma[IaaS](https://azure.microsoft.com/overview/what-is-iaas/)(infraestrutura como serviço). Os aplicativos têm quase a mesma composição de antes, mas agora você os implanta em VMs na nuvem.
Esse tipo simples de migração é normalmente conhecido no setor como "aumentar & Shift".

**Nível 2: Aplicativos otimizados** para nuvem: Nesse nível e ainda sem rearquitetar ou alterar código significativo, você pode obter benefícios adicionais na execução de seu aplicativo na nuvem com tecnologias modernas, como contêineres e serviços adicionais gerenciados por nuvem. Melhore a agilidade dos seus aplicativos para distribuição mais rápida refinando seus processos de DevOps (operações de desenvolvimento) corporativas. Você consegue fazer isso usando tecnologias como contêineres do Windows, que se baseiam no mecanismo do Docker. Os contêineres removem o conflito causado pelas dependências do aplicativo quando você implanta em vários estágios. Nesse modelo de maturidade, você pode implantar contêineres em IaaS ou PaaS enquanto usa serviços adicionais gerenciados na nuvem relacionados a bancos de dados, cache como serviço, monitoramento e pipelines de CI/CD (implantação contínua/integração contínua).

O terceiro nível de maturidade é a meta final na nuvem, mas é opcional para muitos aplicativos e não é o foco principal deste guia:

**Nível 3: Aplicativos nativos** de nuvem: Essa abordagem de migração normalmente é orientada pela necessidade de negócios e tem como alvo a modernização de seus aplicativos de missão crítica. Nesse nível, você pode usar os serviços de PaaS para mover seus aplicativos para plataformas de computação de PaaS. Implemente aplicativos [nativos da nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) e arquitetura de microsserviços para desenvolver aplicativos com agilidade de longo prazo e dimensionar para novos limites. Esse tipo de modernização normalmente requer arquitetura específica para a nuvem. Geralmente é necessário escrever novo código, especialmente ao mover aplicativos nativos de nuvem e modelos baseados em microsserviços. Essa abordagem pode ajudar a obter os benefícios que são difíceis de obter no seu ambiente de aplicativo local e monolítico.

A Tabela 1-1 descreve as principais vantagens e motivos para escolher cada abordagem de migração ou modernização.

| **Pronto para infraestrutura de nuvem** <br /> *Lift-and-shift* | **Otimizado para a nuvem** <br /> *Modernizar* | **Cloud-Native** <br /> *Modernizar, rearquitetar e reescrever* |
|---|---|---|
| **Destino de computação do aplicativo** |
| Aplicativos implantados em VMs no Azure | Aplicativos monolíticos ou de N camadas implantados em Azure App serviço, instância de contêiner do Azure (ACI), VMs com contêineres ou AKS (serviço kubernetes do Azure) | Microservices em contêineres no AKS (serviço de kubernetes do Azure) e/ou em microserviços sem servidor com base em Azure Functions. |
| **Destino de dados** |
| SQL ou qualquer banco de dados relacional em uma VM | Instância Gerenciada do Banco de Dados SQL do Azure ou outro banco de dados gerenciado na nuvem. | Bancos de dados de granulação multas por microserviço, com base no banco de dados SQL do Azure, Azure Cosmos DB ou outro banco de dados gerenciado na nuvem |
| **Vantagens**|
| <li>Sem rearquitetura, nenhum código novo <li> Mínimo de esforço para migração rápida <li> Mínimo denominador comum com suporte no Azure <li> Garantias básicas de disponibilidade <li> Depois de mudar para a nuvem, é mais fácil modernizar ainda mais | <li> Sem rearquitetura <li> Alterações mínimas de código/configuração <li> Melhoria na implantação e agilidade de DevOps para liberação devido a contêineres <li> Aumento da densidade e redução dos custos de implantação <li> Portabilidade de aplicativos e dependências <li> Flexibilidade de destinos de host: Abordagens de PaaS ou IaaS | <li> Arquiteto para a nuvem, você obtém os melhores benefícios da nuvem, mas o novo código é necessário <li> Abordagens de microsserviços nativos de nuvem <li> Aplicativos de missão crítica modernos, hiperescalas resilientes de nuvem <li> Serviços totalmente gerenciados <li> Otimizado para escala <li> Otimizado para agilidade autônoma por subsistema <li> Baseado em implantação e DevOps |
| **Desafios** |
| <li> Menor valor de nuvem, diferente da mudança no custo de operação ou o fechamento de datacenters <li> O pouco é gerenciado: Nenhuma aplicação de patch no sistema operacional ou middleware; pode usar soluções de infraestrutura, como Terraform, Spinnaker ou Puppet | <li> O contêiner é uma etapa adicional na curva de aprendizado para desenvolvedores e operações de ti <li> Os pipelines de DevOps e CI/CD geralmente são ' a ' a ' a para essa abordagem. Se não estiver presente atualmente na cultura da organização, pode ser um desafio adicional| <li> Requer a rearquitetura para aplicativos nativos de nuvem e arquiteturas de microserviço e geralmente requer refatoração significativa de código ou regravação ao modernizar (aumento de tempo e orçamento)|
> **Tabela 1-1.** Benefícios e desafios de caminhos de modernização para serviços e aplicativos .NET existentes

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Principais tecnologias e arquiteturas por nível de maturidade

Aplicativos do .NET Framework inicialmente começavam com o .NET Framework versão 1.0, que foi lançado no final de 2001. Assim, as empresas são movidas para versões mais recentes (como 2.0, 3.5 e .NET 4.x). A maioria desses aplicativos foi executada no Windows Server e no IIS (servidor de informações da Internet) e usava um banco de dados relacional, como SQL Server, Oracle, MySQL ou qualquer outro RDBMS.

A maioria dos aplicativos .NET existentes hoje em dia se baseia no .NET Framework 4.x ou até mesmo no .NET Framework 3.5 e usa estruturas da Web como o ASP.NET MVC, Web Forms do ASP.NET, ASP.NET Web API, WCF (Windows Communication Foundation), ASP.NET SignalR e Páginas da Web ASP.NET. Esses tecnologias estabelecidas do .NET Framework dependem do Windows. É importante considerar essa dependência se você estiver migrando simplesmente migrando aplicativos herdados e deseja realizar o mínimo de alterações na sua infraestrutura de aplicativo.

A Figura 1-2 mostra as principais tecnologias e estilos de arquitetura usados em cada um dos três níveis de maturidade de nuvem:

![Principais tecnologias para cada nível de maturidade para modernizar aplicativos Web .NET existentes](./media/image1-2.png)

> **Figura 1-2.** Principais tecnologias para cada nível de maturidade para modernizar aplicativos Web .NET existentes

A Figura 1-2 realça os cenários mais comuns, mas muitas variações híbridas e mistas são possíveis quando se trata de arquitetura. Por exemplo, os modelos de maturidade se aplicam não apenas a arquiteturas monolíticas em aplicativos Web existentes, mas também a arquiteturas com orientação de serviço, de N camadas e outras variações de estilo de arquiteturas. O foco maior ou a porcentagem em um ou outro tipo de arquitetura e tecnologias relacionadas determinam o nível de maturidade geral de seus aplicativos.

Cada nível de maturidade no processo de modernização está associado às seguintes tecnologias e abordagens principais:

- **Infraestrutura de nuvem-pronto** (Rehost ou comparação básica & Shift): Como uma primeira etapa, muitas organizações desejam apenas executar rapidamente uma estratégia de migração de nuvem. Nesse caso, os aplicativos são rehospedados. A maioria da nova hospedagem pode ser automatizada usando as [Migrações para Azure](https://aka.ms/azuremigrate), um serviço que fornece as diretrizes, os insights e os mecanismos necessários para ajudar você a migrar para o Azure com base em ferramentas de nuvem como o [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) e o [Serviço de Migração do Banco de Dados do Azure](https://azure.microsoft.com/campaigns/database-migration/). Você também pode definir a nova hospedagem manualmente, para que seja possível conhecer os detalhes da infraestrutura sobre seus ativos ao mover aplicativos herdados para a nuvem. Por exemplo, você pode mover seus aplicativos para VMs no Azure com pouca modificação-provavelmente com apenas pequenas alterações de configuração. Nesse caso, a rede é semelhante a um ambiente local, especialmente se você criar redes virtuais no Azure.

- **Otimizado para a nuvem** (Serviços gerenciados e contêineres do Windows): Esse modelo trata de fazer algumas otimizações de implantação importantes para obter alguns benefícios significativos da nuvem, sem alterar a arquitetura principal do aplicativo. A etapa fundamental aqui é adicionar suporte a [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) aos seus aplicativos .NET Framework existentes. Essa etapa importante (a contêinerização) não exige o toque do código, portanto, o esforço geral de comparação de precisão e deslocamento é claro. Você pode usar ferramentas como [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ou o Visual Studio, com as suas ferramentas para [Docker](https://www.docker.com/). O Visual Studio escolhe automaticamente padrões inteligentes para aplicativos ASP.NET e imagens de Contêineres do Windows. Essas ferramentas oferecem um loop interno ágil e um caminho rápido para levar os contêineres para o Azure. A agilidade é melhorada ao implantar em vários ambientes. Em seguida, passando para a produção, você pode implantar seus contêineres do Windows no [azure aplicativo Web para contêineres](https://azure.microsoft.com/services/app-service/containers/), [ACI (instâncias de contêiner do Azure)](https://azure.microsoft.com/services/container-instances/)e VMs do Azure com o Windows Server 2016 e contêineres se preferir uma abordagem IaaS. Para aplicativos de vários contêineres mais complexos, considere usar orquestradores como o [serviço de kubernetes do Azure (AKs/ACS)](https://azure.microsoft.com/services/container-service/). 

Durante essa modernização inicial, você também pode adicionar ativos da nuvem, como o monitoramento com ferramentas como o [aplicativo Azure](https://docs.microsoft.com/azure/application-insights/app-insights-overview)insights; Pipelines de CI/CD para seus ciclos de vida do aplicativo com [Azure DevOps Services](https://azure.microsoft.com/services/devops/); e muitos outros serviços de recursos de dados que estão disponíveis no Azure. Por exemplo, é possível modificar um aplicativo Web monolítico que foi originalmente desenvolvido usando [Web Forms do ASP.NET](https://www.asp.net/web-forms) ou [ASP.NET MVC](https://www.asp.net/mvc) tradicionais, mas agora ele é implantado usando os Contêineres do Windows. Se você usar Contêineres do Windows, também deverá migrar os dados para um banco de dados em uma [Instância Gerenciada do Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/), tudo sem alterar a arquitetura principal do seu aplicativo.

- **Nativo de nuvem**: Conforme introduzido, você deve pensar na arquitetura [de aplicativos nativos de nuvem](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) quando estiver visando aplicativos grandes e complexos com várias equipes de desenvolvimento independentes trabalhando em diferentes microservices que podem ser desenvolvidos e implantados forma autônoma. Além disso, devido à escalabilidade granular e independente por microatendimento. Essas abordagens de arquitetura enfrentam desafios e complexidades muito importantes, mas podem ser bastante simplificadas com o uso de PaaS e orquestradores de nuvem como o [serviço de kubernetes do Azure (AKs/ACS)](https://azure.microsoft.com/services/container-service/) (Managed kubernetes) e [Azure Functions](https://azure.microsoft.com/services/functions/) para um abordagem sem servidor. Todas essas abordagens (como os microserviços e sem servidor) normalmente exigem que você projete para a nuvem e escreva um novo código — código adaptado a plataformas PaaS específicas ou código que se alinhe a arquiteturas específicas, como os microserviços.

A Figura 1-3 mostra as tecnologias internas que você pode usar para cada nível de maturidade:

![Tecnologias internas para cada nível de maturidade de modernização](./media/image1-3.png)

> **Figura 1-3.** Tecnologias internas para cada nível de maturidade de modernização

## <a name="lift-and-shift-scenario"></a>Cenário de comparação de precisão e deslocamento

Para usar migrações lift-and-shift, lembre-se que é possível usar muitas variações diferentes de migração lift-and-shift nos seus cenários de aplicativo. Se você é apenas o novo host do seu aplicativo, você pode ter um cenário semelhante ao mostrado na Figura 1-4, em que as VMs na nuvem são usadas apenas para seu aplicativo e para o servidor de banco de dados.

![Exemplo de um cenário de IaaS puro na nuvem](./media/image1-4.png)

> **Figura 1-4**. Exemplo de um cenário de IaaS puro na nuvem

## <a name="modernization-scenarios"></a>Cenários de modernização

Para cenários de modernização, você pode ter um aplicativo puro otimizado para nuvem que usa elementos somente desse nível de maturidade. Ou então, você pode ter um aplicativo de estado intermediário com alguns elementos da infraestrutura de nuvem – prontos e outros elementos, de um modelo otimizado para a nuvem (um "escolha e escolha" ou de modelos mistos), como na Figura 1-5.

![Cenário de exemplo de "Escolha", com o banco de dados no IaaS, DevOps e ativos em contêineres](./media/image1-5.png)

> **Figura 1-5.** Cenário de exemplo de "Escolha", com o banco de dados no IaaS, DevOps e ativos em contêineres

Em seguida, como o cenário ideal para muitos aplicativos .NET Framework existentes migrar, você poderia migrar para um aplicativo otimizado para a nuvem, para obter benefícios significativos de pouco trabalho. Essa abordagem também define a nuvem nativa como uma possível evolução futura. A Figura 1-6 mostra um exemplo.

![Cenário de aplicativos otimizados para nuvem de exemplo, com contêineres do Windows e serviços gerenciados](./media/image1-6.png)

> **Figura 1-6.** Cenário de aplicativos otimizados para nuvem de exemplo, com contêineres do Windows e serviços gerenciados

Indo ainda mais, você pode estender seu aplicativo existente otimizado para a nuvem adicionando alguns microserviços para cenários específicos. Isso o moveria parcialmente para o nível de modelo nativo de nuvem, que não é o foco principal das diretrizes presentes.

## <a name="what-this-guide-does-not-cover"></a>O que este guia não cobre

Este guia abrange um subconjunto específico de cenários de exemplo, conforme mostrado na Figura 1-7. Este guia se concentra apenas em cenários de comparação de precisão e deslocamento e, por fim, no modelo otimizado para a nuvem. No modelo otimizado para a nuvem, um aplicativo .NET Framework é modernizado usando contêineres do Windows, além de componentes adicionais, como o monitoramento e pipelines de CI/CD. Cada componente é fundamental para implantar aplicativos na nuvem de maneira mais rápida e ágil.

![A nuvem nativa não é abordada neste guia](./media/image1-7.png)

> **Figura 1-7.** A nuvem nativa não é abordada neste guia

O foco deste guia é específico. Ele mostra o caminho que você pode tomar para obter um deslocamento e uma mudança dos seus aplicativos .NET existentes, sem rearquitetar e sem alterações de código. Por fim, ele mostra como tornar seu aplicativo otimizado para a nuvem.

Este guia não mostra como criar aplicativos nativos de nuvem, como a evolução de uma arquitetura de microserviços. Para rearquitetar seus aplicativos ou criar aplicativos novos que se baseiam em microserviços, consulte os microserviços .NET [do livro eletrônico: Arquitetura para aplicativos](https://aka.ms/microservicesebook).net em contêineres.

### <a name="additional-resources"></a>Recursos adicionais

- **Ciclo de vida do aplicativo Docker em contêineres com plataforma e ferramentas da Microsoft** (livro eletrônico baixável) \
  <https://aka.ms/dockerlifecycleebook>

- **Microsserviços do .NET: Arquitetura para aplicativos** .net em contêineres (e-book para download) \
  <https://aka.ms/microservicesebook>

- **Arquitetando aplicativos Web modernos com o ASP.NET Core e o Azure** (livro eletrônico baixável) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Quem deve usar este guia

Este guia foi escrito para desenvolvedores e arquitetos de soluções que desejam modernizar os aplicativos Web ASP.NET existentes ou serviços WCF baseados na .NET Framework, para melhorar a agilidade no envio e na liberação de aplicativos.

Você também pode achar este guia útil se for um tomador de decisões técnicas, como um arquiteto corporativo ou um líder de desenvolvimento/diretor que deseja ter apenas uma visão geral dos benefícios que podem ser alcançados usando Contêineres do Windows e implantando na nuvem ao usar o Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Como usar este guia

Este guia aborda “o porquê”, isto é, por que modernizar seus aplicativos existentes e os benefícios específicos obtidos ao usar os Contêineres do Windows ao mover seus aplicativos para a nuvem. O conteúdo dos primeiros capítulos do guia destina-se a arquitetos e tomadores de decisões técnicas que desejam obter uma visão geral, mas que não precisam se concentrar nos detalhes técnicos passo a passo nem na implementação.

O último capítulo deste guia apresenta vários tutoriais passo a passo que se concentram em cenários de implantação específicos. Este guia oferece versões mais curtas dos passo a passos para resumir os cenários e destacar seus benefícios. Os tutoriais passo a passo completos detalham a configuração e a implementação e são publicados como um conjunto de [postagens de wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki) no mesmo [repositório do GitHub](https://github.com/dotnet-architecture/eShopModernizing) público em que residem os aplicativos de exemplo relacionados (discutido na próxima seção). O último capítulo e os tutoriais da wiki passo a passo no GitHub serão mais interessantes para desenvolvedores e arquitetos que desejam se concentrar nos detalhes de implementação.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Aplicativos de exemplo para modernização de aplicativos herdados: eShopModernizing

O repositório [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) no GitHub oferece dois aplicativos de exemplo que simulam aplicativos Web monolíticos herdados. Um aplicativo Web é desenvolvido usando o ASP.NET MVC; o segundo aplicativo Web é desenvolvido usando ASP.NET Web Forms e o terceiro aplicativo é um aplicativo de N camadas com um aplicativo de área de trabalho do cliente WinForms consumindo um back-end do serviço WCF. Todos esses aplicativos são baseados no .NET Framework tradicional. Esses aplicativos de exemplo não usam o .NET Core ou o ASP.NET Core, pois eles se destinam a aplicativos do .NET Framework existentes/herdados que serão modernizados.

Esses aplicativos de exemplo têm uma segunda versão, com código modernizado e que são razoavelmente simples. A diferença mais importante entre as versões do aplicativo é que as segundas versões usam Contêineres do Windows como a opção de implantação. Também há algumas adições para as segundas versões, como Blobs de Armazenamento do Microsoft Azure para gerenciar imagens, Azure Active Directory para gerenciar a segurança e o Azure Application Insights para monitorar e auditar os aplicativos.

## <a name="send-your-feedback"></a>Envie seus comentários

Este guia foi escrito para ajudá-lo a entender suas opções para melhorar e modernizar os aplicativos Web .NET existentes. O guia e os aplicativos de exemplo relacionados estão em evolução. Seus comentários são bem-vindos! Se você tiver comentários sobre como este guia poderia ser mais útil, envie-os para [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
>[Avançar](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
