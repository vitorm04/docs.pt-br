---
title: "Explicações passo a passo e technical obter a visão geral de Introdução"
description: "Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | explicações passo a passo e technical obter a visão geral de Introdução"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: e78dd4a324ca9fc973f1aa0d8e6a9abe1341876c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Explicações passo a passo e technical obter a visão geral de Introdução 

Para limitar o tamanho deste livro eletrônico, fizemos documentação técnica adicional e explicações passo a passo completa disponível em um repositório do GitHub. A série online de instruções passo a passo é descrita neste capítulo aborda a instalação passo a passo de vários ambientes baseados em contêineres do Windows e a implantação no Azure.

As seções a seguir explicam cada passo a passo novidades sobre seus objetivos, sua visão de alto nível- e fornece um diagrama das tarefas que estão envolvidos. Você pode obter instruções passo a passo em si no *eShopModernizing* aplicativos wiki de repositório do GitHub em [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).

# <a name="technical-walkthrough-list"></a>Lista de instruções passo a passo técnico

Orientações iniciada por get a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo de comparação de precisão e shift usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.

Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de amostra, que estão disponíveis no GitHub em [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

-   **Tour de aplicativos herdados eShop**

-   **Coloca seus aplicativos existentes do .NET com contêineres do Windows**

-   **Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure**

-   **Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure**

-   **Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Passo a passo 1: Tour aplicativos herdados eShop

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/01.-tour-on-eShopModernizing-Apps-Implementation-Code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a>Visão Geral

Neste passo a passo, você pode explorar a implementação inicial dos dois aplicativos herdados de exemplo. Os dois aplicativos de exemplo tem uma arquitetura monolítica e foram criados usando o ASP.NET clássico. Um aplicativo é baseado no ASP.NET 4. x MVC; o segundo aplicativo é baseado em Web Forms do ASP.NET 4. x. Ambos os aplicativos estão no [eShopModernizing do repositório GitHub](https://github.com/dotnet-architecture/eShopModernizing).

Você pode coloca os dois aplicativos de exemplo, semelhante ao modo coloca um clássico [Windows Communication Foundation](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) aplicativo (WCF) a serem consumidos como um aplicativo de área de trabalho. Para obter um exemplo, consulte [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).

### <a name="goals"></a>Objetivos

O objetivo principal deste passo a passo é apenas para se familiarizar com esses aplicativos e seu código e configuração. Você pode configurar os aplicativos para que eles gerarem e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste. Essa configuração opcional baseia-se na injeção de dependência, de modo separado.

### <a name="scenario"></a>Cenário

Figura 5-1 mostra um cenário simples de aplicativos herdados originais.

> ![Cenário de arquitetura simples dos aplicativos herdados originais](./media/image5-1.png)
>
> **Figura 5-1.** Cenário de arquitetura simples dos aplicativos herdados originais

De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento. Membros da equipe do enterprise eShop usaria o aplicativo para exibir e editar o catálogo de produtos. Figura 5-2 mostra as capturas de tela inicial do aplicativo.

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdado)](./media/image5-2.png)

> **Figura 5-2.** Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdado)

Esses são aplicativos web que são usados para navegar e modificar as entradas do catálogo. O fato de que ambos os aplicativos fornecem os mesmos recursos funcionais/de negócios é simplesmente para fins de comparação. Você pode ver um processo modernização semelhante para aplicativos que foram criados usando as estruturas de Web Forms do ASP.NET MVC do ASP.NET.

Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET MVC de núcleo. Isso demonstra que o ponto de se você não deseja refazer a arquitetura ou reescrever o código, você pode coloca os aplicativos existentes e ainda usar as mesmas tecnologias .NET e o mesmo código de erro. Você pode ver como você pode executar aplicativos como esses contêineres, sem qualquer alteração de código herdado.

### <a name="benefits"></a>Benefícios

Os benefícios deste passo a passo são simples: basta se familiarizar com a configuração do aplicativo e de código, com base em injeção de dependência. Em seguida, você pode fazer experiências com essa abordagem quando você coloca e implanta em vários ambientes no futuro.

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/01.-tour-on-eShopModernizing-Apps-Implementation-Code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Passo a passo 2: Coloca seus aplicativos existentes do .NET com contêineres do Windows

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-Web-Apps-with-Windows-Containers-and-Docker](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-DockerTBD)

### <a name="overview"></a>Visão Geral

Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, formulários da Web ou WCF, para ambientes de teste, desenvolvimento e produção.

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é mostrar a você diversas opções para containerizing um aplicativo existente do .NET Framework. Você pode:

-   Coloca o seu aplicativo usando [ferramentas do Visual Studio 2017 para Docker](https://docs.microsoft.com/dotnet/core/docker/visual-studio-tools-for-docker) (2017 do Visual Studio ou versões posteriores).

-   Coloca o seu aplicativo manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).

-   Coloca o seu aplicativo usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (um código-fonte aberto do Docker).

Este passo a passo enfoca o Visual Studio Tools 2017 abordagem Docker, mas as duas abordagens são bastante semelhantes no que diz respeito ao uso de Dockerfiles.

