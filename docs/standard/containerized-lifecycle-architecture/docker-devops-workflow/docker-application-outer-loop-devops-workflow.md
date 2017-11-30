---
title: Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo de Docker
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 070d174cde9e80f542865f5617b1c702a07a8018
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo de Docker

Figura 5-1 apresenta uma representação de ponta a ponta das etapas que compõem o fluxo de trabalho do DevOps loop externo.

![](./media/image1.png)

Figura 5-1: DevOps loop externo fluxo de trabalho para aplicativos de Docker com as ferramentas da Microsoft

Agora, vamos examinar cada uma dessas etapas mais detalhadamente.

## <a name="step-1-inner-loop-development-workflow"></a>Etapa 1: Fluxo de trabalho de desenvolvimento de loop interno

Esta etapa é explicada em detalhes no capítulo 4, mas, para recapitular, aqui é onde o loop externo começa, o momento em que um desenvolvedor envia o código para o sistema de gerenciamento de controle de origem (como o Git) Iniciando ações de pipeline de CI.

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>Etapa 2: Integração de controle do código-fonte e gerenciamento com o Visual Studio Team Services e o Git

Nesta etapa, você precisa ter um sistema de controle de versão para obter uma versão consolidada de todo o código provenientes de diferentes desenvolvedores na equipe.

Mesmo que o controle do código-fonte (SCC) e o gerenciamento de código-fonte podem parecer natureza de segundo ciclo à maioria dos desenvolvedores, ao criar aplicativos de Docker em uma duração de DevOps, é essencial para enfatizar que você não deve enviar as imagens do Docker com o aplicativo diretamente para o Docker registro global (como o registro de contêiner do Azure ou o Hub do Docker) da máquina do desenvolvedor. Ao contrário, as imagens do Docker para ser liberado e implantado em ambientes de produção devem ser criadas apenas em código-fonte que está sendo integrado no build global ou CI pipeline com base em seu repositório de código-fonte (como o Git).

As imagens de locais geradas pelos desenvolvedores se devem ser usadas apenas pelos desenvolvedores durante o teste em seu próprio computador. É por isso é essencial para que o pipeline de DevOps ativado do código de SCC.

Visual Studio Team Services e o Team Foundation Server suportam a controle de versão do Team Foundation e Git. Você pode escolher entre eles e usá-lo para uma experiência da Microsoft de ponta a ponta. No entanto, você também pode gerenciar seu código em repositórios externos (como GitHub, repositórios do Git local ou Subversão) e ainda poderá se conectar a ele e obter o código como o ponto de partida para o pipeline de CI DevOps.

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>Etapa 3: Compilação CI, integrar e teste com o Visual Studio Team Services e o Docker

CI surgiu como um padrão para testes de software moderno e entrega. A solução de Docker mantém uma clara separação de preocupações entre as equipes de desenvolvimento e operações. A imutabilidade de imagens do Docker garante uma implantação repetível entre o que tem desenvolvidos, testados por meio de CI e executar em produção. Mecanismo do docker implantadas em laptops developer e infraestrutura de teste torna os contêineres portátil em ambientes.

Neste ponto, após você ter um sistema de controle de versão com o código correto enviado, é necessário um *criar serviço* para acompanhar o código e execute o build global e testes.

O fluxo de trabalho interno para esta etapa (CI, compilação, teste) é sobre a construção de um pipeline de CI consiste em seu repositório de código (Git, etc.), o servidor de compilação (Visual Studio Team Services), o mecanismo do Docker e um registro de Docker.

Você pode usar Visual Studio Team Services como base para criação de seus aplicativos e definir seu pipeline de CI e para a publicação criados "artefatos" um "repositório de artefatos", que é explicada na próxima etapa.

Ao usar o Docker para a implantação, os "artefatos finais" para ser implantado são imagens do Docker com os aplicativos ou serviços inseridas dentro deles. Essas imagens são enviados por push ou publicadas em um *Docker registro* (um repositório privado como aquelas que no registro de contêiner do Azure ou um público como registro de Hub do Docker, que é normalmente usada para imagens de base oficiais).

Aqui está o conceito básico: CI o pipeline será iniciado-desligado por uma confirmação a um repositório do SCC como o Git. A confirmação fará com que o Visual Studio Team Services executar um trabalho de compilação em um contêiner do Docker e, após a conclusão bem-sucedida do trabalho, enviar por push uma imagem do Docker no registro do Docker, conforme ilustrado na Figura 5-2.

