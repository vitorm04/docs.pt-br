---
title: Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/10/2018
ms.openlocfilehash: a03853a508cfb3d5dd5fbfe66e4ef484b685faaa
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45653233"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo do Docker

Figura 5-1 apresenta uma representação de ponta a ponta das etapas que compõem o fluxo de trabalho do DevOps loop externo.

![](./media/image1.png)

Figura 5-1: DevOps loop externo fluxo de trabalho para aplicativos do Docker com as ferramentas da Microsoft

Agora, vamos examinar cada uma dessas etapas mais detalhadamente.

## <a name="step-1-inner-loop-development-workflow"></a>Etapa 1: o fluxo de trabalho de desenvolvimento de loop interno

Esta etapa é explicada em detalhes no capítulo 4, mas, para recapitular, aqui é onde começa o loop externo, o momento em que um desenvolvedor enviar código por push para o sistema de gerenciamento de controle do código-fonte (como o Git) Iniciando ações do pipeline de CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Etapa 2: Integração do controle do código-fonte e gerenciamento com serviços de DevOps do Azure e o Git

Nesta etapa, você precisa ter um sistema de controle de versão para reunir uma versão consolidada de todo o código provenientes de diferentes desenvolvedores na equipe.

Mesmo que o controle do código-fonte (SCC) e o gerenciamento de código-fonte podem parecer à maioria dos desenvolvedores, durante a criação de aplicativos do Docker em uma vida de DevOps do ciclo de natureza de segundo, é essencial para enfatizar que você não deve enviar as imagens do Docker com o aplicativo diretamente para o Docker registro global (como o registro de contêiner do Azure ou Hub do Docker) do computador do desenvolvedor. Por outro lado, as imagens do Docker para ser lançado e implantado em ambientes de produção devem ser criadas apenas no código-fonte que está sendo integrado em seu build global ou de um pipeline de CI com base em seu repositório de código-fonte (como o Git).

As imagens de locais geradas pelos desenvolvedores em si devem ser usadas apenas pelos desenvolvedores durante o teste em seus próprios computadores. É por isso é essencial para ter o pipeline de DevOps ativado a partir do código de SCC.

Team Foundation Server e serviços de DevOps do Azure dão suporte a Git e o controle de versão do Team Foundation. Você pode escolher entre elas e usá-lo para uma experiência da Microsoft de ponta a ponta. No entanto, você também pode gerenciar seu código em repositórios externos (como GitHub, repositórios de Git local ou Subversion) e ainda ser capaz de se conectar a ele e obter o código como o ponto de partida para seu pipeline de DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Etapa 3: Compilação, CI, integrar e testar com DevOps do Azure Services e o Docker

CI surgiu como um padrão para testes de software moderno e entrega. A solução do Docker mantém uma clara separação de preocupações entre as equipes de desenvolvimento e operações. A imutabilidade das imagens do Docker garante uma implantação repetível entre o que tem desenvolvido, testado por meio de CI e executar em produção. Mecanismo do docker implantado entre os laptops de desenvolvedor e infraestrutura de teste faz com que os contêineres portáteis entre ambientes.

Neste ponto, depois de ter um sistema de controle de versão com o código correto enviado, você precisa um *serviço de compilação* para acompanhar o código e executar o build global e os testes.

O fluxo de trabalho interno para esta etapa (CI, build, teste) é sobre a construção de um pipeline de CI consiste em seu repositório de código (Git, etc.), seu servidor de compilação (serviços de DevOps do Azure), o mecanismo do Docker e um registro do Docker.

Você pode usar os serviços de DevOps do Azure como a base para criação de seus aplicativos e definir seu pipeline de CI e para a publicação "artefatos" internos para um "repositório de artefatos", que é explicado na próxima etapa.

Ao usar o Docker para a implantação, os "artefatos finais" a serem implantados são imagens do Docker com o seu aplicativo ou serviços incorporadas dentro deles. Essas imagens são enviados por push ou publicadas em um *registro de Docker* (um repositório privado, como aqueles que você pode ter no registro de contêiner do Azure ou um pública como o registro de Hub do Docker, que é normalmente usada para as imagens base oficiais).

Aqui está o conceito básico: CI o pipeline será iniciada por uma confirmação a um repositório do SCC, como Git. A confirmação fará com que os serviços de DevOps do Azure executar um trabalho de build dentro de um contêiner do Docker e, após a conclusão bem-sucedida do trabalho, enviar uma imagem do Docker para o registro de Docker, conforme ilustrado na Figura 5-2.

