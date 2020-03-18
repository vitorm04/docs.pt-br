---
title: Visão geral de tutoriais passo a passo e introduções técnicas
description: Modernizar aplicativos .NET existentes com contêineres Azure Cloud e Windows | Passo a passo e visão técnica começam
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660892"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>Visão geral de tutoriais passo a passo e introduções técnicas

Para limitar o tamanho deste e-book, documentação técnica adicional e os passoados completos foram disponibilizados em um repositório do GitHub. A série on-line de passo sadia que é descrita neste capítulo abrange a configuração passo a passo dos vários ambientes baseados em contêineres do Windows e a implantação no Azure.

As seções a seguir explicam do que se trata cada passo a passo, seus objetivos e visão de alto nível, e fornece um diagrama das tarefas envolvidas. Você pode obter os passo a passo nos aplicativos *eShopModernizing* GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.

## <a name="technical-walkthrough-list"></a>Lista técnica de passo a passo

Os passoados iniciais a seguir fornecem orientação técnica consistente e abrangente para aplicativos de amostra que você pode levantar e mudar usando contêineres e, em seguida, mover-se usando várias opções de implantação no Azure.

Cada um dos passoados a seguir usa os novos aplicativos eShopLegacy e eShopModernizing, que estão disponíveis no GitHub em <https://github.com/dotnet-architecture/eShopModernizing>.

- **Tour pelos aplicativos legados do eShop (aplicativos de base para modernizar)**

- **Contêiner seus aplicativos web ASP.NET existentes (WebForms & MVC) com contêineres do Windows**

- **Contêiner seus serviços WCF existentes (aplicativos N-Tier) com contêineres do Windows**

- **Implante seu aplicativo baseado em contêineres do Windows para as VMs do Azure**

- **Implante seus aplicativos baseados em contêineres do Windows para kubernetes no Serviço de Contêineres Do Azure**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Passo a passo 1: Tour pelos aplicativos legados do eShop

### <a name="technical-walkthrough-availability"></a>Disponibilidade técnica do passo a passo

O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:

