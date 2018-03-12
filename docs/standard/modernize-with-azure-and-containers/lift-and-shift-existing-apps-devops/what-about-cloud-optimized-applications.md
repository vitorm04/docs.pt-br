---
title: E aplicativos otimizada para a nuvem?
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | E aplicativos otimizada para a nuvem?"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 249da9ecbac90514647f4fdc926928ac7ad4648e
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="what-about-cloud-optimized-applications"></a>E aplicativos otimizada para a nuvem?

Embora a otimização de nuvem e [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplicativos não são o foco principal deste guia, é muito útil para compreender desse nível de maturidade modernização, para diferenciá-lo da nuvem DevOps pronto.

Figura 4-3 posiciona aplicativos otimizada para a nuvem nos níveis de maturidade modernização de aplicativo:

![Posicionamento de aplicativos com otimização de nuvem](./media/image3.png)

> **Figura 4-3.** Posicionamento de aplicativos com otimização de nuvem

O nível de maturidade modernização otimizada para a nuvem normalmente requer investimentos de desenvolvimento de novo. Mover para o nível de otimização de nuvem normalmente é orientada por empresas que precisam modernizar aplicativos tanto quanto possíveis reduzir os custos e aumentar a agilidade e competir vantagem. Essas metas são realizadas, maximizando o uso da nuvem PaaS. Isso significa que não apenas usando serviços de PaaS como plataforma como serviço de aplicativo do Azure de computação de armazenamento como um serviço (STaaS), mas também migrando seus próprios aplicativos e serviços para um PaaS, CaaS e DBaaS ou orchestrators.

Esse tipo de modernização normalmente requer refatoração ou escrever novo código que é otimizado para nuvem PaaS plataformas (como para o serviço de aplicativo do Azure). Ainda podem exigir arquitetura especificamente para o ambiente de nuvem, especialmente se você estiver movendo para modelos de aplicativo nativo de nuvem com base em microservices. Esta é uma chave diferenciando fator em comparação comparada DevOps pronta para a nuvem, que não exige que nenhum rearquitetura e nenhum novo código.

Em alguns casos mais avançados, você pode criar [nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplicativos baseados em arquiteturas de microservices, que podem evoluir com agilidade e dimensionar aos limites que seriam difíceis de uma arquitetura monolítica implantar um ambiente local.

Figura 4-4 mostra o tipo de aplicativos que você pode implantar quando você usa o modelo de otimização de nuvem. Você tem dois aplicativos web moderna opções básico e aplicativos de nuvem nativo.

> ![Tipos de aplicativo no nível de otimização de nuvem](./media/image4.png)
>
> **Figura 4-4.** Tipos de aplicativo no nível de otimização de nuvem

Você pode estender aplicativos web modernos básico e nativo de nuvem adicionando outros serviços, como inteligência artificial (AI), o aprendizado de máquina (ML) e IoT. Você pode usar qualquer um desses serviços para estender uma das abordagens possíveis otimizada para a nuvem.

A diferença fundamental em aplicativos no nível de otimização de nuvem é na arquitetura do aplicativo. [Nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplicativos são, por definição, os aplicativos que se baseiam no microservices. Aplicativos de nuvem nativo exigem arquiteturas especiais, tecnologias e plataformas, em comparação comparadas um aplicativo web monolítico ou tradicionais de aplicativos de N camadas.

Criar novos aplicativos que não usam microservices também faz sentido. Há muitos cenários de novos e modernos ainda no qual uma abordagem baseada em microservices pode exceder suas necessidades. Em alguns casos, você apenas deseja criar um aplicativo web monolítico mais simples, ou adicionar serviços de alta granularidade para um aplicativo de N camadas. Nesses casos, você ainda pode fazer uso total da nuvem de recursos de PaaS, como aquelas oferecidas pelo serviço de aplicativo do Azure. Você ainda pode reduzir o trabalho de manutenção para o limite.

Além disso, porque você desenvolver o novo código otimizada para a nuvem cenários (para um aplicativo completo ou parciais subsistemas), quando você cria o novo código, você deve usar as versões mais recentes do .NET ([.NET Core](../../../core/index.md) e [ASP.NET Core](/aspnet/core/), em particular). Isso é especialmente verdadeiro se você criar microservices e contêineres como .NET Core é uma estrutura lean e rápida. Você terá um espaço de memória pequenos e início rápido em contêineres e os aplicativos serão alto desempenho. Essa abordagem se ajusta perfeitamente com os requisitos de microservices e contêineres e obter os benefícios de uma plataforma cruzada do framework-sendo capazes de executar o mesmo aplicativo em Mac (Mac para ambientes de desenvolvimento), Windows Server e Linux.

## <a name="cloud-native-applications-with-cloud-optimized-applications"></a>Aplicativos de nuvem nativo com otimização de nuvem

[Nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) é um estado mais avançado ou mais maduro para aplicativos grandes e de missão crítica. Aplicativos de nuvem nativo geralmente requerem a arquitetura e design criado do zero, em vez de por modernizar aplicativos existentes. A principal diferença entre um aplicativo nativo de nuvem e um aplicativo web com otimização de nuvem mais simples implantado PaaS é a recomendação para usar microservices arquiteturas em uma abordagem de nuvem nativo. Otimização de nuvem aplicativos também podem ser aplicativos web monolítico ou aplicativos de N camadas implantados em uma nuvem PaaS serviço como o serviço de aplicativo do Azure.

O [aplicativo doze Factor](https://12factor.net/) (uma coleção de padrões que estão intimamente relacionados abordagens microservices) é considerada um requisito para [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) arquiteturas de aplicativo.

O [Foundation de computação nativo de nuvem (CNCF)](https://www.cncf.io/) é um Promotores primário dos princípios de nuvem nativo. A Microsoft tem um [membro o CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Para um exemplo de definição e para obter mais informações sobre as características dos aplicativos de nuvem nativo, consulte o artigo Gartner [como projetar e criar aplicativos de nuvem nativo](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Para obter orientações específicas da Microsoft sobre como implementar um aplicativo nativo de nuvem, consulte [microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook).

O fator mais importante a considerar se você migrar um aplicativo completo para o [nuvem nativo](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modelo é que você deverá arquitetar novamente para uma arquitetura baseada em microservices. Isso exige um investimento significativo em desenvolvimento devido o grande refatoração processo envolvido. Essa opção geralmente é escolhida para aplicativos de missão crítica que precisam de novos níveis de escalabilidade e agilidade de longo prazo. Mas, você pode começar a mover em direção à nuvem nativo adicionando microservices para apenas alguns novos cenários e eventualmente refatorar o aplicativo totalmente como microservices. Esta é uma abordagem incremental que é a melhor opção para alguns cenários.

## <a name="what-about-microservices"></a>E microservices? 

Noções básicas sobre microservices e como eles funcionam é importante quando você estiver pensando em aplicativos de nuvem nativo para sua organização.

A arquitetura de microservices é uma abordagem avançada que você pode usar para aplicativos que são criados do zero ou quando você desenvolve aplicativos existentes (local ou DevOps pronto aplicativos de nuvem) para aplicativos de nuvem nativo. Você pode iniciar adicionando microservices alguns aplicativos existentes para saber mais sobre os novos paradigmas de microservices. Mas, obviamente, você precisa arquiteto e código, especialmente para esse tipo de abordagem de arquitetura.

No entanto, microservices não são obrigatórios para qualquer aplicativo novo ou moderno. Microservices não são um marcador"magic", e não são a maneira recomendada único de criar todos os aplicativos. Como e quando você usar microservices depende do tipo de aplicativo que você precisa criar.

A arquitetura microservices está se tornando a abordagem preferencial para aplicativos de missão crítica distribuídos e grandes ou complexas com base em vários subsistemas independentes na forma de serviços autônomos. Em uma arquitetura baseada em microservices, um aplicativo é criado como uma coleção de serviços que podem ser desenvolvidos de forma independente, testada e com controle de versão, implantado e expandida. Isso pode incluir qualquer banco de dados relacionado, autônomo por microsserviço.

Para obter uma visão detalhada de uma arquitetura de microservices que você pode implementar usando .NET Core, consulte para download PDF livro eletrônico [microservices .NET: arquitetura de aplicativos .NET em contêineres](https://aka.ms/microservicesebook). O guia também está disponível [online](../../microservices-architecture/index.md).

Mas, mesmo em cenários em que microservices oferecem implantação de independente de recursos avançada, limites de subsistema de alta segurança e diversidade de tecnologia-elas também geram muitos novos desafios. Os desafios relacionados ao desenvolvimento de aplicativos distribuídos, como modelos de dados fragmentados e independente. Obtendo resiliente comunicação entre microservices; a necessidade de consistência eventual. e a complexidade operacional. Microservices introduzir um nível mais alto de complexidade em comparação comparada aplicativos monolíticos tradicionais.

Devido à complexidade de uma arquitetura de microservices, somente determinados tipos de aplicativos e cenários específicos são adequados para aplicativos baseados em microsserviço. Isso inclui aplicativos grandes e complexos que têm várias surgimento de subsistemas. Nesses casos, vale a pena investir em uma arquitetura de software mais complexa, para maior agilidade de longo prazo e manutenção de aplicativos mais eficiente. Mas para cenários menos complexos, talvez seja melhor continuar com uma abordagem de aplicativo monolítico ou abordagens mais simples de N camadas.

Uma observação final, mesmo com o risco de ser repetitiva sobre esse conceito, você não deve ver usando microservices em seus aplicativos como "completo ou nada mesmo*.*" Você pode estender e desenvolver aplicativos monolíticos existentes adicionando novos e cenários pequenos com base em microservices. Você não precisa começar do zero para começar a trabalhar com uma abordagem de arquitetura microservices. Na verdade, é recomendável que você evoluir do uso de um aplicativo monolítico ou de N camadas existente adicionando novos cenários. Por fim, você pode dividir o aplicativo em componentes autônomos ou microservices. Você pode iniciar o surgimento de seus aplicativos monolíticos em direção microservices, passo a passo.

## <a name="when-to-use-azure-app-service-for-modernizing-existing-net-apps"></a>Quando usar o serviço de aplicativo do Azure para modernizar aplicativos existentes do .NET

Quando você modernizar aplicativos da web ASP.NET existentes para o nível de maturidade otimizada para a nuvem, porque os aplicativos da web desenvolvidos usando o .NET Framework, suas dependências principais são no Windows e, provavelmente, o servidor de informações da Internet (IIS). Você pode usar e implantar aplicativos baseados no IIS e Windows por implantação diretamente em [do serviço de aplicativo do Azure](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is) ou pelo primeiro containerizing seu aplicativo usando os contêineres do Windows. Se containerizing, implantar os aplicativos ou a contêineres do Windows hospeda (baseado em VM) ou a uma malha de serviço do Azure que dá suporte a contêineres do Windows do cluster.

Quando você usar contêineres do Windows, você pode obter todos os benefícios do enormemente. Aumentar a agilidade no envio e implantar seu aplicativo e reduzir a fricção para problemas de ambiente (teste, desenvolvimento/teste, produção). Nas próximas seções, entrarmos em mais detalhes sobre os benefícios da usando contêineres.

No momento de escrever este guia, o serviço de aplicativo do Azure não oferece suporte a contêineres do Windows. Contêineres dá suporte para Linux. Portanto, pode ser sua próxima pergunta, "Como escolher entre o serviço de aplicativo do Azure e contêineres do Windows?"

Basicamente, se o serviço de aplicativo do Azure funciona para seu aplicativo e não existem qualquer servidor ou dependências personalizadas bloqueando o caminho para usar o serviço de aplicativo, você deve migrar seu aplicativo de web do .NET existente para o serviço de aplicativo. Que é a maneira mais fácil e mais eficiente para manter seu aplicativo. No Azure, seu aplicativo também terá um caminho mais simples de manutenção devido os benefícios da infraestrutura de PaaS, como DBaaS, CaaS e STaaS.

No entanto, se seu aplicativo tiver servidor ou dependências personalizadas que não há suporte para o serviço de aplicativo do Azure, você precisará considerar opções baseadas em contêineres do Windows. Exemplos de servidor ou dependências personalizadas incluem software de terceiros ou um arquivo. msi que precisa ser instalado no servidor, mas que não tem suporte no serviço de aplicativo do Azure. Outro exemplo é qualquer outra configuração de servidor que não tem suporte no serviço de aplicativo do Azure, como usar assemblies no Cache de Assembly Global (GAC) ou COM / componentes COM+. Graças a imagens de contêiner do Windows, você pode incluir as suas dependências personalizadas na mesma "unidade de implantação."

Como alternativa, você poderia refatorar as áreas do seu aplicativo que não são suportadas pelo serviço de aplicativo do Azure. Dependendo do volume de trabalho refatoração exigiria, você precisa avaliar cuidadosamente se que vale a pena.

### <a name="benefits-of-moving-to-azure-app-service"></a>Benefícios da transferência para o serviço de aplicativo do Azure

Serviço de aplicativo do Azure é um PaaS totalmente gerenciado oferta que torna mais fácil criar aplicativos web que contam com os processos de negócios. Quando você usa o serviço de aplicativo, você pode evitar os custos do gerenciamento de infraestrutura associados com a atualização e manutenção de aplicativos de web no local. Especificamente, você recorta o hardware e os custos de licenciamento da execução de aplicativos de web no local.

Se seu aplicativo da web é adequado para a migração para o serviço de aplicativo do Azure, o principal benefício é o período curto de tempo que leva para mover o aplicativo. Serviço de aplicativo oferece um ambiente muito fácil começar.

Serviço de aplicativo do Azure é a melhor opção para a maioria dos aplicativos web porque ele é o mais simples PaaS no Azure que você pode usar para executar aplicativos da web. Gerenciamento e implantação são integradas à plataforma, sites de dimensionar rapidamente para lidar com cargas de tráfego intenso e o Gerenciador de tráfego e balanceamento de carga interna fornecer alta disponibilidade.

Até mesmo a seus aplicativos web de monitoramento é simple, por meio do Azure Application Insights. Application Insights é fornecido gratuitamente com o serviço de aplicativo e não requer a gravar qualquer código especial em seu aplicativo. Apenas executar seu aplicativo web no serviço de aplicativo, e você terá um sistema de monitoramento atraente, sem trabalho adicional.

Com o serviço de aplicativo, você pode usar também diretamente muitos aplicativos de código-fonte aberto da Galeria de aplicativos Web do Azure (como o Umbraco ou o WordPress) ou você pode criar um novo site usando as ferramentas de sua escolha, como o ASP.NET e do framework. O recurso WebJobs do serviço de aplicativo facilita a adicionar um trabalho em segundo plano para seu aplicativo da web do serviço de aplicativo de processamento.

As principais vantagens de migrar seus aplicativos web usando o recurso de aplicativos Web do serviço de aplicativo do Azure incluem o seguinte:

-   O dimensionamento automático para atender à demanda horários e reduzir os custos durante horários de silêncio.

-   Backups automática de site para proteger as alterações e dados.

-   Alta disponibilidade e resiliência na plataforma do Azure PaaS.

-   Slots de implantação para ambientes de teste e desenvolvimento e para testar vários designs de site.

-   Balanceamento de carga e proteção de negação de serviço (DDoS).

-   Gerenciamento de tráfego para direcionar os usuários para a implantação geográfica mais próximo.

Embora o serviço de aplicativo pode ser a melhor escolha para novos aplicativos da web, no entanto, para aplicativos existentes, serviço de aplicativo pode ser a melhor opção somente se as suas dependências de aplicativo têm suporte no serviço de aplicativo.

### <a name="additional-resources"></a>Recursos adicionais

-   **Análise de compatibilidade para o serviço de aplicativo do Azure**  
[https://www.migratetoazure.net/Resources](https://www.migratetoazure.net/Resources)


### <a name="benefits-of-moving-to-windows-containers"></a>Benefícios de mover a contêineres do Windows

A principal vantagem de usar contêineres do Windows é que você obtém uma experiência de implantação mais confiável e aprimorado, em comparação comparada aplicativos não em contêineres. Além disso, seu aplicativo modernizado com contêineres efetivamente torna o seu aplicativo pronto para muitas outras plataformas e nuvens que dão suporte a contêineres do Windows. Os benefícios de mover a contêineres do Windows são abordados mais detalhadamente nas próximas seções.

Os ambientes de computação principal no Azure (em disponibilidade geral, a partir de meados de 2017) que dão suporte a contêineres do Windows são Azure Service Fabric e hosts básicos de contêineres do Windows (Windows Server 2016 VMs). Esses ambientes são os cenários de infraestrutura principal abordados neste guia.

Você também pode implantar os contêineres do Windows para outros orchestrators, como Kubernetes, Docker Swarm ou DC/OS. No momento (logo se enquadram 2017), essas plataformas estão em visualização no serviço de contêiner do Azure para usar contêineres do Windows.

>[!div class="step-by-step"]
[Anterior](microsoft-technologies-in-cloud-devops-ready-applications.md)
[Próximo](how-to-deploy-existing-net-apps-to-azure-app-service.md)
