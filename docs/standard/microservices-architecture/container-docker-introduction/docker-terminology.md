---
title: Terminologia de docker
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Terminologia de docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 885b1fbd3369dec54ebde21a5378630c764f852d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="docker-terminology"></a>Terminologia de docker

Esta seção lista os termos e definições que você deve se familiarizar antes de obter maior no Docker. Para obter mais definições, consulte o amplo [glossário](https://docs.docker.com/v1.11/engine/reference/glossary/) fornecida pelo Docker.

**Imagem de contêiner**: um pacote com todas as dependências e as informações necessárias para criar um contêiner. Uma imagem inclui todas as dependências (como estruturas) além de implantação e execução de configuração a ser usada por um tempo de execução do contêiner. Geralmente, uma imagem é derivado de várias imagens de base são empilhadas uns sobre os outros para formar o sistema de arquivos do contêiner de camadas. Uma imagem é imutável depois que ela foi criada.

**Contêiner**: uma instância de uma imagem do Docker. Um contêiner representa a execução de um único aplicativo, processo ou serviço. Ele consiste no conteúdo de uma imagem do Docker, um ambiente de execução e um conjunto padrão de instruções. Ao dimensionar um serviço, você cria várias instâncias de um contêiner da mesma imagem. Ou um trabalho em lotes pode criar vários contêineres da mesma imagem, passando parâmetros diferentes para cada instância.

**Marca**: uma marca ou um rótulo, você pode aplicar a imagens para que podem ser identificadas diferentes imagens ou versões da mesma imagem (dependendo do número de versão ou o ambiente de destino).

**Dockerfile**: um arquivo de texto que contém instruções sobre como criar uma imagem do Docker.

**Criar**: A ação de criação de uma imagem de contêiner com base nas informações e contexto fornecido pelo seu Dockerfile, além de arquivos adicionais na pasta em que a imagem é criada. Você pode criar imagens com o comando de compilação de docker do Docker.

**Repositório (repositório)**: uma coleção de imagens relacionadas do Docker, rotulado com uma marca que indica a versão da imagem. Alguns repositórios contêm várias variantes de uma imagem específica, como uma imagem que contém o SDKs (mais), uma imagem que contém somente tempos de execução (mais leves), etc. Essas variantes podem ser marcadas com marcas. Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.

**Registro**: um serviço que fornece acesso aos repositórios. O registro padrão para as imagens mais públicas está [Docker Hub](https://hub.docker.com/) (propriedade Docker como uma organização). Um registro geralmente contém repositórios de várias equipes. As empresas geralmente têm registros privados para armazenar e gerenciar as imagens que você criou. Registro de contêiner do Azure é outro exemplo.

**Hub do docker**: um registro público para carregar imagens e trabalhar com eles. Hub do docker fornece Docker hospedagem de imagem, registros públicos ou privados, gatilhos de compilação e ganchos web e integração com o GitHub, Bitbucket.

**Registro de contêiner do Azure**: um recurso público para trabalhar com imagens do Docker e seus componentes no Azure. Isso fornece um registro que está perto de suas implantações no Azure e que fornece a você controle sobre o acesso, tornando possível usar suas permissões e grupos do Active Directory do Azure.

**Docker confiáveis do registro (DTR)**: serviço de registro de Docker de um (a partir do Docker) que pode ser instalado localmente para que ela reside no datacenter e a rede da organização. É conveniente para imagens privadas que devem ser gerenciadas dentro da empresa. Registro confiável do docker é incluído como parte do produto Docker Datacenter. Para obter mais informações, consulte [Docker confiável do registro (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker Community Edition (CE)**: ferramentas de desenvolvimento para Windows e macOS para compilar, executar e testar contêineres localmente. CE do docker para Windows fornece os ambientes de desenvolvimento para Linux e contêineres do Windows. O host do Docker do Linux no Windows é baseado em um [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) máquina virtual. O host para contêineres do Windows baseia-se diretamente no Windows. Docker CE para Mac baseia-se na estrutura do hipervisor da Apple e a [xhyve hipervisor](https://github.com/mist64/xhyve), que fornece uma máquina virtual do host Linux Docker no Mac OS X. Docker CE para Windows e Mac substitui a caixa de ferramentas do Docker, que é baseado no Oracle VirtualBox.

**Docker Enterprise Edition (EE)**: uma versão de grande porte das ferramentas do Docker para desenvolvimento Linux e Windows.

**Compor**: uma ferramenta de linha de comando e YAML formato com metadados para definir e executar aplicativos de vários contêiner de arquivo. Você define um único aplicativo com base em várias imagens com um ou mais arquivos de .yml que podem substituir valores dependendo do ambiente. Depois que você criou as definições, você pode implantar o aplicativo inteiro vários contêiner com um único comando (docker-compor backup) que cria um contêiner por imagem no host do Docker.

**Cluster**: uma coleção de hosts de Docker expostos como se fosse um único host Docker virtual, para que o aplicativo pode ser dimensionado para várias instâncias dos serviços distribuídos em vários hosts do cluster. Clusters de docker podem ser criados com o Docker Swarm, Mesosphere DC/OS, Kubernetes e Azure Service Fabric. (Se você usar o Docker Swarm para gerenciar um cluster, você normalmente se referir ao cluster como um *swarm* em vez de um cluster.)

**Orchestrator**: uma ferramenta que simplifica o gerenciamento de clusters e hosts de Docker. Orchestrators permitem gerenciar suas imagens, contêineres e hosts por meio de uma interface de linha de comando (CLI) ou uma interface de usuário gráfica. Você pode gerenciar a rede de contêiner, configurações, balanceamento de carga, descoberta de serviço, alta disponibilidade, configuração de host do Docker e muito mais. Um orquestrador é responsável por executar, distribuir, escala e reparo de cargas de trabalho em uma coleção de nós. Normalmente, orchestrator produtos são o mesmo que fornecem infraestrutura de cluster, como Mesosphere DC/OS, Kubernetes, Docker Swarm e Azure Service Fabric.


>[!div class="step-by-step"]
[Anterior] (docker-defined.md) [Avançar] (docker-contêineres-imagens-registries.md)
