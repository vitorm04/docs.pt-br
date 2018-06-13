---
title: Explicações passo a passo e technical obter a visão geral de Introdução
description: Modernizar aplicativos existentes do .NET com contêineres do Windows e de nuvem do Azure | Explicações passo a passo e technical obter a visão geral de Introdução
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027383"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Explicações passo a passo e technical obter a visão geral de Introdução

Para limitar o tamanho deste livro eletrônico, documentação técnica adicional e explicações passo a passo completa foram disponibilizada em um repositório do GitHub. A série online de instruções passo a passo é descrita neste capítulo aborda a instalação passo a passo de vários ambientes baseados em contêineres do Windows e a implantação no Azure.

As seções a seguir explicam o que cada passo a passo é sobre seus objetivos e visão de alto nível e fornece um diagrama das tarefas que estão envolvidos. Você pode obter instruções passo a passo em si no *eShopModernizing* aplicativos wiki de repositório do GitHub em [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).

## <a name="technical-walkthrough-list"></a>Lista de instruções passo a passo técnico

Orientações iniciada por get a seguir fornecem orientação técnica abrangente e consistente para os aplicativos de exemplo de comparação de precisão e shift usando os contêineres e, em seguida, mover, usando várias opções de implantação no Azure.

Cada as instruções a seguir usa os novo eShopLegacy e eShopModernizing aplicativos de amostra, que estão disponíveis no GitHub em [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).

- **Tour de eShop herdados aplicativos (aplicativos de linha de base para modernizar)**

- **Coloca seus aplicativos web ASP.NET existentes (WebForms & MVC) com contêineres do Windows**

- **Coloca os serviços do WCF (aplicativos de N camadas) existentes com contêineres do Windows**

- **Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure**

- **Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure**

