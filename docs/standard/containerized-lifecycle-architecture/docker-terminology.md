---
title: Terminologia do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 1efb2fa567bd452f0a0a5ee5afb6f759511e4145
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151298"
---
# <a name="docker-terminology"></a>Terminologia do Docker

Esta seção lista os termos e definições com os quais você deve se familiarizar com antes de nos aprofundarmos mais profundo no Docker (para obter mais definições, consulte o amplo [glossário](https://docs.docker.com/glossary/) fornecido pelo Docker em <https://docs.docker.com/glossary/>:

-   **Imagem de contêiner** um pacote com todas as dependências e as informações necessárias para criar um contêiner. Uma imagem inclui todas as dependências (como estruturas) além de implantação e configuração a ser usada por um tempo de execução do contêiner. Geralmente, uma imagem deriva de várias imagens base que são camadas empilhadas uma sobre a outra para formar o sistema de arquivos do contêiner. Uma imagem é imutável depois de ele ter sido criado.

-   **Contêiner** uma instância de uma imagem do Docker. Um contêiner representa um tempo de execução para um único aplicativo, processo ou serviço. Ele consiste no conteúdo de uma imagem do Docker, um ambiente de tempo de execução e um conjunto padrão de instruções. Ao dimensionar um serviço, você cria várias instâncias de um contêiner da mesma imagem. Ou, um trabalho em lotes pode criar vários contêineres da mesma imagem, passando parâmetros diferentes para cada instância.

-   **Marca** uma marca ou um rótulo que você pode aplicar às imagens para que possam ser identificadas imagens diferentes ou versões da mesma imagem (dependendo do número de versão ou o ambiente de destino).

-   **Dockerfile** um arquivo de texto que contém instruções sobre como criar uma imagem do Docker.

-   **Build** a ação de criação de uma imagem de contêiner com base nas informações e contexto fornecidos pelo seu Dockerfile, bem como arquivos adicionais na pasta em que a imagem é criada. Você pode criar imagens usando o comando docker build do Docker.

-   **Repositório (Também conhecido como repo)** uma coleção de imagens Docker relacionadas, rotulada com uma tag que indica a versão da imagem. Alguns repositórios contêm diversas variantes de uma imagem específica, como uma imagem que contém os SDKs (mais pesadas), uma imagem que contém somente tempos de execução (mais leves), e assim por diante. Essas variantes podem ser marcadas com tags. Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.

-   **Registro** um serviço que fornece acesso aos repositórios. O registro padrão para as imagens mais públicas é o [Docker Hub](https://hub.docker.com/) (propriedade da Docker como uma organização). Um registro geralmente contém repositórios de várias equipes. As empresas geralmente têm registros privados para armazenar e gerenciar imagens criados por eles. *O registro de contêiner do Azure* é outro exemplo.

-   **Docker Hub** um registro público para carregar imagens e trabalhar com elas. O Docker Hub hospeda imagens do Docker, registros públicos ou privados, cria gatilhos e ganchos da Web e integra-se com o GitHub e o Bitbucket.

-   **O Registro de Contêiner do Azure** um recurso público para trabalhar com imagens do Docker e seus componentes no Azure. Fornece um registro que está perto de suas implantações no Azure e que permite controlar o acesso, tornando possível usar as permissões e os grupos do Azure Active Directory.

-   **Docker Trusted Registry (DTR)** serviço de registro (a partir do Docker) que podem ser instalados no local, de modo que ele reside no datacenter e rede da organização. É conveniente para imagens privadas que devem ser gerenciadas dentro da empresa. O Docker Trusted Registry é parte do produto Docker Datacenter. Para obter mais informações, acesse [ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** ferramentas de desenvolvimento para Windows e macOS para compilar, executar e testar contêineres localmente. O Docker CE para Windows fornece os ambientes de desenvolvimento para Linux e contêineres do Windows. O host do Docker do Linux no Windows se baseia em uma [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM. O host para contêineres do Windows se baseia diretamente no Windows. Docker CE para Mac baseia-se na estrutura do Apple Hypervisor e o [xhyve hypervisor](https://github.com/mist64/xhyve), que fornece uma VM do host Linux Docker no Mac OS X. Docker CE para Windows e Mac substitui o Docker Toolbox, que foi baseado no Oracle VirtualBox.

-   **Docker Enterprise Edition (EE)** uma versão empresarial das ferramentas do Docker para o desenvolvimento de Linux e Windows.

-   **Compose** uma ferramenta de linha de comando e formato de arquivo YAML com metadados para definir e executar aplicativos de vários contêineres. Você define um único aplicativo com base em várias imagens com um ou mais arquivos .yml que podem substituir valores dependendo do ambiente. Depois que cria as definições, você pode implantar todo o aplicativo de vários contêineres por meio de um único comando (docker-compose) que cria um contêiner por imagem no host do Docker.

-   **Cluster** uma coleção de hosts do Docker expostos como se fossem um único host virtual para que o aplicativo pode ser dimensionado para várias instâncias dos serviços espalhadas em vários hosts no cluster. Você pode criar clusters do Docker usando o Docker Swarm, Mesosphere DC/OS, Kubernetes e Service Fabric do Azure. (Ao usar o Docker Swarm para gerenciar um cluster, você normalmente se referirá ao cluster como um *swarm* em vez de um cluster.)

-   **Orchestrator** uma ferramenta que simplifica o gerenciamento de clusters e hosts do Docker. Usando orquestradores, você pode gerenciar suas imagens, contêineres e hosts por meio de uma CLI ou uma interface gráfica do usuário. É possível gerenciar a rede de contêiner, configurações, balanceamento de carga, descoberta de serviço, alta disponibilidade, configuração de host do Docker e muito mais. Um orquestrador é responsável por executar, distribuir, dimensionar e reparar de cargas de trabalho em uma coleção de nós. Normalmente, produtos de orquestrador são os mesmos que fornecem infraestrutura de cluster, como Mesosphere DC/OS, Kubernetes, Docker Swarm e Azure Service Fabric.

>[!div class="step-by-step"]
>[Anterior](what-is-docker.md)
>[Próximo](docker-containers-images-and-registries.md)