![](./media/image2.png)

Figura 5-2: as etapas envolvidas no CI

Aqui estão as etapas de fluxo de trabalho de CI básicas com o Docker e serviços de DevOps do Azure:

1.  O desenvolvedor envia uma confirmação para um repositório de SCC (Git/serviços do Azure DevOps, GitHub, etc.).

2.  Se você estiver usando serviços de DevOps do Azure ou Git, CI é interna, que significa que ele é tão simples quanto selecionar uma caixa de seleção nos serviços de DevOps do Azure. Se você estiver usando um SCC externo (como o GitHub), uma *webhook* irá notificar os serviços de DevOps do Azure da atualização ou enviar por push para o Git/GitHub.

3.  Serviços de DevOps do Azure efetua pull do repositório de SCC, incluindo o DockerFile que descrevem a imagem, bem como o código do aplicativo e de teste.

4.  Os serviços do Azure DevOps cria uma imagem do Docker e rotula-lo com um número de compilação.

5.  Os serviços do Azure DevOps cria uma instância de contêiner do Docker no Host do Docker provisionado e executa os testes apropriados.

6.  Se os testes forem bem-sucedidos, a imagem é primeiro rotulados novamente com um nome significativo para que você sabe que é uma "compilação blessed" (como "/ 1.0.0" ou qualquer outro rótulo) e, em seguida, enviados por push para seu registro do Docker (Hub do Docker, registro de contêiner do Azure, DTR, etc.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementando o pipeline de CI com os serviços de DevOps do Azure e a extensão do Docker para os serviços de DevOps do Azure

O [extensão do Docker de serviços do Azure DevOps](https://aka.ms/vstsdockerextension) adiciona uma tarefa ao seu pipeline de CI com a qual você pode criar imagens do Docker, enviar por push imagens do Docker a um registro de Docker autenticado, executar imagens do Docker ou executar outras operações oferecidas pelo Docker CLI. Ele também adiciona uma tarefa do Docker Compose que você pode usar para compilar, enviar por push e executar aplicativos de vários contêineres Docker ou executar outras operações oferecidas pela CLI redigir do Docker, conforme mostrado na Figura 5-3.

![](./media/image3.png)

Figura 5-3: O pipeline de CI do Docker nos serviços de DevOps do Azure

A extensão do Docker pode usar pontos de extremidade de serviço para hosts do Docker e para o contêiner ou registros de imagem. O padrão de tarefas para usar um host de Docker local se estiver disponível (atualmente requer um agente personalizado de serviços de DevOps do Azure); Caso contrário, eles exigem que você forneça uma conexão de host do Docker. Ações que dependem do que está sendo autenticado com um registro de Docker, como enviar por push uma imagem, exigem que você forneça um Docker a conexão do registro.

A extensão do Docker de serviços do Azure DevOps instala os seguintes componentes na sua conta dos serviços do Azure DevOps:

-   Um ponto de extremidade de serviço para se conectar a um registro de Docker

-   Um ponto de extremidade de serviço para se conectar a um Host de contêiner do Docker

-   Uma tarefa de Docker para fazer o seguinte:

-   Criar uma imagem

-   Enviar por push uma imagem ou um repositório para um registro

-   Executar uma imagem em um contêiner

-   Executar um comando do Docker

-   Uma tarefa do Docker Compose para executar um comando do Docker Compose

Com essas tarefas de serviços de DevOps do Azure, uma compilação de Host do Docker do Linux/VM provisionada no Azure e o registro de Docker preferencial (registro de contêiner do Azure, Hub do Docker, DTR privado do Docker ou qualquer outro registro do Docker), você pode montar seu pipeline de CI do Docker em um muito maneira consistente.

***Requisitos:***

-   Serviços de DevOps do Azure, ou para instalações locais, o Team Foundation Server 2015 atualização 3 ou posterior.

-   Um agente de serviços de DevOps do Azure que tem os binários de Docker.

Uma maneira fácil de criar um desses é usar o Docker para executar um contêiner com base na imagem do Docker de agente de serviços de DevOps do Azure.

**Obter mais informações** para ler mais sobre como montar um CI de Docker de serviços do Azure DevOps de pipeline e para exibir instruções passo a passo, visite os seguintes sites:

Executando um agente de serviços de DevOps do Azure como um contêiner do Docker: [ https://hub.docker.com/r/\ microsoft/agente de vsts /](https://hub.docker.com/r/microsoft/vsts-agent/)

Extensão do Docker de serviços de DevOps do Azure: <https://aka.ms/vstsdockerextension>

Criando imagens do Linux Docker no .NET Core com os serviços do Azure DevOps: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Criando uma máquina de compilação baseado em Linux Visual Studio Team Service com suporte do Docker: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Integrar, testar e validar aplicativos de vários contêineres Docker

Normalmente, a maioria dos aplicativos do Docker são compostos de vários contêineres em vez de um único contêiner. Um bom exemplo é um aplicativo orientado a microsserviços para o qual você teria um contêiner por microsserviço. Mas, mesmo sem estritamente seguindo os padrões de abordagem de microsserviços, é muito provável que seu aplicativo do Docker deve ser composto de vários contêineres ou serviços.

Portanto, depois de criar os contêineres de aplicativo no pipeline de CI, você também precisa implantar, integrar e testar o aplicativo como um todo, com todos os seus contêineres dentro de um host do Docker de integração ou até mesmo em um cluster de teste para o qual seus contêineres são distribuído.

Se você estiver usando um único host, você pode usar comandos do Docker, como o docker-compose para compilar e implantar contêineres relacionados para testar e validar o ambiente do Docker em uma única VM. Mas, se você estiver trabalhando com um cluster do orquestrador, como Docker Swarm, Kubernetes ou DC/SO, você precisará implantar seus contêineres por meio de um mecanismo diferente ou o orchestrator, dependendo do seu cluster/Agendador selecionado.

A seguir estão os diversos tipos de testes que podem ser executados em contêineres do Docker:

-   Testes de unidade para contêineres do Docker

-   Grupos de testes de aplicativos inter-relacionados ou microsserviços

-   Em versões "canário" e a produção de teste

O ponto importante é que, ao executar testes funcionais e integração, você deve executar esses testes de fora dos contêineres. Testes não devem ser definidos e executados dentro dos contêineres que você está implantando, como os contêineres se baseiam em imagens estáticas que devem ser exatamente como aqueles que você implantará na produção.

É uma opção viável muito ao testar os cenários mais avançados, como teste de vários clusters (cluster de produção, preparação de cluster e cluster de teste) publicar as imagens em um registro de teste em vários clusters.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Enviar por push a imagem do Docker de aplicativo personalizado em seu registro do Docker global

Depois que as imagens do Docker foram testadas e validadas, convém marcar e publicá-los em seu registro do Docker. O registro de Docker é uma peça fundamental no ciclo de vida do aplicativo Docker porque ele é o local central onde você armazena seu teste de personalizado (também conhecido como "blessed imagens") para ser implantado em ambientes de produção e de controle de qualidade.

Semelhante a como o código do aplicativo armazenado em seu repositório de SCC (Git, etc.) é a "fonte de verdade", o registro do Docker é a "fonte de verdade" para seu aplicativo binário ou bits devem ser implantados nos ambientes de controle de qualidade ou produção.

Normalmente, você talvez queira ter seus repositórios privados para suas imagens personalizadas em um repositório privado no registro de contêiner do Azure em um registro de local, como Docker Trusted Registry ou em um registro de nuvem pública com acesso restrito (como Hub do docker), embora Nesse último caso, se seu código não é código aberto, você deve confiar em segurança do fornecedor. De qualquer forma, o método pelo qual você fazer isso é muito semelhante e, por fim, com base no comando docker por push, conforme ilustrado na Figura 5-4.

![](./media/image4.png)

Figura 5-4: publicar imagens personalizadas no registro do Docker

Há várias ofertas de registros do Docker de fornecedores de nuvem como o registro de contêiner do Azure, registro de contêiner do Amazon Web Services, o registro de contêiner do Google, registro Quay e assim por diante.

Usando a extensão do Docker de serviços de DevOps do Azure, você pode enviar por push um conjunto de imagens de serviço definidos por um arquivo docker-Compose. yml, com várias marcas a um registro de Docker autenticado (como o registro de contêiner do Azure), conforme mostrado na Figura 5-5.

![](./media/image5.png)

Figura 5-5: usando os serviços de DevOps do Azure para publicação imagens personalizadas para um registro de Docker

**Obter mais informações** para ler mais sobre a extensão do Docker para serviços de DevOps do Azure, vá para <https://aka.ms/vstsdockerextension>. Para saber mais sobre o registro de contêiner do Azure, vá para <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Etapa 4: CD, implantar

A imutabilidade das imagens do Docker garante uma implantação repetível com o que tem desenvolvido, testado por meio de CI e executar em produção. Depois de ter as imagens do Docker aplicativo publicadas no seu registro de Docker (público ou privado), você pode implantá-los para vários ambientes em que você possa ter (produção, QA, preparo, etc.) do seu pipeline de CD usando serviços de DevOps do Azure tarefas de pipeline ou gerenciamento de versão de serviços de DevOps do Azure.

No entanto, neste ponto depende do tipo de aplicativo do Docker que você está implantando. Implantar um aplicativo simples (de composição e a implantação de uma perspectiva), como um monolítico implantado e de aplicativos que englobam alguns contêineres ou serviços alguns servidores ou VMs é muito diferente da implantação de um aplicativo mais complexo, como um aplicativo orientado a microsserviços com recursos em hiperescala. Esses dois cenários são explicados nas seções a seguir.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Implantando aplicativos de Docker em vários ambientes de Docker de compostos

Vamos ver primeiro o cenário menos complexas: Implantando a simples hosts de Docker (VMs ou servidores) em um ambiente único ou vários ambientes (garantia de qualidade, preparação e produção). Nesse cenário, internamente seu pipeline de CD pode usar o docker-compose (de suas tarefas de implantação de serviços de DevOps do Azure) para implantar os aplicativos do Docker com seu conjunto relacionado de contêineres ou serviços, conforme ilustrado na Figura 5 a 6.

![](./media/image6.png)

Figura 5-6: implantação de contêineres de aplicativo para registro de ambientes de host de Docker simple

Figura 5 a 7 destaca como você pode conectar seu build CI para ambientes de controle de qualidade/teste nos serviços do Azure DevOps, clicando em Docker Compose na caixa de diálogo Adicionar tarefa. No entanto, ao implantar em ambientes de preparo ou produção, você normalmente usaria vários ambientes de tratamento de recursos do Release Management (como QA, preparo e produção). Se você estiver implantando em hosts únicos do Docker, ele está usando os serviços de DevOps do Azure "Docker Compose" tarefa (que está invocando o docker-compose comando nos bastidores). Se você estiver implantando no serviço de contêiner do Azure, ele usa a tarefa de implantação do Docker, conforme explicado na seção a seguir.

![](./media/image7.png)

Figura 5 a 7: adicionando uma tarefa de Docker Compose em um pipeline de serviços de DevOps do Azure

Quando você cria uma versão nos serviços de DevOps do Azure, ele usa um conjunto de artefatos de entrada. Elas devem ser imutáveis durante a vida útil da versão em vários ambientes. Quando você introduz contêineres, os artefatos de entrada identificam imagens em um registro para implantar. Dependendo de como eles são identificados, eles não são garantidos permanecem os mesmos em toda a duração da versão, o caso mais óbvio que está sendo ao fazer referência a "myimage:latest" de um arquivo docker-Compose.

A extensão do Docker para os serviços de DevOps do Azure oferece a capacidade de gerar artefatos de compilação que contém a imagem do registro específica resumos garantida para identificar exclusivamente a mesma imagem binária. Esses são o que você realmente deseja usar como entrada para uma versão.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Gerenciamento de versões para ambientes do Docker usando o gerenciamento de versão de serviços de DevOps do Azure

Por meio das extensões de serviços de DevOps do Azure, você pode criar uma nova imagem, publicá-lo em um registro de Docker, executá-lo em hosts Linux ou Windows e usar comandos como o docker-compose para implantar vários contêineres como um aplicativo inteiro, tudo através de DevOps do Azure Serviços de recursos de gerenciamento de versão destinados a vários ambientes, conforme mostrado na Figura 5 a 8.

![](./media/image8.png)

Figura 5 a 8: configurar o Docker Compose do Azure DevOps serviços tarefas do gerenciamento de versão de serviços de DevOps do Azure

No entanto, tenha em mente que o cenário mostrado na Figura 5 a 6 e implementado na Figura 5-8 é muito básico (ele está implantando VMs e hosts de Docker simples, e haverá um único contêiner ou uma instância por imagem) e provavelmente deve ser usado apenas para desenvolvimento ou teste sc enarios. Na maioria dos cenários empresariais de produção, convém ter alta disponibilidade (HA) e fácil de gerenciar escalabilidade por balanceamento de carga entre vários nós, servidores e as VMs, além de "failovers inteligentes" assim que se um servidor ou um nó falhar, seus serviços e contêineres serão movidos para outro servidor de host ou VM. Nesse caso, você precisa de mais avançadas tecnologias como clusters de contêiner, orquestradores e agendadores. Portanto, a maneira de implantar a esses clusters é precisamente por meio de cenários avançados, explicados na próxima seção.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Implantar aplicativos complexos do Docker para clusters do Docker (DC/OS, Kubernetes e Docker Swarm)

A natureza de aplicativos distribuídos exige recursos de computação que também são distribuídos. Para que os recursos de escala de produção, você precisa ter recursos que fornecem alta escalabilidade de clustering e alta disponibilidade com base nos recursos em pool.

Você pode implantar contêineres manualmente para esses clusters de uma ferramenta CLI, como Docker Swarm (como ao usar [criar serviço do docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) ou uma interface do usuário da web, como [Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) para DC/OS clusters, mas você deve Reserve que somente para teste de implantação punctual ou para fins de gerenciamento, como expansão ou fins de monitoramento.

Do ponto de vista de CD e os serviços do Azure DevOps especificamente, pode executar tarefas de implantação feita especialmente de seus ambientes de gerenciamento de versão de serviços de DevOps do Azure que irá implantar seus aplicativos em contêineres em clusters distribuídos no contêiner Serviço, conforme ilustrado na Figura 5 a 9.

![](./media/image9.png)

Figura 5 a 9: implantação de aplicativos distribuídos para o serviço de contêiner

Inicialmente, ao implantar em determinadas clusters ou orquestradores, tradicionalmente usaria os scripts de implantação específica e mecanismos de por cada orquestrador (ou seja, Mesosphere DC/SO ou Kubernetes possuem mecanismos de implantação diferentes que o Docker e Docker Swarm) em vez do mais simples e fácil de usar docker-compõem ferramenta com base no arquivo de definição de docker-Compose. yml. No entanto, graças a tarefa de implantação do Docker de serviços do Microsoft Azure DevOps, mostrada na Figura 5 a 10, você agora também pode implantar para DC/SO usando apenas seu arquivo docker-Compose. yml familiarizado, porque a Microsoft realiza essa "tradução" para você (da sua arquivo docker-Compose. yml para outros formatos necessários ao DC/OS).

![](./media/image10.png)

Figura 5 a 10: adicionando a tarefa de implantação do Docker para seu ambiente RM

Figura 5 a 11 demonstra como você pode editar a tarefa de implantação do Docker e especificar o tipo de destino (Azure Container Service DC/OS, neste caso), seu arquivo do Docker Compose e a conexão de registro do Docker (como o registro de contêiner do Azure ou Hub do Docker). Isso é onde a tarefa irá recuperar as imagens do Docker personalizadas prontos para uso para ser implantado como contêineres no cluster DC/SO.

![](./media/image11.png)

Implantação da definição de tarefa do Figura 5-11: Docker Deploy para serviço de contêiner do Azure DC/SO

**Obter mais informações** para ler mais sobre o pipeline de CD com serviços de DevOps do Azure e o Docker, visite os seguintes sites:

Extensão de serviços de DevOps do Azure para o Docker e o serviço de contêiner do Azure: [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Serviço de contêiner do Azure: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Etapa 5: Executar e gerenciar

Como executar e gerenciar aplicativos em produção enterprise nível é um assunto principal e de si mesmo e devido ao tipo de operações e pessoas trabalhando nesse nível (operações de TI), bem como o escopo grande desta área, podemos ter dedicada a toda a em seguida capítulo para explicá-lo.

## <a name="step-6-monitor-and-diagnose"></a>Etapa 6: Monitorar e diagnosticar

Este tópico também é abordado no capítulo seguinte como parte das tarefas que executa a operações de TI nos sistemas de produção; No entanto, é importante destacar que a das ideias obtidas nesta etapa devem feed volta para a equipe de desenvolvimento, de modo que o aplicativo é constantemente aprimorado. Desse ponto de Vista, ele também faz parte de DevOps, embora as operações e tarefas normalmente são executadas pelo IT.

Somente quando o monitoramento e diagnóstico é 100 por cento dentro do domínio das operações de desenvolvimento são os processos de monitoramento e análise realizada pela equipe de desenvolvimento em ambientes de teste ou beta. Isso é feito pela execução de teste de carga ou simplesmente pelo monitoramento beta ou ambientes de controle de qualidade, onde os testadores beta estão tentando as novas versões.

>[!div class="step-by-step"]
[Anterior](index.md)
[Próximo](../run-manage-monitor-docker-environments/index.md)
