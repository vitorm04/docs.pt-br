---
title: Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo do Docker
description: Conheça as etapas de "loop externo" do fluxo de trabalho de DevOps
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 95664e20269f68a2eea5111b6c12ec7f108dc77b
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462975"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo do Docker

Figura 5-1 apresenta uma representação de ponta a ponta das etapas que compõem o fluxo de trabalho do DevOps loop externo.

![Este diagrama mostra o "loop externo" do DevOps. Quando o código for enviado para o repositório, um pipeline de CI é iniciado, em seguida, começa o pipeline de CD, onde o aplicativo é implantado. As métricas coletadas de aplicativos implantados são retornem para a carga de trabalho de desenvolvimento, onde ocorre o "loop interno", para que as equipes de desenvolvimento tenham dados reais para responder às necessidades de negócios e de usuário.](./media/image1.png)

**Figura 5-1**. Fluxo de trabalho do DevOps loop externo para aplicativos do Docker com as ferramentas da Microsoft

Agora, vamos examinar cada uma dessas etapas mais detalhadamente.

## <a name="step-1-inner-loop-development-workflow"></a>Etapa 1: Fluxo de trabalho de desenvolvimento do loop interno

Esta etapa é explicada em detalhes no capítulo 4, mas, para recapitular, aqui é onde começa o loop externo, o momento em que um desenvolvedor enviar código por push para o sistema de gerenciamento de controle do código-fonte (como o Git) Iniciando ações do pipeline de CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Etapa 2: Integração de controle do código-fonte e o gerenciamento com serviços de DevOps do Azure e o Git

Nesta etapa, você precisa ter um sistema de controle de versão para reunir uma versão consolidada de todo o código provenientes de diferentes desenvolvedores na equipe.

Mesmo que o controle do código-fonte (SCC) e o gerenciamento de código-fonte podem parecer à maioria dos desenvolvedores, durante a criação de aplicativos do Docker em uma vida de DevOps do ciclo de natureza de segundo, é essencial para enfatizar que você não deve enviar as imagens do Docker com o aplicativo diretamente para o Docker registro global (como o registro de contêiner do Azure ou Hub do Docker) do computador do desenvolvedor. Por outro lado, as imagens do Docker para ser lançado e implantado em ambientes de produção devem ser criadas apenas no código-fonte que está sendo integrado em seu build global ou de um pipeline de CI com base em seu repositório de código-fonte (como o Git).

As imagens de locais, geradas por desenvolvedores, devem apenas ser usadas por eles ao testar dentro de seus próprios computadores. É por isso que é essencial para ter o pipeline de DevOps ativado a partir do código de SCC.

Team Foundation Server e serviços de DevOps do Azure dão suporte a Git e o controle de versão do Team Foundation. Você pode escolher entre elas e usá-lo para uma experiência da Microsoft de ponta a ponta. No entanto, você também pode gerenciar seu código em repositórios externos (como GitHub, repositórios de Git local ou Subversion) e ainda ser capaz de se conectar a ele e obter o código como o ponto de partida para seu pipeline de DevOps CI.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Etapa 3: Compilar, CI, integrar e testar com o DevOps do Azure Services e o Docker

CI surgiu como um padrão para testes de software moderno e entrega. A solução do Docker mantém uma clara separação de preocupações entre as equipes de desenvolvimento e operações. A imutabilidade das imagens do Docker garante uma implantação repetível entre o que tem desenvolvido, testado por meio de CI e executar em produção. Mecanismo do docker implantado entre os laptops de desenvolvedor e infraestrutura de teste faz com que os contêineres portáteis entre ambientes.

Neste ponto, depois de ter um sistema de controle de versão com o código correto enviado, você precisa um *serviço de compilação* para acompanhar o código e executar o build global e os testes.

O fluxo de trabalho interno para esta etapa (CI, build, teste) é sobre a construção de um pipeline de CI consiste em seu repositório de código (Git, etc.), seu servidor de compilação (serviços de DevOps do Azure), o mecanismo do Docker e um registro do Docker.

Você pode usar os serviços de DevOps do Azure como a base para criação de seus aplicativos e definir seu pipeline de CI e para a publicação "artefatos" internos para um "repositório de artefatos", que é explicado na próxima etapa.

Ao usar o Docker para a implantação, os "artefatos finais" a serem implantados são imagens do Docker com o seu aplicativo ou serviços incorporadas dentro deles. Essas imagens são enviados por push ou publicadas em um *registro de Docker* (um repositório privado, como aqueles que você pode ter no registro de contêiner do Azure ou um pública como o registro de Hub do Docker, que é normalmente usada para as imagens base oficiais).

