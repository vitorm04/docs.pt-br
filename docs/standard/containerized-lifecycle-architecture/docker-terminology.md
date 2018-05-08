---
title: Terminologia do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 7a8ec2233b7927c1e3f85f5a3536a889a6a55e22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="docker-terminology"></a>Terminologia do Docker

Esta seção lista os termos e definições com a qual você deve se familiarizar antes de investigar mais profunda Docker (para obter mais definições, consulte o amplo [glossário](https://docs.docker.com/glossary/) fornecida pelo Docker em <https://docs.docker.com/glossary/>:

-   **Imagem de contêiner** um pacote com todas as dependências e as informações necessárias para criar um contêiner. Uma imagem inclui todas as dependências (como estruturas) além de implantação e configuração a ser usada por um tempo de execução do contêiner. Geralmente, uma imagem deriva de várias imagens de base que são camadas empilhadas um sobre o outro para formar o sistema de arquivos do contêiner. Uma imagem é imutável depois que ela foi criada.

-   **Contêiner** uma instância de uma imagem do Docker. Um contêiner representa um tempo de execução para um único aplicativo, processo ou serviço. Ele consiste no conteúdo de uma imagem do Docker, um ambiente de tempo de execução e um conjunto padrão de instruções. Ao dimensionar um serviço, você cria várias instâncias de um contêiner da mesma imagem. Ou então, um trabalho em lotes pode criar vários contêineres da mesma imagem, passando parâmetros diferentes para cada instância.

-   **Marca** uma marca ou um rótulo que você pode aplicar a imagens para que podem ser identificadas diferentes imagens ou versões da mesma imagem (dependendo do número de versão ou o ambiente de destino).

-   **Dockerfile** um arquivo de texto que contém instruções sobre como criar uma imagem do Docker.

-   **Criar** a ação de criação de uma imagem de contêiner com base nas informações e contexto fornecido pela sua Dockerfile, bem como arquivos adicionais na pasta em que a imagem é criada. Você pode criar imagens usando o comando de compilação de docker do Docker.

-   **Repositório (também conhecido como repositório)** uma coleção de imagens do Docker relacionadas rotulado com uma marca que indica a versão da imagem. Alguns repositórios contêm várias variantes de uma imagem específica, como uma imagem que contém o SDKs (mais), uma imagem que contém somente tempos de execução (mais leves), e assim por diante. Essas variantes podem ser marcadas com marcas. Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.

-   **Registro** um serviço que fornece acesso aos repositórios. O registro padrão para as imagens mais públicas é o [Docker Hub](https://hub.docker.com/) (propriedade da Docker como uma organização). Um registro geralmente contém repositórios de várias equipes. As empresas geralmente têm registros privados para armazenar e gerenciar imagens que criaram. *Registro de contêiner do Azure* é outro exemplo.

-   **Hub do docker** um registro público para carregar imagens e trabalhar com eles. O Docker Hub hospeda imagens do Docker, registros públicos ou privados, cria gatilhos e ganchos da Web e integra-se com o GitHub e o Bitbucket.

-   **Registro de contêiner do Azure** um recurso público para trabalhar com imagens do Docker e seus componentes no Azure. Fornece um registro que está perto de suas implantações no Azure e que permite controlar o acesso, tornando possível usar as permissões e os grupos do Azure Active Directory.

-   **Docker confiáveis do registro (DTR)** serviço de registro de Docker de um (a partir do Docker) que podem ser instalados no local para que ela reside no datacenter e a rede da organização. É conveniente para imagens privadas que devem ser gerenciadas dentro da empresa. O Docker Trusted Registry é parte do produto Docker Datacenter. Para obter mais informações, vá para [ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/).

-   **Docker Community Edition (CE)** ferramentas de desenvolvimento para Windows e macOS para compilar, executar e testar contêineres localmente. O Docker CE para Windows fornece os ambientes de desenvolvimento para Linux e contêineres do Windows. O host do Docker do Linux no Windows é baseado em um [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM. O host para contêineres do Windows se baseia diretamente no Windows. Docker CE para Mac baseia-se na estrutura do hipervisor da Apple e a [xhyve hipervisor](https://github.com/mist64/xhyve), que fornece uma VM do host do Linux Docker no Mac OS X. Docker CE para Windows e Mac substitui a caixa de ferramentas do Docker, que é baseado em VirtualBox Oracle.

-   **Docker Enterprise Edition (EE)** uma versão de grande porte das ferramentas do Docker para desenvolvimento Linux e Windows.

-   **Compor** uma ferramenta de linha de comando e YAML formato com metadados para definir e executar aplicativos multicontainer de arquivo. Você define um único aplicativo com base em várias imagens com um ou mais arquivos .yml que podem substituir valores dependendo do ambiente. Depois que você criou as definições, você pode implantar o aplicativo multicontainer inteiro usando um único comando (docker-compor backup) que cria um contêiner por imagem no host do Docker.

-   **Cluster** uma coleção de hosts de Docker expostas como se fossem um único host virtual do Docker para que o aplicativo pode ser dimensionado para várias instâncias dos serviços distribuídos em vários hosts do cluster. Você pode criar clusters do Docker usando o Docker Swarm, Mesosphere DC/OS, Kubernetes e Azure Service Fabric. (Ao usar o Docker Swarm para gerenciar um cluster, você normalmente se referirá ao cluster como um *swarm* em vez de um cluster.)

-   **Orchestrator** uma ferramenta que simplifica o gerenciamento de clusters e hosts de Docker. Usando orchestrators, você pode gerenciar suas imagens, contêineres e hosts por meio de uma CLI ou uma interface gráfica do usuário. É possível gerenciar a rede de contêiner, configurações, balanceamento de carga, descoberta de serviço, alta disponibilidade, configuração de host do Docker e muito mais. Um orquestrador é responsável por executar, distribuir, dimensionar e reparar de cargas de trabalho em uma coleção de nós. Normalmente, produtos de orquestrador são os mesmos que fornecem infraestrutura de cluster, como Mesosphere DC/OS, Kubernetes, Docker Swarm e Azure Service Fabric.


>[!div class="step-by-step"]
[Anterior] (e-for-docker.md) [Avançar] (docker-contêineres-imagens-e-registries.md)
