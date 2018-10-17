---
title: Instruções passo a passo e técnico obtém visão de geral de Introdução
description: Modernizar aplicativos .NET existentes com contêineres do Windows e de nuvem do Azure | Instruções passo a passo e técnico obtém visão de geral de Introdução
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 1c23acc16698446bc07c0047b68186e21c2ceb2d
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372845"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Instruções passo a passo e técnico obtém visão de geral de Introdução

Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e explicações passo a passo completa foram disponibilizada em um repositório GitHub. A série online de instruções passo a passo é descrita neste capítulo aborda a configuração passo a passo de vários ambientes em que se baseiam em contêineres do Windows e a implantação do Azure.

As seções a seguir explicam o que cada passo a passo é sobre seus objetivos e visão de alto nível e fornece um diagrama das tarefas que estão envolvidos. Você pode obter instruções passo a passo de si mesmos na *eShopModernizing* wiki do repositório de GitHub de aplicativos no [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).

## <a name="technical-walkthrough-list"></a>Passo a passo técnico lista

Orientações de Introdução a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo que você pode levantar e deslocar usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.

Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de exemplo, que estão disponíveis no GitHub em [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).

- **Tour de aplicativos herdados do eShop (aplicativos de linha de base para modernizar)**

- **Colocar seus aplicativos web ASP.NET existentes (WebForms e MVC) em um contêiner com contêineres do Windows**

- **Colocar em contêineres seus serviços do WCF (aplicativos de N camadas) existentes com contêineres do Windows**

- **Implantar seu aplicativo com base em contêineres do Windows em VMs do Azure**

- **Implantar seus aplicativos baseados em contêineres do Windows no Kubernetes no serviço de contêiner do Azure**

- **Implantar seus aplicativos baseados em contêineres do Windows no Azure Service Fabric**


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Passo a passo 1: Tour eShop de aplicativos herdados

### <a name="technical-walkthrough-availability"></a>Disponibilidade de passo a passo técnico

O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:

