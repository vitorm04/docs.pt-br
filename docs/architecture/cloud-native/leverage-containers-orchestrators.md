---
title: Como aproveitar contêineres e orquestradores
description: Aproveitando contêineres do Docker e orquestradores kubernetes no Azure
ms.date: 06/30/2019
ms.openlocfilehash: 62aaa68b2ada0725f33df62e97f1ca3216b91ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315885"
---
# <a name="leveraging-containers-and-orchestrators"></a>Como aproveitar contêineres e orquestradores

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Contêineres e orquestradores são projetados para resolver problemas comuns a abordagens de implantação monolítica.

## <a name="challenges-with-monolithic-deployments"></a>Desafios com implantações monolíticos

Tradicionalmente, a maioria dos aplicativos foi implantada como uma única unidade. Esses aplicativos são chamados de monolíticos. Essa abordagem geral de implantação de aplicativos como unidades únicas, mesmo se eles são compostos por vários módulos ou assemblies, é conhecida como arquitetura monolítica, como mostra a Figura 3-1.

![Arquitetura monolítica.](./media/monolithic-architecture.png)

**Figura 3-1**. Arquitetura monolítica.

Embora eles tenham o benefício da simplicidade, as arquiteturas monolíticos enfrentam vários desafios:

### <a name="deployments"></a>Implantações

A implantação em aplicativos monolíticos normalmente requer a reinicialização do aplicativo inteiro, mesmo que apenas um módulo pequeno esteja sendo substituído. Dependendo do número de máquinas que hospedam o aplicativo, isso pode resultar em tempo de inatividade durante as implantações.

### <a name="hosting"></a>Hospedagem

Os aplicativos monolíticos são hospedados inteiramente em uma única instância de computador. Isso pode exigir um hardware de maior capacidade do que qualquer módulo em um aplicativo distribuído precisaria. Além disso, se qualquer parte do aplicativo se tornar um afunilamento, o aplicativo inteiro deverá ser implantado em nós de computador adicionais para que possa escalar horizontalmente.

### <a name="environment"></a>Ambiente

Os aplicativos monolíticos normalmente são implantados em um ambiente de hospedagem existente (sistema operacional, estruturas instaladas, etc.). Esse ambiente pode não corresponder ao ambiente no qual o aplicativo foi desenvolvido ou testado. Inconsistências no ambiente do aplicativo são uma fonte comum de problemas para implantações monolíticos.

### <a name="coupling"></a>Acoplamento

Os aplicativos monolíticos provavelmente terão uma grande quantidade de acoplamento entre diferentes partes do aplicativo e entre o aplicativo e seu ambiente. Isso pode dificultar a retirada de um determinado serviço ou de uma preocupação mais tarde, a fim de aumentar sua escalabilidade ou trocar em uma implementação alternativa. Esse acoplamento também leva a um grande impacto potencial para as alterações no sistema, exigindo testes extensivos em aplicativos maiores.

### <a name="technology-choice"></a>Opção de tecnologia

Os aplicativos monolíticos são criados e implantados como uma unidade. Isso oferece simplicidade e uniformidade, mas pode ser uma barreira à inovação. Embora um novo recurso ou módulo no sistema possa ser mais adequado para uma plataforma ou estrutura mais moderna, é provável que seja criado usando a abordagem atual do aplicativo para fins de consistência, bem como para facilitar o desenvolvimento e a implantação.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Quais são os benefícios de contêineres e orquestradores?

O Docker é a plataforma de gerenciamento de contêineres e de geração de imagens mais popular e permite que você trabalhe rapidamente com contêineres no Linux e no Windows. Os contêineres fornecem ambientes de aplicativos separados, mas reproduzíveis, que são executados da mesma maneira em qualquer sistema. Isso os torna perfeitos para desenvolver e hospedar aplicativos e componentes de aplicativo em aplicativos nativos de nuvem. Os contêineres são isolados uns dos outros, de modo que dois contêineres no mesmo hardware de host podem ter versões diferentes do software e até mesmo do sistema operacional instalado, sem as dependências que causam conflitos.

E mais, os contêineres são definidos por arquivos simples que podem ser verificados no controle do código-fonte. Ao contrário de servidores completos, até mesmo máquinas virtuais, que frequentemente exigem trabalho manual para aplicar atualizações ou instalar serviços adicionais, a infraestrutura de contêiner pode facilmente ser controlada por versão. Assim, os aplicativos criados para execução em contêineres podem ser desenvolvidos, testados e implantados usando ferramentas automatizadas como parte de um pipeline de compilação.