### <a name="scenario"></a>Cenário

Figura 5-3 mostra o cenário para aplicativos herdados eShop em contêineres.

> ![Diagrama de arquitetura simplificada de aplicativos em contêineres em um ambiente de desenvolvimento](./media/image5-3.png)
>
> **Figura 5-3.** Diagrama de arquitetura simplificada de aplicativos em contêineres em um ambiente de desenvolvimento

### <a name="benefits"></a>Benefícios

Há vantagens para executar seu aplicativo monolítico em um contêiner. Primeiro, crie uma imagem para o aplicativo. Daí em diante, cada implantação é executado no mesmo ambiente. Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instalado, usa a mesma versão do framework .NET e é criado usando o mesmo processo. Basicamente, você deve controlar as dependências do seu aplicativo usando uma imagem do Docker. As dependências de viagem com o aplicativo ao implantar os contêineres.

Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente que é fornecido pelos contêineres do Windows. Problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de ter em um ambiente de preparo ou produção. Diferenças nos ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.

Aplicativos em contêineres também têm uma curva mais simples de expansão. Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo comum por máquina. Isso resulta em maior densidade e menos necessários recursos, especialmente quando você usar orchestrators como Kubernetes ou do Service Fabric.

Enormemente, em situações ideais, não exige a fazer alterações no código do aplicativo (C\#). Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e compor Docker).

### <a name="next-steps"></a>Próximas etapas

Explorar o conteúdo mais detalhado no wiki do GitHub: [https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/03.-How-to-Deploy-Your-Windows-Containers-based-App-INTO-Azure-VMs-(including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Visão Geral

A implantação para um host Docker em uma VM do Windows Server 2016 no Azure permite configurar rapidamente ambientes de teste/desenvolvimento/teste. Ele também fornece um local comum para testadores ou usuários de negócios validar o aplicativo. Máquinas virtuais também podem ser válidos ambientes de produção de IaaS.

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é mostrar a você as várias alternativas que ao implantar contêineres do Windows em máquinas virtuais do Azure que são baseados no Windows Server 2016 ou versões posteriores.

### <a name="scenarios"></a>Cenários

Vários cenários são abordados neste passo a passo.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Cenário a: implantar para uma VM do Azure a partir de um computador de desenvolvimento por meio de conexão do mecanismo do Docker

![Implantar em uma VM do Azure a partir de um computador de desenvolvimento por meio de uma conexão do mecanismo do Docker](./media/image5-4.png)

> **Figura 5-4.** Implantar em uma VM do Azure a partir de um computador de desenvolvimento por meio de uma conexão do mecanismo do Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Cenário b: implantar em uma VM do Azure por meio de um registro de Docker

![Implantar uma VM do Azure por meio de um registro de Docker](./media/image5-5.png)

> **Figura 5-5.** Implantar uma VM do Azure por meio de um registro de Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a>Cenário c: implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services

![Implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services](./media/image5-6.png)

> **Figura 5-6.** Implantar em uma VM do Azure de pipelines de CI/CD no Visual Studio Team Services

### <a name="azure-vms-for-windows-containers"></a>Máquinas virtuais do Azure para contêineres do Windows

Máquinas virtuais do Azure para contêineres do Windows são simplesmente VMs que são baseados no Windows Server 2016, o Windows 10, ou versões posteriores, ambos com o mecanismo do Docker é configurado. Na maioria dos casos, você usará o Windows Server 2016 nas VMs do Azure.

Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**. Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou Nano Server do Windows. Imagens de contêiner do sistema operacional estão instaladas e, em seguida, a máquina virtual está pronta para uso com o Docker.

### <a name="benefits"></a>Benefícios

Embora os contêineres do Windows podem ser implantados em VMs do local no Windows Server 2016, quando você implanta no Azure, você obterá uma maneira fácil de começar, prontos para uso VMs de contêiner do Windows Server. Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de escala de VM do Azure.

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/03.-How-to-Deploy-Your-Windows-Containers-based-App-INTO-Azure-VMs-(including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Passo a passo 4: Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/04.-How-to-Deploy-Your-Windows-Containers-based-Apps-INTO-Kubernetes-in-Azure-container-Service-(including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Visão Geral

Um aplicativo baseado em contêineres do Windows precisará rapidamente usam as plataformas, ainda mais se afastando de VMs de IaaS. Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão. Você pode atingir essas metas, usando o orchestrator [Kubernetes](https://kubernetes.io/), disponível em [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é aprender como implantar um aplicativo baseado no contêiner do Windows para Kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure. Implantando a Kubernetes de zero é um processo de duas etapas:

1.  Implante um cluster de Kubernetes para serviço de contêiner do Azure.

2.  Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.

### <a name="scenarios"></a>Cenários

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Cenário a: a implantar diretamente a um cluster de Kubernetes a partir de um ambiente de desenvolvimento

![Implantar diretamente a um cluster de Kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

> **Figura 5-7.** Implantar diretamente a um cluster de Kubernetes de um ambiente de desenvolvimento

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a>Cenário b: implantar um cluster Kubernetes do CI/CD pipelines no Team Services

![Implantar um cluster Kubernetes de pipelines de CI/CD no Team Services](./media/image5-8.png)

> **Figura 5-8.** Implantar um cluster Kubernetes de pipelines de CI/CD no Team Services

### <a name="benefits"></a>Benefícios

Há muitos benefícios à implantação em um cluster em Kubernetes. O maior benefício é que você obtenha um ambiente pronto para produção no qual você pode expansão o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e com base no número de nós ou VMs no (cluster escalabilidade global do cluster).

Serviço de contêiner do Azure otimiza tecnologias e ferramentas de código aberto populares especificamente para o Azure. Você obtém uma solução aberta que oferece portabilidade, para os contêineres e sua configuração de aplicativo. Selecione o tamanho, o número de hosts, e o contêiner de ferramentas orchestrator serviço controla todo o resto.

Kubernetes, os desenvolvedores podem passam da ideia sobre máquinas físicas e virtuais, para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:

-   Aplicativos com base em vários contêineres

-   Replicação de instâncias de contêiner e o dimensionamento automático horizontal

-   Nomenclatura e descobrir (por exemplo, DNS interno)

-   Balanceamento de carga

-   Atualizações móveis

-   Distribuindo segredos

-   Verificações de integridade do aplicativo

## <a name="next-steps"></a>Próximas etapas

Explorar o conteúdo mais detalhado no wiki do GitHub: [(https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service- Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>Passo a passo 5: Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/05.-How-to-Deploy-Your-Windows-Containers-based-Apps-INTO-Azure-Service-Fabric-(including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Visão Geral

Um aplicativo baseado em contêineres do Windows precisará rapidamente usam as plataformas, ainda mais se afastando de VMs de IaaS. Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão. Você pode alcançar essas metas usando o orchestrator Service Fabric do Azure, que está disponível na nuvem do Azure, mas também disponível para uso local, ou até mesmo em uma nuvem pública diferente.

### <a name="goals"></a>Objetivos

É o objetivo deste passo a passo saber como implantar um aplicativo baseado no contêiner do Windows para um cluster do Service Fabric no Azure. Implantando a malha do serviço do zero é um processo de duas etapas:

1.  Implante um cluster do Service Fabric para o Azure (ou em um ambiente diferente).

2.  Implante o aplicativo e os recursos relacionados ao cluster do Service Fabric.

### <a name="scenarios"></a>Cenários

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Cenário a: implantar diretamente para um cluster do Service Fabric a partir de um ambiente de desenvolvimento

![Implantar diretamente a um cluster de malha do serviço de um ambiente de desenvolvimento](./media/image5-9.png)

> **Figura 5-9.** Implantar diretamente a um cluster de malha do serviço de um ambiente de desenvolvimento

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a>Cenário b: implantar um cluster do Service Fabric do CI/CD pipelines no Team Services

![Implantar em um cluster do Service Fabric de pipelines de CI/CD no Visual Studio Team Services](./media/image5-10.png)

> **Figura 5-10.** Implantar em um cluster do Service Fabric de pipelines de CI/CD no Visual Studio Team Services

## <a name="benefits"></a>Benefícios

Os benefícios da implantação em um cluster de malha do serviço são semelhantes aos benefícios de usar Kubernetes. Uma diferença, no entanto, é que o Service Fabric é um ambiente de produção maduro para aplicativos do Windows em comparação comparada Kubernetes, que estava no modo de visualização para contêineres do Windows até logo se enquadram de 2017. (Kubernetes é um ambiente mais maduro para Linux). 

O principal benefício do uso do Azure Service Fabric é que você obtenha um ambiente de produção no qual você pode expansão o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou VMs no cluster (escalabilidade global do cluster).

Malha do serviço do Azure oferece portabilidade para seus contêineres e sua configuração de aplicativo. Você pode ter uma malha do serviço de cluster no Azure, ou instale-o no local em seu próprio data center. Até você pode instalar um cluster do Service Fabric em uma nuvem diferente, como [AWS Amazon](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Com o Service Fabric, os desenvolvedores podem progresso da ideia sobre máquinas físicas e virtuais para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:

-   Aplicativos com base em vários contêineres.

-   Replicação de instâncias de contêiner e dimensionamento automático horizontal.

-   Nomenclatura e descoberta (por exemplo, DNS interno).

-   Balanceamento de carga.

-   Implantar atualizações.

-   Distribuindo segredos.

-   Verifica a integridade do aplicativo.

Os seguintes recursos são exclusivos na malha do serviço (em comparação com outras orchestrators):

-   Recurso de serviços com monitoração de estado, por meio do modelo de aplicativo de serviços confiáveis.

-   Padrão de atores, por meio do modelo de aplicativo de atores confiável.

-   Implante bare bone processos, além de contêineres do Windows ou Linux.

-   Atualizações e verificações de integridade avançadas.

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

[https://GitHub.com/dotnet-Architecture/eShopModernizing/wiki/05.-How-to-Deploy-Your-Windows-Containers-based-Apps-INTO-Azure-Service-Fabric-(including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Próximo](conclusions.md)