- **Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric**


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Passo a passo 1: Tour aplicativos herdados eShop

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[explicações passo a passo do eShopModernizing wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a>Visão geral

Neste passo a passo, você pode explorar a implementação inicial de três aplicativos herdados de exemplo. Os aplicativos de web de exemplo dois primeiros têm uma arquitetura monolítica e foram criados usando o ASP.NET clássico. Um aplicativo é baseado no ASP.NET 4. x MVC; o segundo aplicativo é baseado em Web Forms do ASP.NET 4. x. O aplicativo de terceiro é um aplicativo de camada 3 composto por um aplicativo de WinForms de cliente e um servidor [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) serviço.

Todos esses aplicativos estão disponíveis no [eShopModernizing do repositório GitHub](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Objetivos

O objetivo principal deste passo a passo é apenas para se familiarizar com esses aplicativos e seu código e configuração. Você pode configurar os aplicativos para que eles gerarem e usam dados fictícios, sem usar o banco de dados SQL, para fins de teste. Essa configuração opcional baseia-se na injeção de dependência, de modo separado.

### <a name="scenario-1-aspnet-web-apps"></a>Cenário 1: Aplicativos da Web ASP.NET

A figura a seguir mostra um cenário simples que aplicativos herdados original de web do ASP.NET.

> ![Cenário de arquitetura simples aplicativos herdados original de web do ASP.NET](./media/image5-1.png)
>

De uma perspectiva de domínio de negócios, os dois aplicativos oferecem o mesmo catálogo de recursos de gerenciamento. Membros da equipe do enterprise eShop usaria o aplicativo para exibir e editar o catálogo de produtos. 

A figura a seguir mostra as capturas de tela inicial do aplicativo.

![Aplicativos ASP.NET MVC e Web Forms do ASP.NET (tecnologias existentes/herdado)](./media/image5-2.png)

Dependências no ASP.NET 4. x ou versões anteriores (seja para MVC ou Web Forms) significa que esses aplicativos não serão executados no .NET Core, a menos que o código é totalmente reescrito usando o ASP.NET MVC de núcleo. 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Cenário 2: Serviço do WCF e o aplicativo cliente do WinForms (aplicativo da camada 3)

A figura a seguir mostra um cenário simples com o aplicativo herdado de 3 camadas original.

> ![Cenário de arquitetura simples do aplicativo de camada 3 herdado original com um serviço WCF e um aplicativo cliente do WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a>Benefícios

Os benefícios deste passo a passo são simples: basta se familiarizar com o código e aplicativos inicias.

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

  - [Tour na linha de base ASP.NET MVC e aplicativos "herdados" do Web Forms](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [Tour sobre o serviço do WCF de linha de base e o aplicativo "herdado" do WinForms (camada 3)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Passo a passo 2: Coloca seus aplicativos existentes do .NET com contêineres do Windows

### <a name="overview"></a>Visão geral

Use contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, formulários da Web ou WCF, para ambientes de teste, desenvolvimento e produção.

### <a name="goals"></a>Objetivos

O objetivo deste passo a passo é mostrar a você diversas opções para containerizing um aplicativo existente do .NET Framework. Você pode:

- Coloca o seu aplicativo usando [ferramentas do Visual Studio 2017 para Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (2017 do Visual Studio ou versões posteriores).

- Coloca o seu aplicativo manualmente adicionando um [Dockerfile](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [CLI do Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Coloca o seu aplicativo usando o [Img2Docker](https://github.com/docker/communitytools-image2docker-win) ferramenta (um código-fonte aberto do Docker).

Este passo a passo enfoca o Visual Studio Tools 2017 abordagem Docker, mas as duas abordagens são bastante semelhantes em termos de uso Dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Cenário 1: Aplicativos de web do ASP.NET em contêineres

A figura abaixo mostra o cenário para os aplicativos de aplicativos web herdados eShop em contêineres.

> ![Diagrama de arquitetura simplificada de em contêineres de aplicativos ASP.NET em um ambiente de desenvolvimento](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a>Cenário 2: Serviço do WCF em contêineres

A figura abaixo mostra o cenário para um aplicativo de camada 3 com um serviço WCF em contêineres. 

> ![Diagrama da arquitetura do serviço do WCF em contêineres em um ambiente de desenvolvimento de simplificado](./media/image5-3.5.png)
>

### <a name="benefits"></a>Benefícios

Há vantagens para executar seu aplicativo monolítico em um contêiner. Primeiro, crie uma imagem para o aplicativo. Daí em diante, cada implantação é executado no mesmo ambiente. Cada contêiner usa a mesma versão do sistema operacional, tem a mesma versão das dependências instalado, usa a mesma versão do framework .NET e é criado usando o mesmo processo. Basicamente, você deve controlar as dependências do seu aplicativo usando uma imagem do Docker. As dependências de viagem com o aplicativo ao implantar os contêineres.

Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente que é fornecido pelos contêineres do Windows. Problemas que aparecem apenas com determinadas versões podem ser identificados imediatamente, em vez de ter em um ambiente de preparo ou produção. Diferenças nos ambientes de desenvolvimento usados por membros da equipe de desenvolvimento importam menor quando os aplicativos executados em contêineres.

Aplicativos em contêineres também têm uma curva mais simples de expansão. Aplicativos em contêineres permitem que você tenha mais aplicativos e instâncias de serviço (com base em contêineres) em uma VM ou máquina física em relação às implantações de aplicativo comum por máquina. Isso resulta em maior densidade e menos necessários recursos, especialmente quando você usar orchestrators como Kubernetes ou do Service Fabric.

Enormemente, em situações ideais, não exige a fazer alterações no código do aplicativo (C\#). Na maioria dos cenários, você precisa apenas os arquivos de metadados de implantação do Docker (arquivos Dockerfiles e compor Docker).

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

  - [Como coloca os aplicativos da web do .NET Framework com contêineres do Windows e o Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [Adicionando suporte de Docker para um serviço WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Passo a passo 3: Implantar seu aplicativo com base em contêineres do Windows para as VMs do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Visão geral

A implantação para um host Docker em um Windows Server 2016 Máquina Virtual (VM) no Azure permite configurar rapidamente ambientes de teste/desenvolvimento/teste. Ele também fornece um local comum para testadores ou usuários de negócios validar o aplicativo. Máquinas virtuais também podem ser infra-estrutura válida como ambientes de produção de serviço (IaaS).

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

Máquinas virtuais do Azure para contêineres do Windows são VMs com base no Windows Server 2016, o Windows 10 ou versões posteriores, ambos com o mecanismo do Docker configurado. Na maioria dos casos, o Windows Server 2016 é usado em VMs do Azure.

Atualmente, o Azure fornece uma VM denominada **Windows Server 2016 com contêineres**. Você pode usar essa VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou Nano Server do Windows. Imagens de contêiner do sistema operacional estão instaladas e, em seguida, a máquina virtual está pronta para uso com o Docker.

### <a name="benefits"></a>Benefícios

Embora os contêineres do Windows podem ser implantados em VMs do local no Windows Server 2016, quando você implanta no Azure, você obterá uma maneira fácil de começar, prontos para uso VMs de contêiner do Windows Server. Você também pode obter um local comum online que seja acessível para testadores e escalabilidade automática por meio de conjuntos de escala de máquina virtual do Azure.

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Passo a passo 4: Implantar seus aplicativos com base em contêineres do Windows para instâncias de contêiner do Azure (ACI)

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[Implantar os aplicativos para ACI (instâncias de contêiner do Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Visão geral

[Instâncias de contêiner do Azure (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) é a maneira mais rápida para ter um ambiente de teste/desenvolvimento/teste contêineres onde você pode implantar instâncias únicas de contêineres.

### <a name="goals"></a>Objetivos

Este passo a passo mostra os cenários principais ao implantar contêineres do Windows para instâncias de contêiner do Azure (ACI) e como você pode implantar aplicativos eShopModernizing em ACI.

### <a name="scenarios"></a>Cenários

Pode haver variações sobre como implantar os aplicativos eShopModernizing em ACI como implantar um ou todos os aplicativos (aplicativo MVC, o aplicativo de formulários da Web ou serviço WCF). No cenário a seguir mostrado abaixo, você pode ver o aplicativo ASP.NET MVC e o contêiner do SQL Server deles implantadas como contêineres para ACI (instâncias de contêiner do Azure).

![Implantar em ACI de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a>Benefícios

Instâncias de contêiner do Azure torna fácil criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior. Com ACI, diretamente você pode implantar um contêiner do Windows Azure e expô-lo com a internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem de contêiner do Windows pronta em um registro de Docker como o Hub do Docker ou do contêiner do Azure Registro).

### <a name="considerations"></a>Considerações

Implantar contêineres do Windows com o .NET Framework completo não é muito mais rápido implantando em um Host Docker regular (como um Windows Server 2016 com contêineres do Windows) como a imagem do Docker precisa ser ASP.NET ou do SQL Server em instâncias de contêiner do Azure (ACI) baixados (desconectado do registro do Docker) sempre e os tamanhos de imagem de contêiner SQL (15.1 GB) e a imagem de contêiner do ASP.NET (13.9 GB) são muito grandes, no entanto, é muito mais barato do que manter seu próprio host docker (permanentemente on-line Windows Server 2016 com a VM de contêineres do Windows no Azure) para não mencionar um orquestrador de inteiro como Kubernetes no Azure (AKS/ACS) ou Service Fabric do Azure que são, por outro lado, excelentes opções para implantações de produção.

Como principal conclusão, usando as instâncias de contêiner do Azure é uma opção muito convincente para cenários de desenvolvimento/teste em pipelines de CI/CD.

## <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub: 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Passo a passo 5: Implantar seus aplicativos com base em contêineres do Windows para Kubernetes no serviço de contêiner do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Visão geral

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

Há muitos benefícios à implantação em um cluster em Kubernetes. O maior benefício é que você obtenha um ambiente pronto para produção no qual você pode expandir o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e com base no número de nós ou VMs no (cluster escalabilidade global do cluster).

Serviço de contêiner do Azure otimiza tecnologias e ferramentas de código aberto populares especificamente para o Azure. Você obtém uma solução aberta que oferece portabilidade, para os contêineres e sua configuração de aplicativo. Selecione o tamanho, o número de hosts, e o contêiner de ferramentas orchestrator serviço controla todo o resto.

Kubernetes, os desenvolvedores podem passam da ideia sobre máquinas físicas e virtuais, para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:

- Aplicativos com base em vários contêineres

- Replicação de instâncias de contêiner e o dimensionamento automático horizontal

- Nomenclatura e descobrir (por exemplo, DNS interno)

- Balanceamento de carga

- Atualizações móveis

- Distribuindo segredos

- Verificações de integridade do aplicativo

## <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>Passo a passo 6: Implantar seus aplicativos com base em contêineres do Windows Azure Service Fabric

### <a name="technical-walkthrough-availability"></a>Disponibilidade do passo a passo técnico

Passo a passo completo técnica está disponível no wiki de repositório do GitHub eShopModernizing:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Visão geral

Um aplicativo baseado em contêineres do Windows rapidamente precisa usam as plataformas, ainda mais se afastando de VMs de IaaS. Isso é necessário para obter facilmente alta escalabilidade e melhor automatizada escalabilidade e para uma melhoria significativa em automatizada implantações e controle de versão. Você pode alcançar essas metas usando o orchestrator Service Fabric do Azure, que está disponível na nuvem do Azure, mas também disponível para uso local, ou até mesmo em uma nuvem pública diferente.

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

Os benefícios da implantação em um cluster de malha do serviço são semelhantes aos benefícios de usar Kubernetes. Uma diferença, no entanto, é que o Service Fabric é um ambiente de produção mais maduro para aplicativos do Windows em comparação comparada Kubernetes, que é uma fase de beta para contêineres do Windows em Kubernetes versão 1.9 (de 2017 dezembro). Kubernetes é um ambiente mais maduro para Linux.

O principal benefício do uso do Azure Service Fabric é que você obtenha um ambiente de produção no qual você pode expandir o aplicativo com base no número de instâncias de contêiner, você deseja usar (interna escalabilidade em nós existentes) e, com base no número de nós ou VMs no cluster (escalabilidade global do cluster).

Malha do serviço do Azure oferece portabilidade para seus contêineres e sua configuração de aplicativo. Você pode ter uma malha do serviço de cluster no Azure, ou instale-o no local em seu próprio data center. Até você pode instalar um cluster do Service Fabric em uma nuvem diferente, como [AWS Amazon](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Com o Service Fabric, os desenvolvedores podem progresso da ideia sobre máquinas físicas e virtuais para o planejamento de uma infra-estrutura centrada no contêiner que facilita os seguintes recursos, entre outros:

- Aplicativos com base em vários contêineres.

- Replicação de instâncias de contêiner e dimensionamento automático horizontal.

- Nomenclatura e descoberta (por exemplo, DNS interno).

- Balanceamento de carga.

- Implantar atualizações.

- Distribuindo segredos.

- Verifica a integridade do aplicativo.

Os seguintes recursos são exclusivos na malha do serviço (em comparação com outras orchestrators):

- Recurso de serviços com monitoração de estado, por meio do modelo de aplicativo de serviços confiáveis.

- Padrão de atores, por meio do modelo de aplicativo de atores confiável.

- Implante bare bone processos, além de contêineres do Windows ou Linux.

- Atualizações e verificações de integridade avançadas.

### <a name="next-steps"></a>Próximas etapas

Explore o conteúdo mais detalhado no wiki do GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Anterior](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Próximo](conclusions.md)