Os contêineres são imutáveis. Quando você tiver a definição de um contêiner, poderá recriar esse contêiner e ele será executado exatamente da mesma maneira. Essa imutabilidade se presta ao design baseado em componentes. Se algumas partes de um aplicativo não forem alteradas com frequência como outras, por que reimplantar todo o aplicativo quando você puder apenas implantar as partes que mudam com mais frequência? Diferentes recursos e preocupações abrangentes de um aplicativo podem ser divididos em unidades separadas. A Figura 3-2 mostra como um aplicativo monolítico pode aproveitar os contêineres e os microserviços delegando determinados recursos ou funcionalidades. A funcionalidade restante no aplicativo também foi contida em contêineres.

![Breaking um aplicativo monolítico para usar os microserviços no back-end. ](./media/breaking-up-monolith-with-backend-microservices.png)
**figura 3-2**. Dividir um aplicativo monolítico para usar os microserviços no back-end.

Os aplicativos nativos de nuvem criados usando contêineres separados beneficiam-se da capacidade de implantar o máximo ou o mínimo de um aplicativo, conforme necessário. Serviços individuais podem ser hospedados em nós com recursos apropriados para cada serviço. O ambiente em que cada serviço é executado é imutável, pode ser compartilhado entre desenvolvimento, teste e produção e pode ser facilmente com controle de versão. O acoplamento entre diferentes áreas do aplicativo ocorre explicitamente como chamadas ou mensagens entre serviços, não as dependências de tempo de compilação dentro do monolítico. E qualquer parte do aplicativo geral pode escolher a tecnologia que faz mais sentido para esse recurso ou recurso sem a necessidade de alterações no restante do aplicativo.

## <a name="what-are-the-scaling-benefits"></a>Quais são os benefícios de dimensionamento?

Os serviços criados nos contêineres podem aproveitar os benefícios de dimensionamento fornecidos pelas ferramentas de orquestração como o kubernetes. Os contêineres de design só sabem sobre si mesmos. Depois de começar a ter vários contêineres que precisam trabalhar juntos, pode valer a pena organizá-los em um nível mais alto. Organizar grandes números de contêineres e suas dependências compartilhadas, como a configuração de rede, é onde as ferramentas de orquestração entram para economizar o dia! O kubernetes é uma plataforma de orquestração de contêiner projetada para automatizar a implantação, o dimensionamento e o gerenciamento de aplicativos em contêineres. Ele cria uma camada de abstração sobre grupos de contêineres e os organiza em *pods*. O pods é executado em computadores de trabalho conhecidos como *nós*. O grupo organizado inteiro é conhecido como um *cluster*. A Figura 3-3 mostra os diferentes componentes de um cluster kubernetes.

![Kubernetes componentes de cluster. ](./media/kubernetes-cluster-components.png)
**figura 3-3**. Componentes do cluster kubernetes.

O kubernetes tem suporte interno para dimensionar clusters para atender à demanda. Combinado com micro-Services em contêineres, isso fornece aos aplicativos nativos de nuvem a capacidade de responder de forma rápida e eficiente a picos de demanda com recursos adicionais quando e onde eles são necessários.

### <a name="declarative-versus-imperative"></a>Declarativa versus imperativo

O kubernetes dá suporte à configuração de objeto declarativo e imperativo. A abordagem imperativa envolve a execução de vários comandos que dizem ao kubernetes o que fazer em cada etapa do caminho. *Executar* esta imagem. *Excluir* este Pod. *Expor* esta porta. Com a abordagem declarativa, você usa um arquivo de configuração que descreve *o que você deseja* em vez do *que fazer* e kubernetes descobre o que fazer para atingir o estado final desejado. Se você já tiver configurado o cluster usando comandos imperativos, poderá exportar um manifesto declarativo usando `kubectl get svc SERVICENAME -o yaml > service.yaml`. Isso produzirá um arquivo de manifesto como este:

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

Ao usar a configuração declarativa, você pode visualizar as alterações que serão feitas antes de confirmá-las usando `kubectl diff -f FOLDERNAME` em relação à pasta em que os arquivos de configuração estão localizados. Quando tiver certeza de que deseja aplicar as alterações, execute `kubectl apply -f FOLDERNAME`. Adicione `-R` para processar recursivamente uma hierarquia de pastas.

