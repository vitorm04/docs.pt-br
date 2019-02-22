---
title: Terminologia do Docker
description: Aprenda a terminologia básica que tenha usado todos os dias, ao trabalhar com o Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: a7f0106eed81c28634a079ce61f48d7d56f6ffd2
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584194"
---
# <a name="docker-terminology"></a>Terminologia do Docker

Esta seção lista os termos e definições que você deve conhecer antes de se aprofundar no Docker. Para obter mais definições, consulte o amplo [glossário](https://docs.docker.com/glossary/) fornecido pelo Docker.

**Imagem de contêiner**: Um pacote com todas as dependências e informações necessárias para criar um contêiner. Uma imagem inclui todas as dependências (como estruturas), além da configuração de implantação e execução a ser usada por um tempo de execução de contêiner. Geralmente, uma imagem deriva de várias imagens base que são camadas empilhadas umas sobre as outras para formar o sistema de arquivos do contêiner. Uma imagem é imutável depois de ser criada.

**Dockerfile**: Um arquivo de texto que contém instruções sobre como criar uma imagem do Docker. É como um script em lotes, a primeira linha declara a imagem base para começar com e, em seguida, siga as instruções para instalar os programas necessários, copiar arquivos, e assim por diante, até que você obtenha o ambiente de trabalho que você precisa.

**Build**: A ação de criação de uma imagem de contêiner com base nas informações e no contexto fornecidos pelo Dockerfile, além de arquivos adicionais na pasta em que a imagem é criada. Você pode criar imagens com o Docker **`docker build`** comando.

**Contêiner**: Uma instância de uma imagem do Docker. Um contêiner representa a execução de um único aplicativo, processo ou serviço. Consiste no conteúdo de uma imagem do Docker, um ambiente de execução e um conjunto padrão de instruções. Ao dimensionar um serviço, você cria várias instâncias de um contêiner da mesma imagem. Ou um trabalho em lotes pode criar vários contêineres da mesma imagem, passando parâmetros diferentes para cada instância.

**Volumes**: Oferecem um sistema de arquivos gravável que pode ser usado pelo contêiner. Uma vez que as imagens são somente leitura, mas a maioria dos programas precisam gravar para o sistema de arquivos, os volumes adicionam uma camada gravável sobre a imagem de contêiner, de modo que os programas têm acesso a um sistema de arquivos gravável. O programa não sabe que está acessando um sistema de arquivos em camadas, é apenas o sistema de arquivos como de costume. Os volumes ficam no sistema de host e são gerenciados pelo Docker.

**Tag**: Uma marca ou um rótulo que pode ser aplicado a imagens, de modo que as diferentes imagens ou versões da mesma imagem (dependendo do número de versão ou do ambiente de destino) possam ser identificadas.

**Build de vários estágios**: É uma funcionalidade disponível no Docker 17.05 ou posterior que ajuda a reduzir o tamanho das imagens finais. Em algumas frases, com o build de vários estágios você pode usar, por exemplo, uma imagem base grande contendo o SDK para compilar e publicar o aplicativo e, em seguida, usar a pasta de publicação com uma pequena imagem base somente de tempo de execução para produzir uma imagem final muito menor

**Repositório**: Uma coleção de imagens do Docker relacionadas, rotuladas com uma tag que indica a versão da imagem. Alguns repositórios contêm diversas variantes de uma imagem específica, como uma imagem que contém o SDKs (mais pesada), uma imagem que contém somente tempos de execução (mais leves) etc. Essas variantes podem ser marcadas com marcas. Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows.

**Registro**: Um serviço que fornece acesso aos repositórios. O registro padrão para as imagens mais públicas é o [Docker Hub](https://hub.docker.com/) (propriedade da Docker como uma organização). Um registro geralmente contém repositórios de várias equipes. As empresas geralmente têm registros privados para armazenar e gerenciar as imagens que criaram. O Registro de Contêiner do Azure é outro exemplo.

**Imagem de vários arcos**: Para arquitetura de várias é um recurso que simplifica a seleção da imagem apropriada, de acordo com a plataforma onde Docker está em execução, por exemplo, quando um Dockerfile solicita uma imagem de base **`FROM microsoft/dotnet:2.1-sdk`** do registro Na verdade, ele obtém **`2.1-sdk-nanoserver-1709`**, **`2.1-sdk-nanoserver-1803`** ou **`2.1-sdk-alpine`**, dependendo do sistema operacional e versão em que o Docker está sendo executado.

**Hub do Docker**: Um registro público para fazer upload de imagens e trabalhar com elas. O Docker Hub hospeda imagens do Docker, registros públicos ou privados, cria gatilhos e ganchos da Web e integra-se com o GitHub e o Bitbucket.

**Registro de Contêiner do Azure**: Um recurso público para trabalhar com imagens do Docker e seus componentes no Azure. Fornece um registro que está perto de suas implantações no Azure e que permite controlar o acesso, tornando possível usar as permissões e os grupos do Azure Active Directory.

**DTR (Registro Confiável do Docker)**: Um serviço de registro do Docker (do Docker) que pode ser instalado localmente, de modo que ele resida no datacenter e na rede da organização. É conveniente para imagens privadas que devem ser gerenciadas dentro da empresa. O Docker Trusted Registry é parte do produto Docker Datacenter. Para saber mais, consulte [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/).

**Docker CE (Community Edition)**: Ferramentas de desenvolvimento para Windows e macOS para criação, execução e teste de contêineres localmente. O Docker CE para Windows fornece os ambientes de desenvolvimento para Linux e contêineres do Windows. O host do Docker do Linux no Windows é baseado em uma máquina virtual [Hyper-V](https://www.microsoft.com/cloud-platform/server-virtualization). O host para contêineres do Windows se baseia diretamente no Windows. Docker CE para Mac baseia-se na estrutura do Apple Hypervisor e o [xhyve hypervisor](https://github.com/mist64/xhyve), que fornece uma máquina virtual do host Linux Docker no Mac OS X. O Docker CE para Windows e Mac substitui o Docker Toolbox, que foi baseado no Oracle VirtualBox.

**Docker EE (Enterprise Edition)**: Uma versão empresarial das ferramentas do Docker para desenvolvimento no Linux e no Windows.

**Compose**: Uma ferramenta de linha de comando e formato de arquivo YAML com metadados para definir e executar aplicativos de vários contêineres. Você define um único aplicativo com base em várias imagens com um ou mais arquivos .yml que podem substituir valores dependendo do ambiente. Depois de criar as definições, você pode implantar todo o aplicativo de vários contêineres com um único comando (docker-compose up), que cria um contêiner por imagem no host do Docker.

**Cluster**: Uma coleção de hosts do Docker expostos como um único host virtual do Docker, de modo que o aplicativo possa ser dimensionado para várias instâncias dos serviços distribuídos em vários hosts do cluster. Os clusters do Docker podem ser criados com o Kubernetes, o Azure Service Fabric, o Docker Swarm e o Mesosphere DC/OS.

**Orchestrator**: Uma ferramenta que simplifica o gerenciamento de clusters e hosts do Docker. Os orquestradores permitem gerenciar suas imagens, contêineres e hosts por meio de uma interface de linha de comando (CLI) ou uma interface do usuário gráfica. É possível gerenciar a rede de contêiner, configurações, balanceamento de carga, descoberta de serviço, alta disponibilidade, configuração de host do Docker e muito mais. Um orquestrador é responsável por executar, distribuir, dimensionar e reparar de cargas de trabalho em uma coleção de nós. Normalmente, produtos de orquestrador são os mesmos que fornecem infraestrutura de cluster, como Kubernetes e Azure Service Fabric, além de outras ofertas no mercado.

>[!div class="step-by-step"]
>[Anterior](what-is-docker.md)
>[Próximo](docker-containers-images-and-registries.md)