---
title: Como aproveitar contêineres e orquestradores
description: Aproveitando contêineres docker e orquestradores kubernetes em Azure
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989032"
---
# <a name="leveraging-containers-and-orchestrators"></a>Como aproveitar contêineres e orquestradores

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Contêineres e orquestradores são projetados para resolver problemas comuns a abordagens de implantação monolítica.

## <a name="challenges-with-monolithic-deployments"></a>Desafios com implantações monolíticas

Tradicionalmente, a maioria dos aplicativos foram implantados como uma única unidade. Tais aplicações são referidas como um monólito. Esta abordagem geral de implantar aplicativos como unidades únicas, mesmo que sejam compostas de múltiplos módulos ou conjuntos, é conhecida como arquitetura monolítica, como mostrado na Figura 3-1.

![Arquitetura monolítica.](./media/monolithic-architecture.png)

**Figura 3-1**. Arquitetura monolítica.

Embora tenham o benefício da simplicidade, as arquiteturas monolíticas enfrentam uma série de desafios:

### <a name="deployments"></a>Implantações

A implantação em aplicações monolíticas normalmente requer reiniciar toda a aplicação, mesmo que apenas um pequeno módulo esteja sendo substituído. Dependendo do número de máquinas que hospedam o aplicativo, isso pode resultar em tempo de inatividade durante as implantações.

### <a name="hosting"></a>Hosting

As aplicações monolíticas estão hospedadas inteiramente em uma única instância de máquina. Isso pode exigir hardware de maior capacidade do que qualquer módulo em um aplicativo distribuído precisaria. Além disso, se qualquer parte do aplicativo se tornar um gargalo, todo o aplicativo deve ser implantado em outros nós de máquina, a fim de dimensionar.

### <a name="environment"></a>Ambiente

As aplicações monolíticas são normalmente implantadas em um ambiente de hospedagem existente (sistema operacional, frameworks instalados, etc.). Este ambiente pode não corresponder ao ambiente em que a aplicação foi desenvolvida ou testada. Inconsistências no ambiente do aplicativo são uma fonte comum de problemas para implantações monolíticas.

### <a name="coupling"></a>Acoplamento

É provável que as aplicações monolíticas tenham uma grande quantidade de acoplamento entre diferentes partes da aplicação e entre a aplicação e seu ambiente. Isso pode dificultar a fatoração de um determinado serviço ou preocupação mais tarde, a fim de aumentar sua escalabilidade ou troca em uma implementação alternativa. Esse acoplamento também leva a impactos potenciais muito maiores para mudanças no sistema, exigindo testes extensivos em aplicações maiores.

### <a name="technology-choice"></a>Escolha da tecnologia

Aplicações monolíticas são construídas e implantadas como uma unidade. Isso oferece simplicidade e uniformidade, mas pode ser uma barreira à inovação. Embora um novo recurso ou módulo no sistema possa ser mais adequado para uma plataforma ou estrutura mais moderna, é provável que ele seja construído usando a abordagem atual do aplicativo por uma questão de consistência, bem como facilidade de desenvolvimento e implantação.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Quais são os benefícios dos contêineres e orquestradores?

Docker é a plataforma de gerenciamento e imagem de contêineres mais popular e permite que você trabalhe rapidamente com contêineres no Linux e Windows. Os contêineres fornecem ambientes de aplicação separados, mas reprodutíveis, que funcionam da mesma maneira em qualquer sistema. Isso os torna perfeitos para desenvolver e hospedar aplicativos e componentes de aplicativos em aplicativos nativos da nuvem. Os contêineres são isolados um do outro, então dois contêineres no mesmo hardware host podem ter versões diferentes de software e até mesmo sistema operacional instalado, sem que as dependências causem conflitos.

Além disso, os contêineres são definidos por arquivos simples que podem ser verificados no controle de origem. Ao contrário dos servidores completos, até mesmo das máquinas virtuais, que frequentemente exigem trabalho manual para aplicar atualizações ou instalar serviços adicionais, a infra-estrutura de contêineres pode ser facilmente controlada por versão. Assim, os aplicativos construídos para serem executados em contêineres podem ser desenvolvidos, testados e implantados usando ferramentas automatizadas como parte de um pipeline de construção.