Além dos serviços, você pode usar a configuração declarativa para outros recursos do kubernetes, como *implantações*. Implantações declarativas são usadas por controladores de implantação para atualizar recursos de cluster. As implantações são usadas para distribuir novas alterações, escalar verticalmente para dar suporte a mais carga ou reverter para uma revisão anterior. Se um cluster estiver instável, as implantações declarativas fornecerão um mecanismo para colocar automaticamente o cluster de volta para um estado desejado.

O uso da configuração declarativa permite que a infraestrutura seja representada como código que pode ser verificado e com controle de versão junto com o código do aplicativo. Isso fornece um controle de alterações aprimorado e melhor suporte à implantação contínua usando um pipeline de compilação e implantação vinculado às alterações de controle do código-fonte.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Quais cenários são ideais para contêineres e orquestradores?

Os cenários a seguir são ideais para usar contêineres e orquestradores.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Aplicativos que exigem alto tempo de atividade e escalabilidade

Os aplicativos individuais que têm altos requisitos de tempo de atividade e escalabilidade são candidatos ideais para arquiteturas nativas de nuvem usando microservices, contêineres e orquestradores. Esses aplicativos podem ser desenvolvidos em contêineres usando ambientes com controle de versão, que podem ser extensivamente testados antes de passar para a produção e podem ser implantados para produção sem tempo de inatividade. O uso de clusters kubernetes garante que esses aplicativos também possam ser dimensionados sob demanda e recuperados automaticamente de falhas de nó.

### <a name="large-numbers-of-applications"></a>Grandes números de aplicativos

As organizações que implantam e devem posteriormente manter um grande número de aplicativos se beneficiam de contêineres e orquestradores. O esforço antecipado de configurar ambientes em contêineres e clusters kubernetes é, principalmente, um custo fixo. Implantar, manter e atualizar aplicativos individuais tem um custo que varia de acordo com o número de aplicativos que devem ser mantidos. Além de um certo número muito pequeno de aplicativos, a complexidade de manter aplicativos personalizados excede manualmente o custo da implementação de uma solução usando contêineres e orquestradores.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Quando você deve evitar o uso de contêineres e orquestradores?

Se você não estiver implantando ou não puder criar seu aplicativo seguindo os princípios de aplicativo de doze fatores, provavelmente será melhor evitar contêineres e orquestradores. Nesses casos, pode ser melhor seguir adiante com uma plataforma de hospedagem baseada em VM ou possivelmente um sistema híbrido no qual você possa fazer a rotação de determinadas partes de funcionalidade em contêineres separados ou mesmo em funções sem servidor. 

## <a name="development-resources"></a>Recursos de desenvolvimento