![](./media/image2.png)

Figura 5-2: as etapas envolvidas no CI

Aqui estão as etapas básicas de fluxo de trabalho de CI com o Docker e o Visual Studio Team Services:

1.  O desenvolvedor envia uma confirmação para um repositório de SCC (Git/Visual Studio Team Services, GitHub, etc.).

2.  Se você estiver usando o Visual Studio Team Services ou Git, CI incorporada, que significa que ele é tão simples quanto selecionar uma caixa de seleção no Visual Studio Team Services. Se você estiver usando um SCC externo (como GitHub), um *webhook* serão notifique Visual Studio Team Services da atualização ou enviar por push para Git/GitHub.

3.  Visual Studio Team Services recebe o repositório do SCC, incluindo o DockerFile que descrevem a imagem, bem como o código do aplicativo e teste.

4.  Visual Studio Team Services cria uma imagem do Docker e rótulos-lo com um número de compilação.

5.  Visual Studio Team Services instancia o contêiner de Docker dentro do Host do Docker provisionados e executa os testes apropriados.

6.  Se os testes forem bem-sucedidas, a imagem é primeiro novamente rotulada para um nome significativo para que você sabe que é um "build blessed" (como "/ 1.0.0" ou qualquer outro rótulo) e, em seguida, passado para o registro de Docker (Hub do Docker, o registro de contêiner do Azure, DTR, etc.)

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>Implementando o pipeline de CI com o Visual Studio Team Services e a extensão de Docker para Visual Studio Team Services

