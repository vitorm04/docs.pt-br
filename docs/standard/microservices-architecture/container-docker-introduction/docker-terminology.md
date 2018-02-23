---
title: Terminologia do Docker
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Terminologia do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 342b4443470053d81534d4de1d56d2797798c746
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="docker-terminology"></a>Terminologia do Docker

Esta seção lista os termos e definições que você deve conhecer antes de se aprofundar no Docker. Para obter mais definições, consulte o amplo [glossário](https://docs.docker.com/glossary/) fornecido pelo Docker.

**Imagem de contêiner**: um pacote com todas as dependências e informações necessárias para criar um contêiner. Uma imagem inclui todas as dependências (como estruturas), além da configuração de implantação e execução a ser usada por um tempo de execução de contêiner. Geralmente, uma imagem deriva de várias imagens base que são camadas empilhadas umas sobre as outras para formar o sistema de arquivos do contêiner. Uma imagem é imutável depois de ser criada.

**Contêiner**: uma instância de uma imagem do Docker. Um contêiner representa a execução de um único aplicativo, processo ou serviço. Consiste no conteúdo de uma imagem do Docker, um ambiente de execução e um conjunto padrão de instruções. Ao dimensionar um serviço, você cria várias instâncias de um contêiner da mesma imagem. Ou um trabalho em lotes pode criar vários contêineres da mesma imagem, passando parâmetros diferentes para cada instância.

**Marcação**: uma marca ou um rótulo pode ser aplicado a imagens para que imagens ou versões diferentes da mesma imagem (dependendo do número de versão ou do ambiente de destino) possam ser identificadas.

**Dockerfile**: um arquivo de texto que contém instruções sobre como criar uma imagem do Docker.

**Build**: a ação de criar de uma imagem de contêiner com base nas informações e no contexto fornecido pelo Dockerfile, além de arquivos adicionais na pasta em que a imagem é criada. Você pode criar imagens com o comando de build do Docker.

**Repositório**: uma coleção de imagens do Docker relacionadas, rotulada com uma marcação que indica a versão da imagem. Alguns repositórios contêm diversas variantes de uma imagem específica, como uma imagem que contém o SDKs (mais pesada), uma imagem que contém somente tempos de execução (mais leves) etc. Essas variantes podem ser marcadas com marcas. Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.

**Registro**: um serviço que dá acesso aos repositórios. O registro padrão para as imagens mais públicas é o [Docker Hub](https://hub.docker.com/) (propriedade da Docker como uma organização). Um registro geralmente contém repositórios de várias equipes. As empresas geralmente têm registros privados para armazenar e gerenciar as imagens que criaram. O Registro de Contêiner do Azure é outro exemplo.

**Docker Hub**: um registro público para carregar imagens e trabalhar com elas. O Docker Hub hospeda imagens do Docker, registros públicos ou privados, cria gatilhos e ganchos da Web e integra-se com o GitHub e o Bitbucket.

**Registro de Contêiner do Azure**: um recurso público para trabalhar com imagens do Docker e seus componentes no Azure. Fornece um registro que está perto de suas implantações no Azure e que permite controlar o acesso, tornando possível usar as permissões e os grupos do Azure Active Directory.

**Docker Trusted Registry (DTR)**: serviço de registro do Docker que pode ser instalado localmente para funcionar no datacenter e na rede da organização. É conveniente para imagens privadas que devem ser gerenciadas dentro da empresa. O Docker Trusted Registry é parte do produto Docker Datacenter. Para saber mais, consulte [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: ferramentas de desenvolvimento para Windows e macOS para build, execução e teste de contêineres localmente. O Docker CE para Windows fornece os ambientes de desenvolvimento para Linux e contêineres do Windows. O host do Docker do Linux no Windows é baseado em uma máquina virtual [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx). O host para contêineres do Windows se baseia diretamente no Windows. Docker CE para Mac baseia-se na estrutura do Apple Hypervisor e o [xhyve hypervisor](https://github.com/mist64/xhyve), que fornece uma máquina virtual do host Linux Docker no Mac OS X. O Docker CE para Windows e Mac substitui o Docker Toolbox, que foi baseado no Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: uma versão empresarial das ferramentas do Docker para desenvolvimento em Linux e Windows.

**Compose**: uma ferramenta de linha de comando e formato de arquivo YAML com metadados para definir e executar aplicativos de vários contêineres. Você define um único aplicativo com base em várias imagens com um ou mais arquivos .yml que podem substituir valores dependendo do ambiente. Depois de criar as definições, você pode implantar todo o aplicativo de vários contêineres com um único comando (docker-compose up), que cria um contêiner por imagem no host do Docker.

**Cluster**: uma coleção de hosts do Docker expostos como um único host virtual, para que o aplicativo possa ser dimensionado para várias instâncias dos serviços distribuídos em vários hosts do cluster. Clusters do Docker podem ser criados com o Docker Swarm, Mesosphere DC/OS, Kubernetes e Azure Service Fabric. (Ao usar o Docker Swarm para gerenciar um cluster, você normalmente se referirá ao cluster como um *swarm* em vez de um cluster.)

**Orquestrador**: uma ferramenta que simplifica o gerenciamento de clusters e hosts do Docker. Os orquestradores permitem gerenciar imagens, contêineres e hosts por meio de uma CLI (interface de linha de comando) ou uma interface do usuário gráfica. É possível gerenciar a rede de contêiner, configurações, balanceamento de carga, descoberta de serviço, alta disponibilidade, configuração de host do Docker e muito mais. Um orquestrador é responsável por executar, distribuir, dimensionar e reparar de cargas de trabalho em uma coleção de nós. Normalmente, produtos de orquestrador são os mesmos que fornecem infraestrutura de cluster, como Mesosphere DC/OS, Kubernetes, Docker Swarm e Azure Service Fabric.


>[!div class="step-by-step"]
[Anterior] (docker-defined.md) [Próximo] (docker-containers-images-registries.md)