Esta seção mostra uma lista curta de recursos de desenvolvimento que podem ajudá-lo a começar a usar contêineres e orquestradores para seu próximo aplicativo. Se você estiver procurando orientação sobre como projetar seu aplicativo de arquitetura de microserviços nativos de nuvem, leia o complemento deste livro, [microservices .net: arquitetura para aplicativos .net em contêineres](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Desenvolvimento de kubernetes local

As implantações kubernetes fornecem um ótimo valor em ambientes de produção, mas você também pode executá-las localmente. Embora grande parte do tempo seja bom poder trabalhar em aplicativos individuais ou em microserviços de forma independente, às vezes é bom poder executar todo o sistema localmente, assim como ele será executado quando for implantado para produção. Há várias maneiras de fazer isso, duas das quais são Minikube e Docker desktop. O Visual Studio também fornece ferramentas para o desenvolvimento do Docker.

### <a name="minikube"></a>Minikube

O que é o Minikube? O projeto Minikube diz "Minikube implementa um cluster kubernetes local no macOS, Linux e Windows." Suas metas principais são "para ser a melhor ferramenta para o desenvolvimento de aplicativos kubernetes local e para dar suporte a todos os recursos do kubernetes que se ajustam". A instalação do Minikube é separada do Docker, mas o Minikube dá suporte a diferentes hipervisores do que o Docker desktop dá suporte. Atualmente, há suporte para os seguintes recursos de kubernetes pelo Minikube:

- DNS
- NodePorts
- ConfigMaps e segredos
- Painéis
- Tempos de execução de contêiner: Docker, RKT, CRI-O e em contêineres
- Habilitando o CNI (interface de rede de contêiner)
- Entrada

Depois de instalar o Minikube, você pode começar rapidamente a usá-lo executando o comando `minikube start`, que baixa uma imagem e inicia o cluster kubernetes local. Depois que o cluster é iniciado, você interage com ele usando os comandos kubernetes `kubectl` padrão.

### <a name="docker-desktop"></a>Área de trabalho do Docker

Você também pode trabalhar com kubernetes diretamente da área de trabalho do Docker no Windows. Essa é a única opção se você estiver usando contêineres do Windows e também é uma ótima opção para contêineres que não são do Windows. O aplicativo de configuração de área de trabalho do Docker padrão é usado para configurar o kubernetes em execução do Docker desktop.

![Configurando o kubernetes no Docker desktop](./media/docker-desktop-kubernetes.png)

**Figura 3-4**. Configurando o kubernetes no Docker desktop.

O Docker desktop já é a ferramenta mais popular para configurar e executar aplicativos em contêineres localmente. Ao trabalhar com o Docker desktop, você pode desenvolver localmente no mesmo conjunto de imagens de contêiner do Docker que você implantará na produção. O Docker desktop foi projetado para "Compilar, testar e enviar" aplicativos em contêineres localmente. Depois que as imagens forem enviadas para um registro de imagem, como o registro de contêiner do Azure ou o Hub do Docker, os serviços como o serviço kubernetes do Azure (AKS) gerenciarão o aplicativo em produção.

### <a name="visual-studio-docker-tooling"></a>Ferramentas do Docker do Visual Studio

O Visual Studio dá suporte ao desenvolvimento do Docker para aplicativos Web. Ao criar um novo aplicativo ASP.NET Core, você tem a opção de configurá-lo com o suporte do Docker como parte do processo de criação do projeto, como mostrado na Figura 3-5.

![Habilitar o suporte do Docker ao Visual Studio](./media/visual-studio-enable-docker-support.png)

**Figura 3-5**. Habilitar o suporte do Docker ao Visual Studio

Quando essa opção é selecionada, o projeto é criado com um `Dockerfile` em sua raiz, que pode ser usado para criar e hospedar o aplicativo em um contêiner do Docker. Um exemplo de Dockerfile é mostrado na Figura 3-6.

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

**Figura 3-6**. Dockerfile gerado pelo Visual Studio

O comportamento padrão quando o aplicativo é executado é configurado para usar o Docker também. A Figura 3-7 mostra as diferentes opções de execução disponíveis em um novo projeto ASP.NET Core criado com o suporte do Docker adicionado.

![Opções de execução do Docker do Visual Studio](./media/visual-studio-docker-run-options.png)

**Figura 3-7**. Opções de execução do Docker do Visual Studio

Além do desenvolvimento local, o [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) fornece uma maneira conveniente para vários desenvolvedores trabalharem com suas próprias configurações de kubernetes no Azure. Como você pode ver na Figura 3-7, você também pode executar o aplicativo em Azure Dev Spaces.

Se você não adicionar o suporte do Docker ao seu aplicativo ASP.NET Core ao criá-lo, você sempre poderá adicioná-lo mais tarde. No Gerenciador de Soluções do Visual Studio, clique com o botão direito do mouse no projeto e selecione **Adicionar** **suporte ao docker**de  > , conforme mostrado na Figura 3-8.

![Adicionar suporte ao Docker ao Visual Studio](./media/visual-studio-add-docker-support.png)

**Figura 3-8**. Adicionar suporte ao Docker ao Visual Studio

Além do suporte ao Docker, você também pode adicionar suporte à orquestração de contêiner, também mostrada na Figura 3-8. Por padrão, o orquestrador usa kubernetes e Helm. Depois de escolher o orquestrador, um arquivo `azds.yaml` é adicionado à raiz do projeto e uma pasta `charts` é adicionada contendo os gráficos do Helm usados para configurar e implantar o aplicativo no kubernetes. A Figura 3-9 mostra os arquivos resultantes em um novo projeto.

![Adicionar suporte ao Orchestrator no Visual Studio](./media/visual-studio-add-orchestrator-support.png)

**Figura 3-9**. Adicionar suporte ao Orchestrator no Visual Studio

## <a name="references"></a>Referências

- [O que é o kubernetes?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Instalando o kubernetes com Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [Área de trabalho do MiniKube vs Docker](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Ferramentas do Visual Studio para Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Anterior](scale-applications.md)
>[Próximo](leverage-serverless-functions.md)