[instruções passo a passo de wiki de eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a>Visão geral

Neste passo a passo, você pode explorar a implementação inicial de três amostras de aplicativos herdados. Os dois primeiros aplicativos de web de exemplo tem uma arquitetura monolítica e foram criados usando ASP.NET clássico. Um aplicativo se baseia no ASP.NET 4.x MVC; o segundo aplicativo baseia-se nos Web Forms do ASP.NET 4. x. O aplicativo de terceiro é um aplicativo de camada 3 composto por um aplicativo de WinForms de cliente e um servidor [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.

Todos esses aplicativos estão disponíveis na [repositório do GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Objetivos

A principal meta deste passo a passo é simplesmente para se familiarizar com esses aplicativos e seu código e a configuração. Você pode configurar os aplicativos para que eles geram e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste. Essa configuração opcional se baseia na injeção de dependência, de forma desacoplada.

### <a name="scenario-1-aspnet-web-apps"></a>Cenário 1: Aplicativos de Web do ASP.NET

A figura a seguir mostra o cenário simples dos aplicativos de web ASP.NET herdados originais.

> ![Cenário de arquitetura simples dos aplicativos herdados originais de web do ASP.NET](./media/image5-1.png)
>

De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento. Membros da equipe do enterprise eShop poderia usar o aplicativo para exibir e editar o catálogo de produtos. 

A próxima figura mostra as capturas de tela inicial do aplicativo.

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdados)](./media/image5-2.png)

Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET Core MVC. 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Cenário 2: Serviço do WCF e aplicativo de cliente de WinForms (aplicativo de camada 3)

A figura a seguir mostra o cenário simples do aplicativo herdado de 3 camadas original.

> ![Cenário de arquitetura simples de aplicativo de camada 3 herdado original com um serviço WCF e um aplicativo de cliente de WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a>Benefícios

Os benefícios deste passo a passo são simples: basta se familiarizar com o código e aplicativos inicias.

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais detalhado no wiki do GitHub:

  - [Tour na linha de base ASP.NET MVC e aplicativos de Web Forms "herdados"](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [Tour sobre o serviço do WCF de linha de base e o aplicativo "herdado" do WinForms (camada 3)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Passo a passo 2: Colocar em contêineres seus aplicativos .NET existentes com contêineres do Windows

### <a name="overview"></a>Visão geral

Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles com base no MVC, Web Forms ou WCF, para ambientes de teste, desenvolvimento e produção.

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é mostrar a você várias opções para colocar em contêineres um aplicativo existente do .NET Framework. Você pode:

- Colocar o seu aplicativo em contêineres usando [ferramentas do Visual Studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versões posteriores).

- Colocar o seu aplicativo em contêineres manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Colocar o seu aplicativo em contêineres usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (uma ferramenta de código-fonte aberto do Docker).

Este passo a passo se concentra nas ferramentas do Visual Studio 2017 para a abordagem de Docker, mas as outras duas abordagens são bastante semelhantes em relação ao uso Dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Cenário 1: Aplicativos de web do ASP.NET em contêineres

Figura a seguir mostra o cenário para aplicativos de aplicativos web herdados eShop em contêineres.

> ![Diagrama da arquitetura simplificada de em contêineres aplicativos ASP.NET em um ambiente de desenvolvimento](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a>Cenário 2: Serviço do WCF em contêineres

Figura a seguir mostra o cenário para um aplicativo de camada 3 com um serviço WCF em contêineres. 

> ![Diagrama da arquitetura do serviço WCF em contêineres em um ambiente de desenvolvimento de simplificado](./media/image5-3.5.png)
>

### <a name="benefits"></a>Benefícios

Há vantagens em executar seu aplicativo monolítico em um contêiner. Primeiro, crie uma imagem para o aplicativo. Daí em diante, cada implantação é executada no mesmo ambiente. Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instaladas, usa a mesma versão do .NET framework e é criado usando o mesmo processo. Basicamente, você controla as dependências do seu aplicativo usando uma imagem do Docker. As dependências de viagem com o aplicativo quando você implanta os contêineres.

Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente, que é fornecido pelos contêineres do Windows. Os problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de surgirem em um ambiente de preparo ou produção. Diferenças em ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.

Aplicativos em contêineres também têm uma curva de escala horizontal mais simples. Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo regular por máquina. Isso resulta em maior densidade e menos necessários recursos, especialmente ao usar orquestradores como Kubernetes ou Service Fabric.

O uso de contêineres, em situações ideais, não requer fazer alterações ao código do aplicativo (C\#). Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e Docker Compose).

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais detalhado no wiki do GitHub:

  - [Como colocar em contêineres aplicativos web do .NET Framework com Docker e contêineres do Windows](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [Adicionando suporte ao Docker a um serviço WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows em VMs do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade de passo a passo técnico

O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Visão geral

Implantando em um host do Docker em um Windows Server 2016 Máquina Virtual (VM) no Azure permite que você configure rapidamente ambientes de desenvolvimento/teste /. Ele também fornece um lugar comum para testadores ou usuários de negócios validar o aplicativo. VMs também podem ser infraestrutura da válido como um ambiente de produção do serviço (IaaS).

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é mostrar as várias alternativas que você tem quando você implanta os contêineres do Windows para VMs do Azure que são baseados no Windows Server 2016 ou versões posteriores.

### <a name="scenarios"></a>Cenários

Vários cenários são abordados neste passo a passo.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Cenário a: a implantar uma VM do Azure a partir de um PC de desenvolvimento por meio de conexão do mecanismo do Docker

![Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de uma conexão do mecanismo do Docker](./media/image5-4.png)

> **Figura 5-4.** Implantar em uma VM do Azure a partir de um PC de desenvolvimento por meio de uma conexão do mecanismo do Docker

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Cenário b: implantar uma VM do Azure por meio de um registro de Docker

![Implantar em uma VM do Azure por meio de um registro de Docker](./media/image5-5.png)

> **Figura 5-5.** Implantar em uma VM do Azure por meio de um registro de Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Cenário c: implantar uma VM do Azure de pipelines de CI/CD nos serviços de DevOps do Azure

![Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-6.png)

> **Figura 5-6.** Implantar em uma VM do Azure a partir de pipelines de CI/CD nos serviços de DevOps do Azure

### <a name="azure-vms-for-windows-containers"></a>VMs do Azure para contêineres do Windows

VMs do Azure para contêineres do Windows são VMs com base no Windows Server 2016, Windows 10 ou versões posteriores, tanto com o mecanismo do Docker configurado. Na maioria dos casos, o Windows Server 2016 é usado em VMs do Azure.

Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**. Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou do Windows Nano Server. Imagens de contêiner do sistema operacional são instaladas e, em seguida, a VM está pronta para uso com o Docker.

### <a name="benefits"></a>Benefícios

Embora os contêineres do Windows podem ser implantados em VMs locais Windows Server 2016, quando você implanta no Azure, você obtém uma maneira fácil de obter uma introdução, pronto para usar VMs de contêiner do Windows Server. Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de dimensionamento de máquina virtual do Azure.

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais detalhado no wiki do GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Passo a passo 4: Implantar seus aplicativos baseados em contêineres do Windows para instâncias de contêiner do Azure (ACI)

### <a name="technical-walkthrough-availability"></a>Disponibilidade de passo a passo técnico

O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:

[A implantação dos aplicativos nas Aci (instâncias de contêiner do Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Visão geral

[Instâncias de contêiner do Azure (ACI)](https://docs.microsoft.com/azure/container-instances/) é a maneira mais rápida para ter um ambiente de desenvolvimento/teste/contêineres onde você pode implantar instâncias únicas de contêineres.

### <a name="goals"></a>Objetivos

Este passo a passo mostra os principais cenários ao implantar contêineres do Windows para instâncias de contêiner do Azure (ACI) e como você pode implantar aplicativos eShopModernizing em ACI.

### <a name="scenarios"></a>Cenários

Pode haver variações sobre como implantar os aplicativos eShopModernizing em ACI como implantar apenas um ou todos os aplicativos (aplicativo MVC, o aplicativo de formulários da Web ou serviço WCF). No cenário a seguir, mostrado abaixo, você pode ver o aplicativo ASP.NET MVC além de contêiner do SQL Server, os dois implantados como contêineres em ACI (instâncias de contêiner do Azure).

![Implantar em ACI a partir de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a>Benefícios

As instâncias de contêiner do Azure torna fácil criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior. Com o ACI, diretamente você pode implantar um contêiner do Windows no Azure e expô-lo à internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem de contêiner do Windows pronta em um registro de Docker, como o Hub do Docker ou do contêiner do Azure Registro).

### <a name="considerations"></a>Considerações

Implantar contêineres do Windows com o .NET Framework completo / ASP.NET ou SQL Server nas instâncias de contêiner do Azure (ACI) não é muito mais rápido implantar em um Host Docker regulares (como um Windows Server 2016 com contêineres do Windows) porque a imagem do Docker deve ser baixados (extraídas do registro do Docker) sempre e os tamanhos da imagem de contêiner do SQL (15.1 GB) e a imagem de contêiner do ASP.NET (13.9 GB) são muito grandes, no entanto, é muito mais barato do que manter seu próprio host do docker (permanentemente on-line Windows Server 2016 com VM de contêineres do Windows no Azure) para não mencionar um orquestrador de inteiro como o Kubernetes no Azure (AKS/ACS) ou Azure Service Fabric que são, por outro lado, excelentes opções para implantações de produção.

Como conclusão principal, usando instâncias de contêiner do Azure é uma opção muito atraente para cenários de desenvolvimento/teste e para os pipelines de CI/CD.

## <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais detalhado no wiki do GitHub: 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Passo a passo 5: Implantar seus aplicativos baseados em contêineres do Windows no Kubernetes no serviço de contêiner do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade de passo a passo técnico

O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Visão geral

Um aplicativo que se baseia em contêineres do Windows rapidamente precisará usar as plataformas, ainda mais se afastando das VMs de IaaS. Isso é necessário para atingir facilmente alta escalabilidade e melhor automatizada de escalabilidade e para uma melhoria significativa na automatizada implantações e controle de versão. Você pode obter essas metas, usando o orquestrador [Kubernetes](https://kubernetes.io/), disponível no [serviços de contêiner do Azure](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em Windows contêiner no Kubernetes (também chamado de *K8s*) no serviço de contêiner do Azure. Implantar no Kubernetes do zero é um processo em duas etapas:

1.  Implante um cluster Kubernetes no serviço de contêiner do Azure.

2.  Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.

### <a name="scenarios"></a>Cenários

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Cenário a: implantar diretamente a um cluster Kubernetes a partir de um ambiente de desenvolvimento

![Implantar diretamente a um cluster Kubernetes de um ambiente de desenvolvimento](./media/image5-7.png)

> **Figura 5-7.** Implantar diretamente a um cluster Kubernetes de um ambiente de desenvolvimento

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Cenário b: implantar um cluster Kubernetes de CI/CD pipelines nos serviços de DevOps do Azure

![Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-8.png)

> **Figura 5-8.** Implantar um cluster Kubernetes de pipelines de CI/CD nos serviços de DevOps do Azure

### <a name="benefits"></a>Benefícios

Há muitos benefícios para implantar um cluster no Kubernetes. O maior benefício é que você obtenha um ambiente pronto para produção em que você pode escalar horizontalmente o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou de VMs em (o cluster escalabilidade global do cluster).

O serviço de contêiner do Azure otimiza as tecnologias e ferramentas de código-fonte aberto populares especialmente para o Azure. Você obtém uma solução aberta que oferece portabilidade, tanto para os contêineres para sua configuração de aplicativo. Selecione o tamanho, o número de hosts, e o contêiner de ferramentas do orchestrator serviço lida com todo o resto.

Com o Kubernetes, os desenvolvedores podem progredir de pensar em máquinas físicas e virtuais, ao planejar uma infraestrutura centrada no contêiner que facilita os seguintes recursos, entre outros:

- Aplicativos com base em vários contêineres

- Replicação de instâncias de contêiner e o dimensionamento automático horizontal

- Nomenclatura e descobrindo (por exemplo, DNS interno)

- Balanceamento de carga

- Atualizações sem interrupção

- Distribuição de segredos

- Verificações de integridade do aplicativo

## <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais detalhado no wiki do GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>Passo a passo 6: Implantar seus aplicativos baseados em contêineres do Windows no Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>Disponibilidade de passo a passo técnico

O passo a passo técnica completo está disponível no wiki do repositório de GitHub eShopModernizing:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Visão geral

Um aplicativo baseado em contêineres do Windows rapidamente precisa usar as plataformas, ainda mais se afastando das VMs de IaaS. Isso é necessário para atingir facilmente alta escalabilidade e melhor automatizada de escalabilidade e para uma melhoria significativa na automatizada implantações e controle de versão. Para atingir essas metas, usando o orquestrador do Azure Service Fabric, que está disponível na nuvem do Azure, mas também está disponível para uso no local, ou até mesmo em uma nuvem pública diferente.

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em contêiner do Windows em um cluster do Service Fabric no Azure. Implantação do Service Fabric do zero é um processo de duas etapas:

1.  Implante um cluster do Service Fabric no Azure (ou em um ambiente diferente).

2.  Implante o aplicativo e os recursos relacionados ao cluster do Service Fabric.

### <a name="scenarios"></a>Cenários

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Cenário a: implantar diretamente para um cluster do Service Fabric a partir de um ambiente de desenvolvimento

![Implantar diretamente em um cluster do Service Fabric de um ambiente de desenvolvimento](./media/image5-9.png)

> **Figura 5-9.** Implantar diretamente em um cluster do Service Fabric de um ambiente de desenvolvimento

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Cenário b: implantar um cluster do Service Fabric de CI/CD pipelines nos serviços de DevOps do Azure

![Implantar um cluster do Service Fabric de pipelines de CI/CD nos serviços de DevOps do Azure](./media/image5-10.png)

> **Figura 5-10.** Implantar um cluster do Service Fabric de pipelines de CI/CD nos serviços de DevOps do Azure

## <a name="benefits"></a>Benefícios

Os benefícios de implantar um cluster no Service Fabric são semelhantes aos benefícios de usar o Kubernetes. Uma diferença, no entanto, é que o Service Fabric é um ambiente de produção mais maduro para aplicativos do Windows em comparação comparada Kubernetes, que está em uma fase beta para contêineres do Windows na versão 1.9 do Kubernetes (dezembro de 2017). O Kubernetes é um ambiente mais maduro para Linux.

O principal benefício do uso do Azure Service Fabric é que você obtenha um ambiente de produção em que você pode escalar horizontalmente o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou VMs no cluster (escalabilidade global do cluster).

O Azure Service Fabric oferece portabilidade para seus contêineres e sua configuração de aplicativo. Você pode ter uma malha de serviço de cluster no Azure, ou instalá-lo no local em seu próprio datacenter. Você pode até instalar um cluster do Service Fabric em uma nuvem diferente, como [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Com o Service Fabric, os desenvolvedores podem progredir de pensar em máquinas físicas e virtuais para planejar uma infraestrutura centrada no contêiner que facilita os seguintes recursos, entre outros:

- Aplicativos com base em vários contêineres.

- Replicação de instâncias de contêiner e o dimensionamento automático horizontal.

- Nomenclatura e descobrindo (por exemplo, DNS interno).

- Balanceamento de carga.

- Atualizações sem interrupção.

- Distribuição de segredos.

- Verificações de integridade do aplicativo.

Os seguintes recursos são exclusivos no Service Fabric (em comparação com outros orquestradores):

- Funcionalidade de serviços com estado, por meio do modelo de aplicativo de Reliable Services.

- Padrão de atores, por meio do modelo de aplicativo de Reliable Actors.

- Implante os processos de funções básicas, além de contêineres do Windows ou Linux.

- Atualizações sem interrupção e verificações de integridade avançados.

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais detalhado no wiki do GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Próximo](conclusions.md)