[eShopModernizando os passoados da wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Visão geral

Neste passo a passo, você pode explorar a implementação inicial de três aplicativos legados de amostra. Os dois primeiros aplicativos web de amostra têm uma arquitetura monolítica, e foram criados usando ASP.NET clássicos. Um aplicativo é baseado em ASP.NET 4.x MVC; o segundo aplicativo é baseado em ASP.NET Formulários web 4.x.
O terceiro app é um aplicativo de 3 níveis composto por um aplicativo WinForms cliente e um serviço [de WCF (Windows Communication Foundation)](../../framework/wcf/whats-wcf.md) do lado do servidor.

Todos esses aplicativos estão disponíveis no [repo gitHub do eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Metas

O objetivo principal deste passo a passo é simplesmente se familiarizar com esses aplicativos, e com seu código e configuração. Você pode configurar os aplicativos para que eles gerem e usem dados simulados, sem usar o banco de dados SQL, para fins de teste. Esta configuração opcional é baseada na injeção de dependência, de forma dissociada.

### <a name="scenario-1-aspnet-web-apps"></a>Cenário 1: ASP.NET aplicativos web

A figura abaixo mostra o cenário simples do legado original ASP.NET aplicações web.

![Cenário de arquitetura simples do legado original ASP.NET aplicações web](./media/image5-1.png)

Do ponto de vista do domínio de negócios, ambos os aplicativos oferecem os mesmos recursos de gerenciamento de catálogo. Os membros da equipe corporativa da eShop usariam o aplicativo para visualizar e editar o catálogo de produtos.

A próxima figura mostra as capturas de tela iniciais do aplicativo.

![ASP.NET aplicativos MVC e ASP.NET Web Forms (tecnologias existentes/legados)](./media/image5-2.png)

Dependências em ASP.NET versões 4.x ou anteriores (seja para MVC ou para Formulários Web) significa que esses aplicativos não serão executados no .NET Core, a menos que o código seja totalmente reescrito usando ASP.NET MVC core.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Cenário 2: serviço WCF e aplicativo cliente WinForms (aplicativo de 3 níveis)

A figura abaixo mostra o cenário simples do aplicativo legado original de 3 níveis.

![Cenário de arquitetura simples do aplicativo original legado de 3 níveis com um serviço WCF e um aplicativo cliente WinForms](./media/image5-1.5.png)

### <a name="benefits"></a>Benefícios

Os benefícios deste passo a passo são simples: basta se familiarizar com o código e os aplicativos iniciais.

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais aprofundado na wiki do GitHub:

- [Tour na linha de base ASP.NET aplicativos "legados" de MVC e Web Forms](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Tour no serviço wcf de linha de base e no aplicativo "legado" WinForms (3-Tier)](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Passo a passo 2: Contêiner seus aplicativos .NET existentes com contêineres windows

### <a name="overview"></a>Visão geral

Use os contêineres do Windows para melhorar a implantação de aplicativos .NET existentes, como aqueles baseados em MVC, Formulários web ou WCF, para ambientes de produção, desenvolvimento e teste.

### <a name="goals"></a>Metas

O objetivo deste passo a passo é mostrar várias opções para contêiner um aplicativo .NET Framework existente. Você pode:

- Contêiner seu aplicativo usando [o Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 ou versões posteriores).

- Contêiner seu aplicativo adicionando manualmente um [arquivo Docker](https://docs.docker.com/engine/reference/builder/)e, em seguida, usando o [Cli Docker](https://docs.docker.com/engine/reference/commandline/cli/).

- Contêiner seu aplicativo usando a ferramenta [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (uma ferramenta de código aberto do Docker).

Este passo a passo se concentra na abordagem Visual Studio 2017 Tools for Docker, mas as outras duas abordagens são bastante semelhantes em relação ao uso de Dockerfiles.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Cenário 1: Aplicativos web ASP.NET contêiner

A figura abaixo mostra o cenário para aplicativos web legados do eShop contêiner.

![Diagrama de arquitetura simplificado de aplicações ASP.NET contêiner em um ambiente de desenvolvimento](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Cenário 2: Serviço de CfFC containerizado

A figura abaixo mostra o cenário de um aplicativo de 3 níveis com um serviço WCF contêiner.

![Diagrama de arquitetura simplificado do serviço WCF contêiner em um ambiente de desenvolvimento](./media/image5-3.5.png)

### <a name="benefits"></a>Benefícios

Há vantagens em executar sua aplicação monolítica em um recipiente. Primeiro, você cria uma imagem para o aplicativo. A partir daí, todas as implantações são executadas no mesmo ambiente. Cada contêiner usa a mesma versão do SISTEMA OPERACIONAL, tem a mesma versão de dependências instaladas, usa a mesma versão de framework .NET e é construído usando o mesmo processo. Basicamente, você controla as dependências do seu aplicativo usando uma imagem do Docker. As dependências viajam com o aplicativo quando você implanta os contêineres.

Um benefício adicional é que os desenvolvedores podem executar o aplicativo no ambiente consistente que é fornecido pelo Windows Containers. Problemas que aparecem apenas com determinadas versões podem ser detectados imediatamente, em vez de aparecer em um ambiente de encenação ou produção. As diferenças nos ambientes de desenvolvimento usados pelos membros da equipe de desenvolvimento importam menos quando as aplicações são executadas em contêineres.

Aplicações conteificadas também têm uma curva de escala mais plana. Os aplicativos em contêiner permitem que você tenha mais instâncias de aplicação e serviço (baseadas em contêineres) em uma VM ou máquina física em comparação com implantações regulares de aplicativos por máquina. Isso se traduz em maior densidade e menos recursos necessários, especialmente quando você usa orquestradores como Kubernetes.

A containerização, em situações ideais, não requer\#qualquer alteração no código do aplicativo (C ). Na maioria dos cenários, você só precisa dos arquivos de metadados de implantação do Docker (arquivos Dockerfiles e Docker Compose).

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais aprofundado na wiki do GitHub:

- [Como contêiner os aplicativos web .NET Framework com Contêineres Windows e Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Adicionando suporte ao Docker a um serviço WCF](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Passo a passo 3: implante seu aplicativo baseado em contêineres do Windows para as VMs do Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade técnica do passo a passo

O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Visão geral

A implantação em um host Docker em uma Máquina Virtual (VM) do Windows Server 2016 no Azure permite configurar rapidamente ambientes de desenvolvimento/teste/estágio. Ele também lhe dá um lugar comum para testadores ou usuários de negócios validarem o aplicativo. As VMs também podem ser ambientes de produção de infra-estrutura como serviço (IaaS).

### <a name="goals"></a>Metas

O objetivo deste passo a passo é mostrar as múltiplas alternativas que você tem ao implantar o Windows Containers para As VMs do Azure que são baseadas nas versões windows server 2016 ou posteriores.

### <a name="scenarios"></a>Cenários

Vários cenários estão cobertos neste passo a passo.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Cenário A: Implantar em um VM Azure a partir de um PC dev através da conexão Docker Engine

![Implantar em um Azure VM a partir de um PC dev através de uma conexão Docker Engine](./media/image5-4.png)

**Figura 5-4.** Implantar em um Azure VM a partir de um PC dev através de uma conexão Docker Engine

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Cenário B: Implantar em uma VM Azure através de um Registro Docker

![Implantar em uma VM Azure através de um Registro Docker](./media/image5-5.png)

**Figura 5-5.** Implantar em uma VM Azure através de um Registro Docker

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Cenário C: Implantar em um VM Azure a partir de gasodutos CI/CD nos Serviços Azure DevOps

![Implantar em um VM Azure a partir de gasodutos CI/CD nos Serviços Azure DevOps](./media/image5-6.png)

**Figura 5-6.** Implantar em um VM Azure a partir de gasodutos CI/CD nos Serviços Azure DevOps

### <a name="azure-vms-for-windows-containers"></a>VMs do Azure para Contêineres Windows

As VMs do Azure para Contêineres Windows são VMs baseadas no Windows Server 2016, Windows 10 ou versões posteriores, ambas com o Docker Engine configurado. Na maioria dos casos, o Windows Server 2016 é usado nas VMs do Azure.

Atualmente, o Azure fornece uma VM chamada **Windows Server 2016 com Contêineres**. Você pode usar este VM para experimentar o novo recurso de contêiner do Windows Server, com o Windows Server Core ou o Windows Nano Server. As imagens do sistema operacional de contêiner são instaladas e, em seguida, a VM está pronta para usar com o Docker.

### <a name="benefits"></a>Benefícios

Embora os contêineres do Windows possam ser implantados em VMs do Windows Server 2016, quando você for implantado no Azure, você tem uma maneira mais fácil de começar, com VMs de contêiner do Windows Server prontos para uso. Você também tem um local on-line comum que é acessível aos testadores e escalabilidade automática através de conjuntos de escala de máquinas virtuais do Azure.

### <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais aprofundado na wiki do GitHub:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Passo a passo 4: implante seus aplicativos baseados em contêineres do Windows para a ACI (ACI)

### <a name="technical-walkthrough-availability"></a>Disponibilidade técnica do passo a passo

O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:

[Implantação dos aplicativos para ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Visão geral

[A ACI (Azure Container Instances, instâncias de contêiner do Azure)](https://docs.microsoft.com/azure/container-instances/) é a maneira mais rápida de ter um ambiente de dev/teste/estágio de contêineres onde você pode implantar instâncias únicas de contêineres.

### <a name="goals"></a>Metas

Este passo a passo mostra os principais cenários ao implantar os contêineres do Windows no ACI (ACI) e como você pode implantar aplicativos de eShopModernizando em ACI.

### <a name="scenarios"></a>Cenários

Pode haver variações sobre a implantação dos aplicativos eShopModernizando em ACI, como a implantação de apenas um ou todos os aplicativos (aplicativo MVC, aplicativo WebForms ou serviço WCF). No cenário a seguir mostrado abaixo, você pode ver o aplicativo mvc ASP.NET mais o contêiner SQL Server, ambos implantados como contêineres em ACI (Azure Container Instances).

![Implantar na ACI a partir de um ambiente de desenvolvimento](./media/image5-3.5.6.png)

### <a name="benefits"></a>Benefícios

As Instâncias de Contêiner do Azure facilitam criar e gerenciar contêineres do Docker no Azure, sem a necessidade de provisionar máquinas virtuais ou adotar um serviço de nível superior. Com a ACI, você pode implantar diretamente um contêiner do Windows no Azure e expô-lo à internet com um nome de domínio totalmente qualificado (FQDN) em questão de segundos (desde que você tenha a imagem do Contêiner do Windows pronta em um registro docker como Docker Hub ou Azure Container Registro).

### <a name="considerations"></a>Considerações

Implantar contêineres windows com o Framework /ASP.NET ou o SQL Server completos no Azure Container Instances (ACI) não é tão rápido quanto implantar em um Host Docker normal (como um Windows Server 2016 com contêineres windows) porque a imagem do Docker tem que ser baixada (retirada do registro docker) todas as vezes e os tamanhos da imagem do contêiner SQL (15,1 GB) e da imagem do contêiner ASP.NET (13,9 GB) são significativamente significativamente no entanto, é muito mais barato do que manter seu próprio host docker (permanentemente on-line Windows Servidor 2016 com Windows Containers VM no Azure) sem mencionar um orquestrador inteiro como Kubernetes in Azure (AKS) que é, por outro lado, uma ótima escolha para implantações de produção.

Como conclusão principal, o uso do Azure Container Instances é uma opção muito atraente para cenários de Dev/Teste e para pipelines de CI/CD.

## <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais aprofundado na wiki do GitHub:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Passo a passo 5: implante seus aplicativos baseados em contêineres do Windows para kubernetes no Serviço de Contêineres Azure

### <a name="technical-walkthrough-availability"></a>Disponibilidade técnica do passo a passo

O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Visão geral

Um aplicativo baseado em Contêineres Windows precisará rapidamente usar plataformas, afastando-se ainda mais das VMs IaaS. Isso é necessário para alcançar facilmente alta escalabilidade e melhor escalabilidade automatizada, e para uma melhoria significativa nas implantações e versões automatizadas. Você pode alcançar esses objetivos usando o orquestrador [Kubernetes](https://kubernetes.io/), disponível no [Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Metas

O objetivo deste passo a passo é aprender a implantar um aplicativo baseado em contêiner do Windows no Kubernetes (também chamado *k8s)* no Azure Container Service. Implantar no Kubernetes a partir do zero é um processo de duas etapas:

1. Implante um cluster Kubernetes para o Serviço de Contêineres Do Azure.

2. Implante o aplicativo e os recursos relacionados ao cluster Kubernetes.

### <a name="scenarios"></a>Cenários

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Cenário A: Implante diretamente em um cluster Kubernetes a partir de um ambiente de vérme

![Implante diretamente em um cluster Kubernetes a partir de um ambiente de desenvolvimento](./media/image5-7.png)

**Figura 5-7.** Implante diretamente em um cluster Kubernetes a partir de um ambiente de desenvolvimento

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Cenário B: Implantar em um cluster Kubernetes a partir de gasodutos CI/CD nos Serviços Azure DevOps

![Implantar em um cluster Kubernetes a partir de pipelines CI/CD nos Serviços Azure DevOps](./media/image5-8.png)

**Figura 5-8.** Implantar em um cluster Kubernetes a partir de pipelines CI/CD nos Serviços Azure DevOps

### <a name="benefits"></a>Benefícios

Há muitos benefícios para implantar em um cluster em Kubernetes. O maior benefício é que você obtenha um ambiente pronto para a produção no qual você pode dimensionar o aplicativo com base no número de instâncias de contêiner que deseja usar (escalabilidade interna nos ádeis existentes) e com base no número de nódulos ou VMs no cluster ( escalabilidade global do cluster).

O Azure Container Service otimiza as populares ferramentas e tecnologias de código aberto especificamente para o Azure. Você recebe uma solução aberta que oferece portabilidade, tanto para seus contêineres quanto para a configuração do seu aplicativo. Você seleciona o tamanho, o número de hosts e o orchestrator tools-Container Service lida com todo o resto.

Com o Kubernetes, os desenvolvedores podem progredir desde pensar em máquinas físicas e virtuais, até planejar uma infra-estrutura centrada em contêineres que facilite os seguintes recursos, entre outros:

- Aplicações baseadas em vários contêineres

- Replicando instâncias de contêiner e autodimensionamento horizontal

- Nomeação e descoberta (por exemplo, DNS interno)

- Equilibrando cargas

- Atualizações de rolamento

- Distribuindo segredos

- Verificações de saúde de aplicativos

## <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais aprofundado na wiki do GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Passo a passo 6: implante seus aplicativos baseados em contêineres do Windows para o Serviço de Aplicativos do Azure para Contêineres

### <a name="technical-walkthrough-availability"></a>Disponibilidade técnica do passo a passo

O passo a passo técnico completo está disponível no eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Visão geral

Um aplicativo simples contêiner usando o Windows Containers pode ser facilmente implantado no Azure App Service for Containers. Esta é a abordagem recomendada para a maioria dos aplicativos baseados em contêiner do Windows.

### <a name="goals"></a>Metas

O objetivo deste passo a passo é aprender como implantar um aplicativo baseado em contêiner do Windows no Azure App Service for Containers a partir de um registro (Docker Hub ou Azure Container Registry).

### <a name="scenario"></a>Cenário

![Implantar aplicativo baseado em contêiner do Windows para o serviço de aplicativos do Azure para contêineres](./media/image5-11.png)

### <a name="benefits"></a>Benefícios

A implantação do Azure App Service for Containers oferece os benefícios dos contêineres associados aos benefícios paaS do Azure App Service. O serviço de aplicativo pode ser facilmente dimensionado tanto verticalmente quanto horizontalmente, e pode ser configurado em escala automática para atender às demandas em mudança. As atualizações podem ser realizadas com zero tempo de inatividade e a configuração da implantação contínua de um registro também é facilmente configurada.

## <a name="next-steps"></a>Próximas etapas

Explore este conteúdo mais aprofundado na wiki do GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Próximo](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [anterior](conclusions.md) <!-- Next Chapter -->