O [extensão do Visual Studio Team Services Docker](https://aka.ms/vstsdockerextension) adiciona uma tarefa ao seu pipeline de CI com a qual você pode criar imagens do Docker, enviar imagens do Docker para um registro de Docker autenticado, executar imagens do Docker ou executar outras operações oferecidas pelo CLI do docker. Ele também adiciona uma tarefa Docker Compose que você pode usar para criar, enviar por push e executar aplicativos de Docker multicontainer ou executar outras operações oferecidas pela CLI compor Docker, conforme mostrado na Figura 5-3.

![](./media/image3.png)

Figura 5-3: O pipeline de CI do Docker no Visual Studio Team Services

A extensão do Docker pode usar pontos de extremidade de serviço para os hosts de Docker e para registros de imagem ou contêiner. Padrão de tarefas usando um host Docker local se disponível (atualmente requer um agente personalizado do Visual Studio Team Services); Caso contrário, eles exigem que você forneça uma conexão de host do Docker. Ações que dependem de que está sendo autenticado com um registro de Docker, como enviar por push uma imagem, exigem que você forneça um Docker conexão do registro.

A extensão do Visual Studio Team Services Docker instala os seguintes componentes em sua conta do Visual Studio Team Services:

-   Um ponto de extremidade de serviço para se conectar a um registro de Docker

-   Um ponto de extremidade de serviço para se conectar a um Host do contêiner Docker

-   Uma tarefa de Docker para fazer o seguinte:

-   Criar uma imagem

-   Enviar por push uma imagem ou um repositório para um registro

-   Executar uma imagem em um contêiner

-   Executar um comando do Docker

-   Uma tarefa de Docker Compose para executar um comando Docker Compose

Essas tarefas do Visual Studio Team Services, uma compilação Host VM Linux Docker provisionado no Azure e o registro de Docker preferencial (registro de contêiner do Azure, Hub do Docker, privada DTR de Docker ou qualquer outro registro Docker), você pode montar seu pipeline de CI do Docker em um maneira muito consistente.

***Requisitos:***

-   Visual Studio Team Services, ou para instalações locais, o Team Foundation Server 2015 atualização 3 ou posterior.

-   Um agente do Visual Studio Team Services com os binários do Docker.

Uma maneira fácil de criar um desses é usar o Docker para executar um contêiner com base na imagem do Docker de agente do Visual Studio Team Services.

**Obter mais informações** para ler mais sobre como montar um CI de Docker de serviços do Visual Studio Team pipeline e para exibir explicações passo a passo, consulte os seguintes sites:

Executando um agente do Visual Studio Team Services como um contêiner do Docker: [https://hub.docker.com/r/ \ vsts/microsoft-agente /](https://hub.docker.com/r/microsoft/vsts-agent/)

Extensão de Docker VSTS: <https://aka.ms/vstsdockerextension>

Criação de imagens do Docker do .NET Core Linux com o Visual Studio Team Services: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

Criando um serviço de equipe com base em Linux Visual Studio crie máquina com suporte de Docker: <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>Integrar, testar e validar multicontainer aplicativos de Docker

Normalmente, a maioria dos aplicativos de Docker são compostos de vários contêineres em vez de um único contêiner. Um bom exemplo é um aplicativo orientado a microservices para os quais você teria um contêiner por microsserviço. Mas, mesmo sem seguir estritamente os padrões de abordagem microservices, é muito provável que o aplicativo de Docker deve ser composto de vários contêineres ou serviços.

Portanto, depois de criar os contêineres de aplicativo no pipeline de CI, você também precisa implantar, integrar e testar o aplicativo como um todo, com todos os seus contêineres dentro de um host Docker de integração ou até mesmo em um cluster de teste para que os contêineres são distribuído.

Se você estiver usando um único host, você pode usar comandos do Docker como o docker-compor para compilar e implantar contêineres relacionados para testar e validar o ambiente de Docker em uma única VM. Mas, se você estiver trabalhando com um cluster orchestrator como Docker Swarm, Kubernetes ou SO/controlador de domínio, você precisa implantar seus contêineres por meio de um mecanismo diferente ou orchestrator, dependendo de seu cluster/Agendador selecionado.

A seguir estão os vários tipos de testes que podem ser executados em contêineres do Docker:

-   Testes de unidade para contêineres do Docker

-   Grupos de teste de aplicativos inter-relacionados ou microservices

-   Testar em versões de produção e "canary"

O ponto importante é que, ao executar testes funcionais e integração, você deve executar esses testes de fora os contêineres. Testes não devem definidos e execute dentro dos contêineres que você está implantando, porque os contêineres são baseados em imagens estáticas que devem ser exatamente como os que você estiver implantando em produção.

É uma opção muito viável ao testar os cenários mais avançados como testar vários clusters (cluster, a preparação do cluster e o cluster de produção de teste) publicar as imagens de um registro para testar em vários clusters.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Enviar por push a imagem do Docker de aplicativo personalizado para o registro global de Docker

Depois que as imagens do Docker foram testadas e validadas, convém marcar e publicá-los no registro do Docker. O registro de Docker é uma parte crítica do ciclo de vida do aplicativo Docker porque é o local central onde você armazena seu teste personalizado (também conhecido como "blessed imagens") para ser implantado em ambientes de produção e controle de qualidade.

Semelhante a como o código do aplicativo armazenado no repositório SCC (Git, etc.) é o "fonte da verdade", o registro de Docker é o "fonte da verdade" para seu aplicativo binário ou bits a ser implantado em ambientes de produção ou de controle de qualidade.

Normalmente, talvez você queira ter seus repositórios particulares para as imagens personalizadas em um repositório privado de registro de contêiner do Azure ou em um registro local como registro confiável do Docker ou em um registro de nuvem pública com acesso restrito (como Hub do docker), embora no último caso se seu código não é o código-fonte aberto, você deve confiar segurança do fornecedor. De qualquer forma, o método pelo qual você fazer isso é bastante semelhante e, por fim, com base no comando docker push, conforme ilustrado na Figura 5-4.

![](./media/image4.png)

Figura 5-4: publicar imagens personalizadas do registro de Docker

Há várias ofertas de registros de Docker de fornecedores de nuvem como o registro de contêiner do Azure, registro de contêiner do Amazon Web Services, registro de contêiner do Google, Quay registro e assim por diante.

Usando a extensão do Visual Studio Team Services Docker, você pode enviar um conjunto de imagens de serviço definidas por um arquivo compose.yml docker, com várias marcas, um registro de Docker autenticado (como o registro de contêiner do Azure), conforme mostrado na Figura 5-5.

![](./media/image5.png)

Figura 5-5: usando o Visual Studio Team Services para publicação imagens personalizadas a um registro de Docker

**Obter mais informações** para saber mais sobre a extensão de Docker para Visual Studio Team Services, acesse <https://aka.ms/vstsdockerextension>. Para saber mais sobre o registro de contêiner do Azure, vá para <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Etapa 4: CD, implantar

A imutabilidade de imagens do Docker garante uma implantação repetível com o que tem desenvolvidos, testados por meio de CI e executar em produção. Depois de instalar as imagens do Docker aplicativo publicadas no registro do Docker (privado ou público), implantá-los para vários ambientes em que você pode ter (produção, QA, preparo, etc.) do seu pipeline de CD usando o Visual Studio Team Services pipeline de tarefas ou o Visual Studio Team Services Release Management.

No entanto, neste momento ele depende que tipo de aplicativo do Docker que você está implantando. Implantar um aplicativo simples (de composição e implantação de uma perspectiva) como um monolítico aplicativo que inclui alguns contêineres ou serviços e implantado para alguns servidores ou máquinas virtuais é muito diferente da implantação de um aplicativo mais complexo como um aplicativos orientados a microservices com recursos de hiperescala. Esses dois cenários descritos nas seções a seguir.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Implantando composto por aplicativos de Docker em vários ambientes de Docker

Vamos ver primeiro o cenário menos complexas: Implantando simples hosts de Docker (máquinas virtuais ou servidores) em um único ambiente ou em vários ambientes (QA, preparo e produção). Nesse cenário, internamente o pipeline de CD pode usar docker-compor (de suas tarefas de implantação do Visual Studio Team Services) para implantar os aplicativos do Docker com seu conjunto relacionado de contêineres ou serviços, conforme ilustrado na Figura 5-6.

![](./media/image6.png)

Figura 5-6: implantar os contêineres de aplicativos para registro simple de ambientes de host do Docker

Figura 5-7 destaca como você pode conectar o CI de compilação para ambientes de teste/QA por meio do Visual Studio Team Services clicando Docker compor na caixa de diálogo Adicionar tarefa. No entanto, ao implantar em ambientes de preparo ou de produção, você normalmente usaria vários ambientes de tratamento de recursos de gerenciamento de versão (como QA, preparo e produção). Se você estiver implantando em hosts de Docker único, ele está usando o Visual Studio Team Services tarefa "Docker Compose" (que está invocando o docker-compor o comando nos bastidores). Se você estiver implantando o serviço de contêiner do Azure, ele usa a tarefa de implantação do Docker, conforme explicado na seção a seguir.

![](./media/image7.png)

Figura 5-7: adicionando uma tarefa de Docker Compose em um pipeline do Visual Studio Team Services

Quando você cria uma versão no Visual Studio Team Services, ele usa um conjunto de artefatos de entrada. Eles devem ser imutável durante o tempo de vida da versão em vários ambientes. Quando você introduz contêineres, os artefatos de entrada identificam imagens em um registro para implantar. Dependendo de como eles são identificados, eles não são garantia permanecem os mesmos em toda a duração da versão, o caso mais óbvio sendo quando você faz referência a "myimage:latest" de um arquivo de docker-compose.

A extensão de Docker para Visual Studio Team Services fornece a capacidade de gerar artefatos de compilação que contém a imagem de registro específicos resumos garantidos para identificar exclusivamente a mesma imagem binária. Esses são o que você realmente deseja usar como entrada para uma versão.

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>Gerenciando versões para ambientes de Docker usando o Visual Studio Team Services Release Management

Por meio de extensões do Visual Studio Team Services, você pode criar uma nova imagem, publicá-lo em um registro de Docker, executá-lo em hosts do Windows ou do Linux e usar comandos como docker-compor para implantar vários contêineres como um aplicativo inteiro, tudo isso por meio do Visual Recursos de gerenciamento de versão do Team Services Studio destinados a vários ambientes, como mostrado na Figura 5-8.

![](./media/image8.png)

Figura 5-8: Configurando o Visual Studio Team Services Docker Compose tarefas do Visual Studio Team Services Release Management

No entanto, tenha em mente que o cenário mostrado na Figura 5-6 e implementado na Figura 5-8 é bem básico (ele está implantando VMs e hosts de Docker simples, e haverá uma instância por imagem ou um único contêiner) e provavelmente deve ser usado somente para teste ou desenvolvimento sc enarios. Na maioria dos cenários de produção corporativa, você deseja ter alta disponibilidade (HA) e fácil de gerenciar escalabilidade pelo balanceamento de carga entre vários nós, servidores e VMs, além de "failovers inteligente" assim que se um servidor ou o nó falhar, seus serviços e contêineres serão movidos para outro servidor de host ou máquina virtual. Nesse caso, você precisa de tecnologias mais avançadas, como clusters de contêiner, orchestrators e agendadores. Assim, a maneira de implantar os clusters é precisamente por meio de cenários avançados explicados na próxima seção.

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>Implantando aplicativos complexos de Docker para clusters de Docker (controlador de domínio/OS, Kubernetes e Docker Swarm)

A natureza de aplicativos distribuídos requer recursos de computação que também são distribuídos. Para que os recursos de escala de produção, você precisa ter recursos que fornecem alta escalabilidade de clustering e alta disponibilidade com base nos recursos em pool.

Você pode implantar contêineres manualmente para os clusters de uma ferramenta de CLI como Docker Swarm (como usar [criar serviço do docker](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) ou uma interface do usuário da web, como [Mesosphere maratona](https://mesosphere.github.io/marathon/docs/marathon-ui.html) para DC/OS clusters, mas você deve Reserve que somente para teste de implantação punctual ou para fins de gerenciamento como expansão ou fins de monitoramento.

De um ponto de vista do CD e o Visual Studio Team Services especificamente, pode executar tarefas de implantação especialmente feitas de seus ambientes do Visual Studio Team Services Release Management qual irá implantar seus aplicativos em contêineres para clusters distribuídos em Serviço de contêiner, conforme ilustrado na Figura 5-9.

![](./media/image9.png)

Figura 5-9: implantação de aplicativos distribuídos para o serviço de contêiner

Inicialmente, ao implantar determinados clusters ou orchestrators, você normalmente usaria scripts de implantação específica e mecanismos de por cada orchestrator (ou seja, Mesosphere DC/sistema operacional ou Kubernetes possuem mecanismos de implantação diferentes que o Docker e o Docker Swarm) em vez do mais simples e fácil de usar docker-compõem ferramenta com base no arquivo de definição de docker compose.yml. No entanto, graças a tarefa do Microsoft Visual Studio Team Services Docker implantar, mostrada na Figura 5-10, agora você também pode implantar para DC/OS usando apenas o arquivo de docker-compose.yml familiar porque a Microsoft executa essa conversão de"" para você (do seu arquivo compose.yml docker para outros formatos necessários ao controlador de domínio/OS).

![](./media/image10.png)

Figura 5-10: adicionando a tarefa de implantar o Docker para seu ambiente RM

Figura 5-11 demonstra como você pode editar a tarefa de implantar o Docker e especificar o tipo de destino (contêiner serviço DC/sistema operacional do Azure, neste caso), o arquivo compor do Docker e a conexão do Docker registro (como o registro de contêiner do Azure ou o Hub do Docker). Isso é onde a tarefa irá recuperar as imagens do Docker personalizadas prontos para uso para ser implantado como contêineres no cluster DC/OS.

![](./media/image11.png)

Implantação da definição de tarefa do Figura 5-11: implantar Docker para serviço de contêiner do Azure DC/OS

**Obter mais informações** para saber mais sobre o pipeline do CD com o Visual Studio Team Services e o Docker, visite os seguintes sites:

Extensão do Visual Studio Team Services para o Docker e o serviço de contêiner do Azure: [https://aka.ms/ \ vstsdockerextension](https://aka.ms/vstsdockerextension)

Serviço de contêiner do Azure: <https://aka.ms/azurecontainerservice>

Mesosphere DC/SO: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>Etapa 5: Executar e gerenciar

Como executar e gerenciar aplicativos em produção enterprise nível é uma entidade principal e de si mesma e devido ao tipo de operações e pessoas trabalhando nesse nível (operações de TI), bem como o grande escopo dessa área, podemos ter dedicada a todo o lado capítulo para explicar.

## <a name="step-6-monitor-and-diagnose"></a>Etapa 6: Monitorar e diagnosticar

Este tópico também é abordado no próximo capítulo como parte das tarefas que executa operações de TI em sistemas de produção. No entanto, é importante destacar que as informações obtidas nesta etapa devem feed volta para a equipe de desenvolvimento para que o aplicativo é aprimorado constantemente. Esse ponto de vista do também é parte do DevOps, embora as tarefas e operações são normalmente executadas por IT.

Somente quando o monitoramento e diagnóstico é 100 por cento no território de DevOps são os processos de monitoramento e análise realizada pela equipe de desenvolvimento em ambientes de teste ou beta. Isso é feito executando o teste de carga ou simplesmente monitorando beta ou ambientes de controle de qualidade, onde os testadores beta estão tentando as novas versões.

>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (... /Run-Manage-monitor-docker-Environments/index.MD)