Os recipientes são imutáveis. Uma vez que você tenha a definição de um contêiner, você pode recriar esse recipiente e ele será executado exatamente da mesma maneira. Essa imutabilidade se presta ao design baseado em componentes. Se algumas partes de um aplicativo não mudam com tanta frequência quanto outras, por que reimplantar todo o aplicativo quando você pode simplesmente implantar as peças que mudam com mais freqüência? Diferentes recursos e preocupações transversais de um aplicativo podem ser divididos em unidades separadas. A Figura 3-2 mostra como um aplicativo monolítico pode tirar proveito de contêineres e microsserviços, delegando certos recursos ou funcionalidades. A funcionalidade restante no próprio aplicativo também foi contêiner.

![Quebrando um aplicativo monolítico para usar microsserviços na parte traseira. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Figura 3-2**. Quebrando um aplicativo monolítico para usar microsserviços na parte traseira.

Aplicativos nativos da nuvem construídos usando contêineres separados se beneficiam da capacidade de implantar tanto ou tão pouco de um aplicativo quanto necessário. Serviços individuais podem ser hospedados em nós com recursos apropriados para cada serviço. O ambiente em que cada serviço é executado é imutável, pode ser compartilhado entre desenvolvimento, teste e produção, e pode ser facilmente versão. O acoplamento entre diferentes áreas do aplicativo ocorre explicitamente como chamadas ou mensagens entre serviços, não compilar-tempo dependências dentro do monólito. E qualquer parte do aplicativo global pode escolher a tecnologia que faz mais sentido para esse recurso ou capacidade sem exigir alterações para o resto do aplicativo.

## <a name="what-are-the-scaling-benefits"></a>Quais são os benefícios de dimensionamento?

Serviços construídos em contêineres podem aproveitar os benefícios de dimensionamento fornecidos por ferramentas de orquestração como kubernetes. Por design, os contêineres só sabem sobre si mesmos. Uma vez que você começa a ter vários contêineres que precisam trabalhar juntos, pode valer a pena organizá-los em um nível mais alto. Organizar um grande número de contêineres e suas dependências compartilhadas, como a configuração da rede, é onde as ferramentas de orquestração entram para salvar o dia! Kubernetes é uma plataforma de orquestração de contêineres projetada para automatizar a implantação, o dimensionamento e o gerenciamento de aplicativos contêineres. Ele cria uma camada de abstração em cima de grupos de contêineres e organiza-os em *pods*. Pods executados em máquinas de trabalhadores referidos como *nódulos*. Todo o grupo organizado é chamado de *cluster*. A figura 3-3 mostra os diferentes componentes de um cluster Kubernetes.

![Componentes de cluster Kubernetes. ](./media/kubernetes-cluster-components.png)
 **Figura 3-3**. Componentes de cluster Kubernetes.

A Kubernetes tem suporte integrado para clusters de dimensionamento para atender à demanda. Combinado com microserviços contêineres, isso fornece aos aplicativos nativos da nuvem a capacidade de responder de forma rápida e eficiente a picos de demanda com recursos adicionais quando e onde eles são necessários.

### <a name="declarative-versus-imperative"></a>Declarativo versus imperativo

Kubernetes suporta a configuração de objeto declarativo e imperativo. A abordagem imperativa envolve executar vários comandos que dizem aos Kubernetes o que fazer a cada passo do caminho. *Execute* esta imagem. *Apague* essa cápsula. *Exponha* essa porta. Com a abordagem declarativa, você usa um arquivo de configuração que descreve *o que você quer* em vez do que *fazer* e kubernetes descobre o que fazer para alcançar o estado final desejado. Se você já configurou seu cluster usando comandos imperativos, você `kubectl get svc SERVICENAME -o yaml > service.yaml`pode exportar um manifesto declarativo usando . Isso produzirá um arquivo manifesto como este:

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

Ao usar a configuração declarativa, você pode visualizar as `kubectl diff -f FOLDERNAME` alterações que serão feitas antes de cometê-las usando contra a pasta onde seus arquivos de configuração estão localizados. Uma vez que você tenha certeza de `kubectl apply -f FOLDERNAME`que deseja aplicar as alterações, execute . Adicione `-R` para processar recursivamente uma hierarquia de pastas.

Além dos serviços, você pode usar configuração declarativa para outros recursos do Kubernetes, como *implantações.* Implantações declarativas são usadas por controladores de implantação para atualizar recursos de cluster. As implantações são usadas para implementar novas alterações, escalar para suportar mais carga ou reverter para uma revisão anterior. Se um cluster for instável, as implantações declarativas fornecem um mecanismo para trazer automaticamente o cluster de volta ao estado desejado.

O uso da configuração declarativa permite que a infra-estrutura seja representada como código que pode ser verificado e versionado junto com o código do aplicativo. Isso fornece melhor controle de alterações e melhor suporte para implantação contínua usando um pipeline de compilação e implantação vinculado a alterações de controle de origem.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Que cenários são ideais para contêineres e orquestradores?

Os seguintes cenários são ideais para o uso de contêineres e orquestradores.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplicações que exigem alto tempo de atividade e escalabilidade

Aplicações individuais que têm alto tempo de atividade e requisitos de escalabilidade são candidatos ideais para arquiteturas nativas da nuvem usando microsserviços, contêineres e orquestradores. Essas aplicações podem ser desenvolvidas em recipientes usando ambientes versados, podem ser extensivamente testadas antes de ir para a produção e podem ser implantadas para a produção sem tempo de inatividade. O uso de clusters Kubernetes garante que esses aplicativos também possam escalar sob demanda e se recuperar automaticamente de falhas no nó.

### <a name="large-numbers-of-applications"></a>Grande número de aplicações

As organizações que implantam e devem, posteriormente, manter um grande número de aplicativos se beneficiam de contêineres e orquestradores. O esforço inicial de criação de ambientes contêineres e clusters Kubernetes é principalmente um custo fixo. A implantação, manutenção e atualização de aplicativos individuais tem um custo que varia de acordo com o número de aplicativos que devem ser mantidos. Além de um certo número bastante pequeno de aplicativos, a complexidade de manter aplicativos personalizados excede manualmente o custo de implementação de uma solução usando contêineres e orquestradores.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Quando você deve evitar o uso de recipientes e orquestradores?

Se você não está disposto ou não pode construir seu aplicativo seguindo os princípios do Aplicativo De Doze Fatores, provavelmente será melhor evitar contêineres e orquestradores. Nesses casos, talvez seja melhor avançar com uma plataforma de hospedagem baseada em VM, ou possivelmente algum sistema híbrido no qual você pode girar certas peças de funcionalidade em recipientes separados ou até funções sem servidor.

## <a name="development-resources"></a>Recursos de desenvolvimento

Esta seção mostra uma pequena lista de recursos de desenvolvimento que podem ajudá-lo a começar a usar contêineres e orquestradores para sua próxima aplicação. Se você está procurando orientação sobre como projetar seu aplicativo de arquitetura de microsserviços nativo na nuvem, leia o companheiro deste livro, [.NET Microservices: Architecture for Containerized .NET Applications](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Desenvolvimento local de Kubernetes

As implantações do Kubernetes fornecem grande valor em ambientes de produção, mas você também pode executá-los localmente. Embora na maior parte do tempo seja bom poder trabalhar em aplicativos individuais ou microsserviços de forma independente, às vezes é bom ser capaz de executar todo o sistema localmente, assim como ele será executado quando implantado na produção. Existem várias maneiras de conseguir isso, duas das quais são Minikube e Docker Desktop. O Visual Studio também fornece ferramentas para o desenvolvimento do Docker.

### <a name="minikube"></a>Minikube

O que é Minikube? O projeto Minikube diz que "o Minikube implementa um cluster Kubernetes local no macOS, Linux e Windows.". Seus objetivos principais são "ser a melhor ferramenta para o desenvolvimento de aplicativos kubernetes locais e apoiar todos os recursos kubernetes que se encaixam". A instalação do Minikube é separada do Docker, mas o Minikube suporta hipervisores diferentes dos suportes do Docker Desktop. Os seguintes recursos do Kubernetes são atualmente suportados pela Minikube:

- DNS
- Portos de Nó
- ConfigMaps e segredos
- Painéis
- Tempos de execução de contêineres: Docker, rkt, CRI-O e containerd
- Habilitando a Interface da Rede de Contêineres (CNI)
- Entrada

Depois de instalar o Minikube, você pode `minikube start` começar a usá-lo rapidamente executando o comando, que baixa uma imagem e inicia o cluster Kubernetes local. Uma vez iniciado o cluster, você interage com `kubectl` ele usando os comandos Kubernetes padrão.

### <a name="docker-desktop"></a>Docker Desktop

Você também pode trabalhar com Kubernetes diretamente do Docker Desktop no Windows. Esta é a sua única opção se você estiver usando o Windows Containers, e é uma ótima escolha para contêineres não-Windows também. O aplicativo de configuração padrão do Docker Desktop é usado para configurar kubernetes rodando a partir do Docker Desktop.

![Configuração de Kubernetes no Docker Desktop](./media/docker-desktop-kubernetes.png)

**Figura 3-4**. Configurando Kubernetes no Docker Desktop.

O Docker Desktop já é a ferramenta mais popular para configurar e executar aplicativos contêiner localmente. Quando você trabalha com o Docker Desktop, você pode desenvolver localmente contra o mesmo conjunto de imagens de contêiner Docker que você implantará para a produção. O Docker Desktop foi projetado para "construir, testar e enviar" aplicativos contêiner localmente. Uma vez que as imagens tenham sido enviadas para um registro de imagens como o Azure Container Registry ou o Docker Hub, serviços como o Azure Kubernetes Service (AKS) gerenciam o aplicativo em produção.

### <a name="visual-studio-docker-tooling"></a>Ferramentas do Visual Studio Docker

O Visual Studio suporta o desenvolvimento do Docker para aplicações web. Quando você cria um novo aplicativo ASP.NET Core, você tem a opção de configurá-lo com suporte ao Docker como parte do processo de criação de projetos, como mostrado na Figura 3-5.

![Visual Studio habilitar suporte docker](./media/visual-studio-enable-docker-support.png)

**Figura 3-5**. Visual Studio habilitar suporte docker

Quando essa opção é selecionada, o `Dockerfile` projeto é criado com um em sua raiz, que pode ser usado para construir e hospedar o aplicativo em um contêiner Docker. Um exemplo de Arquivo Docker é mostrado na Figura 3-6.

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

**Figura 3-6**. Visual Studio gerou Dockerfile

O comportamento padrão quando o aplicativo é executado é configurado para usar o Docker também. A Figura 3-7 mostra as diferentes opções de execução disponíveis a partir de um novo projeto ASP.NET Core criado com suporte ao Docker adicionado.

![Opções de execução do Visual Studio Docker](./media/visual-studio-docker-run-options.png)

**Figura 3-7**. Opções de execução do Visual Studio Docker

Além do desenvolvimento local, [o Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) fornece uma maneira conveniente para vários desenvolvedores trabalharem com suas próprias configurações de Kubernetes dentro do Azure. Como você pode ver na Figura 3-7, você também pode executar o aplicativo no Azure Dev Spaces.

Se você não adicionar suporte ao Docker ao seu aplicativo ASP.NET Core ao criá-lo, você sempre poderá adicioná-lo mais tarde. No Visual Studio Solution Explorer, clique com o botão direito do mouse no projeto e selecione **Adicionar** > **suporte ao Docker,** conforme mostrado na Figura 3-8.

![Visual Studio adiciona suporte ao Docker](./media/visual-studio-add-docker-support.png)

**Figura 3-8**. Visual Studio adiciona suporte ao Docker

Além do suporte ao Docker, você também pode adicionar suporte à orquestração de contêineres, também mostrado na Figura 3-8. Por padrão, o orquestrador usa Kubernetes e Helm. Depois de escolher o orquestrador, um `azds.yaml` arquivo é adicionado `charts` à raiz do projeto e uma pasta é adicionada contendo os gráficos Helm usados para configurar e implantar o aplicativo no Kubernetes. A Figura 3-9 mostra os arquivos resultantes em um novo projeto.

![Suporte ao Visual Studio Add Orchestrator](./media/visual-studio-add-orchestrator-support.png)

**Figura 3-9**. Suporte ao Visual Studio Add Orchestrator

## <a name="references"></a>Referências

- [O que é Kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalando Kubernetes com Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Ferramentas do Visual Studio para Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Próximo](scale-applications.md)
>[anterior](leverage-serverless-functions.md)