Aqui está o conceito básico: O pipeline de CI será iniciada por uma confirmação a um repositório do SCC, como Git. A confirmação fará com que os serviços de DevOps do Azure executar um trabalho de build dentro de um contêiner do Docker e, após a conclusão bem-sucedida do trabalho, enviar uma imagem do Docker para o registro de Docker, conforme ilustrado na Figura 5-2.

![A primeira parte do loop externo envolve as etapas 1 a 3, do código, executar, depurar e validar, em seguida, o repositório de código até a etapa de compilação e teste CI](./media/image2.png)

**Figura 5-2**. As etapas envolvidas no CI

Aqui estão as etapas de fluxo de trabalho de CI básicas com o Docker e serviços de DevOps do Azure:

1. O desenvolvedor envia uma confirmação para um repositório de SCC (Git/serviços do Azure DevOps, GitHub, etc.).

2. Se você estiver usando serviços de DevOps do Azure ou Git, CI é interna, que significa que ele é tão simples quanto selecionar uma caixa de seleção nos serviços de DevOps do Azure. Se você estiver usando um SCC externo (como o GitHub), um `webhook` irá notificar os serviços de DevOps do Azure da atualização ou enviar por push para o Git/GitHub.

3. Serviços de DevOps do Azure efetua pull do repositório de SCC, incluindo o Dockerfile que descrevem a imagem, bem como o código do aplicativo e de teste.

4. Os serviços do Azure DevOps cria uma imagem do Docker e rotula-lo com um número de compilação.

5. Os serviços do Azure DevOps cria uma instância de contêiner do Docker no Host do Docker provisionado e executa os testes apropriados.

6. Se os testes forem bem-sucedidos, a imagem é primeiro rotulados novamente com um nome significativo para que você sabe que é uma "compilação blessed" (como "/ 1.0.0" ou qualquer outro rótulo) e, em seguida, enviados por push para seu registro do Docker (Hub do Docker, registro de contêiner do Azure, DTR, etc.)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Implementando o pipeline de CI com os serviços de DevOps do Azure e a extensão do Docker para os serviços de DevOps do Azure

Serviços de DevOps do Visual Studio do Azure contém modelos de versão que você pode usar em seu pipeline de CI/CD com o qual você pode criar imagens do Docker, enviar por push imagens do Docker a um registro de Docker autenticado, executar imagens do Docker ou executar outras operações oferecidas pelo & compilação a CLI do Docker. Ele também adiciona uma tarefa do Docker Compose que você pode usar para compilar, enviar por push e executar aplicativos de vários contêineres do Docker ou executar outras operações oferecidas pela CLI redigir do Docker, conforme mostrado na Figura 5-3.

![Exibição de navegador do pipeline de CI de Docker no DevOps do Azure](./media/image3.png)

**Figura 5-3**. O pipeline de CI do Docker nos serviços de DevOps do Azure incluindo compilação & modelos de versão e as tarefas associadas.

Você pode usar esses modelos e tarefas para construir seus artefatos de CI/CD para criar / testar e implantar no Azure Service Fabric, serviço Kubernetes do Azure e ofertas semelhantes.

Com essas tarefas do Visual Studio Team Services, uma compilação de Host do Docker do Linux/VM provisionada no Azure e o registro de Docker preferencial (registro de contêiner do Azure, Hub do Docker, DTR privado do Docker ou qualquer outro registro do Docker), você pode montar seu pipeline de CI do Docker em um maneira muito consistente.

***Requisitos:***

- Serviços de DevOps do Azure, ou para instalações locais, o Team Foundation Server 2015 atualização 3 ou posterior.

- Um agente de serviços de DevOps do Azure que tem os binários de Docker.

  Uma maneira fácil de criar um desses agentes é usar o Docker para executar um contêiner com base na imagem do Docker de agente de serviços de DevOps do Azure.

> [! INFORMAÇÕES] para ler mais sobre como montar um CI de Docker de serviços do Azure DevOps de pipeline e exibir a instruções passo a passo, visitar esses sites:
>
> - Executando um agente do Visual Studio Team Services (agora serviços do Azure DevOps) como um contêiner do Docker: \
>   [https://hub.docker.com/r/microsoft/vsts-agent/](https://hub.docker.com/r/microsoft/vsts-agent/)
>
> - Criando imagens do Linux Docker no .NET Core com os serviços do Azure DevOps: \
>   [https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/](https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/)
>
> - Criando um serviço de equipe baseado em Linux Visual Studio crie a máquina com suporte do Docker: \
>   [http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support](http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support)

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Integrar, testar e validar aplicativos de vários contêineres do Docker

Normalmente, a maioria dos aplicativos do Docker são compostos de vários contêineres em vez de um único contêiner. Um bom exemplo é um aplicativo orientado a microsserviços para o qual você teria um contêiner por microsserviço. Mas, mesmo sem estritamente seguindo os padrões de abordagem de microsserviços, é provável que seu aplicativo do Docker deve ser composto de vários contêineres ou serviços.

Portanto, depois de criar os contêineres de aplicativo no pipeline de CI, você também precisa implantar, integrar e testar o aplicativo como um todo, com todos os seus contêineres dentro de um host do Docker de integração ou até mesmo em um cluster de teste para o qual seus contêineres são distribuído.

Se você estiver usando um único host, você pode usar comandos do Docker, como o docker-compose para compilar e implantar contêineres relacionados para testar e validar o ambiente do Docker em uma única VM. Mas, se você estiver trabalhando com um cluster do orquestrador, como Docker Swarm, Kubernetes ou DC/SO, você precisará implantar seus contêineres por meio de um mecanismo diferente ou o orchestrator, dependendo do seu cluster/Agendador selecionado.

A seguir estão os diversos tipos de testes que podem ser executados em contêineres do Docker:

- Testes de unidade para contêineres do Docker

- Grupos de testes de aplicativos inter-relacionados ou microsserviços

- Em versões "canário" e a produção de teste

O ponto importante é que, ao executar testes funcionais e integração, você deve executar esses testes de fora dos contêineres. Testes não são contidos ou executar nos contêineres que você está implantando, como os contêineres se baseiam em imagens estáticas que devem ser exatamente como as que você estará implantando para produção.

É uma opção prática, quando o teste mais cenários avançados, como incluindo vários clusters (cluster de produção, preparação de cluster e cluster de teste) publicar as imagens a um registro, portanto, ele pode ser testado em vários clusters.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Enviar por push a imagem do Docker de aplicativo personalizado em seu registro do Docker global

Depois que as imagens do Docker foram testadas e validadas, convém marcar e publicá-los em seu registro do Docker. O registro de Docker é uma peça fundamental no ciclo de vida do aplicativo Docker porque ele é o local central onde você armazena seu teste de personalizado (também conhecido como "blessed imagens") para ser implantado em ambientes de produção e de controle de qualidade.

Semelhante a como o código do aplicativo armazenado em seu repositório de SCC (Git, etc.) é a "fonte de verdade", o registro do Docker é a "fonte de verdade" para seu aplicativo binário ou bits devem ser implantados nos ambientes de controle de qualidade ou produção.

Normalmente, você talvez queira ter seus repositórios privados para suas imagens personalizadas em um repositório privado no registro de contêiner do Azure em um registro de local, como Docker Trusted Registry ou em um registro de nuvem pública com acesso restrito (como Hub do docker), embora Nesse último caso, se seu código não é código aberto, você deve confiar em segurança do fornecedor. De qualquer forma, o método usado é semelhante e se baseia o `docker push` de comando, conforme mostrado na Figura 5-4.

![Na etapa 3, para integração e teste (CI), você pode publicar as imagens do docker resultantes para um registro público ou privado.](./media/image4.png)

**Figura 5-4**. Publicando imagens personalizadas para registro do Docker

Há várias ofertas de registros do Docker de fornecedores de nuvem como o registro de contêiner do Azure, registro de contêiner do Amazon Web Services, o registro de contêiner do Google, registro Quay e assim por diante.

Usando as tarefas de Docker, você pode enviar por push um conjunto de imagens de serviço definidos por um `docker-compose.yml` de arquivo, com várias marcas a um registro de Docker autenticado (como o registro de contêiner do Azure), conforme mostrado na Figura 5-5.

![Modo de exibição de navegador da etapa para publicar imagens para um registro de DevOps do Azure.](./media/image5.png)

**Figura 5-5**. Usando os serviços de DevOps do Azure para publicação imagens personalizadas para um registro de Docker

> [! INFORMAÇÕES] para obter mais informações sobre o registro de contêiner do Azure, consulte <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Etapa 4: CD, implantar

A imutabilidade das imagens do Docker garante uma implantação repetível com o que tem desenvolvido, testado por meio de CI e executar em produção. Depois de ter as imagens do Docker aplicativo publicadas no seu registro de Docker (público ou privado), você pode implantá-los para vários ambientes em que você possa ter (produção, QA, preparo, etc.) do seu pipeline de CD usando serviços de DevOps do Azure tarefas de pipeline ou gerenciamento de versão de serviços de DevOps do Azure.

No entanto, nesse ponto depende do que tipo de aplicativo do Docker que você está implantando. Implantar um aplicativo simples (de composição e a implantação de uma perspectiva), como um monolítico implantado e de aplicativos que englobam alguns contêineres ou serviços para alguns servidores ou máquinas virtuais é diferente da implantação de um aplicativo mais complexo, como um aplicativo orientado a microsserviços com recursos em hiperescala. Esses dois cenários são explicados nas seções a seguir.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Implantando aplicativos de Docker em vários ambientes de Docker de compostos

Vamos ver primeiro o cenário menos complexas: Implantando a simples hosts de Docker (VMs ou servidores) em um ambiente único ou vários ambientes (garantia de qualidade, preparação e produção). Nesse cenário, internamente seu pipeline de CD pode usar o docker-compose (de suas tarefas de implantação de serviços de DevOps do Azure) para implantar os aplicativos do Docker com seu conjunto relacionado de contêineres ou serviços, conforme ilustrado na Figura 5 a 6.

![Implantar o CD de etapa (4) pode publicar em ambientes diferentes, como o q & a, preparo e produção.](./media/image6.png)

**Figura 5-6**. Implantação de contêineres de aplicativo para registro de ambientes de host de Docker simple

Figura 5 a 7 destaca como você pode conectar seu build CI para ambientes de controle de qualidade/teste nos serviços do Azure DevOps, clicando em Docker Compose na caixa de diálogo Adicionar tarefa. No entanto, ao implantar em ambientes de preparo ou produção, você normalmente usaria vários ambientes de tratamento de recursos do Release Management (como QA, preparo e produção). Se você estiver implantando em hosts únicos do Docker, ele está usando os serviços de DevOps do Azure "Docker Compose" tarefa (que está invocando o `docker-compose up` comando nos bastidores). Se você estiver implantando no serviço de contêiner do Azure, ele usa a tarefa de implantação do Docker, conforme explicado na seção a seguir.

![Modo de exibição de navegador de adição de uma tarefa do Docker Compose.](./media/image7.png)

**Figura 5-7**. Adicionando uma tarefa de Docker Compose em um pipeline de serviços de DevOps do Azure

Quando você cria uma versão nos serviços de DevOps do Azure, ele usa um conjunto de artefatos de entrada. Esses artefatos devem ser imutáveis durante a vida útil da versão, em todos os ambientes. Quando você introduz contêineres, os artefatos de entrada identificam imagens em um registro para implantar. Dependendo de como essas imagens são identificadas, eles não são garantidos para permanecem os mesmos ao longo da duração da versão, o mais óbvio caso que está sendo quando você referencia `myimage:latest` de um `docker-compose` arquivo.

Os modelos de serviços de DevOps do Azure oferecem a capacidade de gerar artefatos de compilação que contém a imagem do registro específica resumos garantida para identificar exclusivamente a mesma imagem binária. Esses são o que você realmente deseja usar como entrada para uma versão.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Gerenciamento de versões para ambientes do Docker usando o gerenciamento de versão de serviços de DevOps do Azure

Por meio dos modelos de serviços de DevOps do Azure, você pode criar uma nova imagem, publicá-lo em um registro de Docker, executá-lo em hosts Linux ou Windows e usar comandos como `docker-compose` para implantar vários contêineres como um aplicativo inteiro, tudo através de DevOps do Azure Serviços de recursos de gerenciamento de versão destinados a vários ambientes, conforme mostrado na Figura 5 a 8.

![Exibição de navegador do DevOps do Azure, configurar o Docker compose versões.](./media/image8.png)

**Figura 5-8**. Configurando serviços Docker Compose do Azure DevOps tarefas do gerenciamento de versão de serviços de DevOps do Azure

No entanto, tenha em mente que o cenário mostrado na Figura 5 a 6 e implementado na Figura 5-8 é um simples (ele está implantando VMs e hosts únicos do Docker, e haverá um único contêiner ou uma instância por imagem) e provavelmente deve ser usado apenas para desenvolvimento ou teste sce narios. Na maioria dos cenários de produção corporativo, você desejaria ter alta disponibilidade (HA) e fácil de gerenciar escalabilidade, balanceamento de carga entre vários nós, servidores e as VMs, além de "failovers inteligentes" Portanto, se um servidor ou um nó falhar, seus serviços e contêineres serão movidos para outro servidor de host ou VM. Nesse caso, você precisa de tecnologias mais avançadas, como clusters de contêiner, orquestradores e agendadores. Assim, a maneira de implantar a esses clusters é manipulando os cenários avançados explicada na próxima seção.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Implantando aplicativos do Docker para clusters do Docker

A natureza de aplicativos distribuídos exige recursos de computação que também são distribuídos. Para que os recursos de escala de produção, você precisa ter recursos que oferecem alta escalabilidade e alta disponibilidade com base nos recursos em pool de clustering.

Você pode implantar contêineres manualmente para esses clusters de uma ferramenta de CLI ou uma interface do usuário, da web, mas você deve reservar esse tipo de trabalho manual para teste de implantação especial ou fins de gerenciamento, como expansão ou monitoramento.

Do ponto de vista de CD e os serviços do Azure DevOps especificamente, pode executar tarefas de implantação feita especialmente de seus ambientes de gerenciamento de versão de serviços de DevOps do Azure que irá implantar seus aplicativos em contêineres para clusters distribuídos no contêiner Serviço, conforme ilustrado na Figura 5 a 9.

![Implantar o CD de etapa (4) também pode publicar em clusters por meio de orquestradores.](./media/image9.png)

**Figura 5-9**. Implantando aplicativos distribuídos para o serviço de contêiner

Inicialmente, ao implantar em determinadas clusters ou orquestradores, você tradicionalmente usaria mecanismos por cada orquestrador (ou seja, Kubernetes e Service Fabric possuem mecanismos de implantação diferentes) e scripts de implantação específico em vez do mais simples e fácil de usar `docker-compose` ferramenta com base no `docker-compose.yml` arquivo de definição. No entanto, graças à tarefa do Azure DevOps dos serviços de implantação do Docker, mostrada na Figura 5 a 10, você agora também pode implantar em orquestradores com suporte apenas usando o familiar `docker-compose.yml` arquivo porque a ferramenta realiza essa "tradução" para você (do seu `docker-compose.yml`arquivo para o formato necessário para o orchestrator).

![Tarefa de implantação do modo de exibição de navegador do catálogo de tarefas no DevOps do Azure, mostrando o Docker.](./media/image10.png)

**Figura 5-10**. Adicionando a tarefa de implantação do Docker para seu ambiente RM

Figura 5 a 11 demonstra como você pode editar a tarefa de implantação do Docker e especificar o tipo de destino (Azure Container Service DC/OS, neste caso), seu arquivo do Docker Compose e a conexão de registro do Docker (como o registro de contêiner do Azure ou Hub do Docker). Esta é a tarefa que irá recuperar as imagens do Docker personalizadas prontos para uso para ser implantado como contêineres no cluster.

![Exibição de navegador do DevOps do Azure, implante a definição de tarefa do orchestrator.](./media/image11.png)

**Figura 5-11**. Implantação da definição de tarefa do docker Deploy para serviço de contêiner do Azure DC/SO

> [! INFORMAÇÕES] para ler mais sobre o pipeline de CD com serviços de DevOps do Azure e o Docker, visite <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Etapa 5: Executar e gerenciar

Como executar e gerenciar aplicativos em produção enterprise nível é um assunto principal e de si mesmo e devido ao tipo de operações e pessoas trabalhando nesse nível (operações de TI), bem como o escopo grande desta área, o próximo capítulo inteiro é dedicado a explicá-lo.

## <a name="step-6-monitor-and-diagnose"></a>Etapa 6: Monitorar e diagnosticar

Este tópico também é abordado no próximo capítulo como parte das tarefas que ele executa em sistemas de produção. No entanto, é importante destacar que a das ideias obtidas nesta etapa devem feed volta para a equipe de desenvolvimento, de modo que o aplicativo é constantemente aprimorado. Desse ponto de Vista, ele também faz parte de DevOps, embora as operações e tarefas normalmente são executadas pelo IT.

Somente quando o monitoramento e diagnóstico é 100% dentro do domínio das operações de desenvolvimento são os processos de monitoramento e análise realizada pela equipe de desenvolvimento em ambientes de teste ou beta. Isso é feito pela execução de teste de carga ou monitorando beta ou ambientes de controle de qualidade, onde os testadores beta estão tentando as novas versões.

>[!div class="step-by-step"]
>[Anterior](index.md)
>[Próximo](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
