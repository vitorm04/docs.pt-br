---
title: Estado e os dados em aplicativos de Docker
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Estado e os dados em aplicativos de Docker"
keywords: "Docker, Microservices, ASP.NET, contêiner, SQL, CosmosDB, Docker"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 36d0fb9f27ef56b36c380e2fc972c79cff77003e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="state-and-data-in-docker-applications"></a>Estado e os dados em aplicativos de Docker

Na maioria dos casos, você pode pensar um contêiner como uma instância de um processo. Um processo não mantém o estado persistente. Enquanto um contêiner pode gravar em seu armazenamento local, supondo que uma instância será em torno indefinidamente seria como supondo que um único local na memória sejam durável. Imagens de contêiner, como processos, devem ser assumidas para ter várias instâncias, ou eles eventualmente serão eliminados; Se eles são gerenciados com o orchestrator um contêiner, deve-se assumir que eles podem obter movidos de um nó ou de VM para outra.

O docker fornece um recurso chamado de *sobreposição de sistema de arquivos*. Isso implementa uma tarefa de cópia na gravação que armazena informações atualizadas ao sistema de arquivos raiz do contêiner. Essas informações além disso são a imagem original no qual se baseia o contêiner. Se o contêiner é excluído do sistema, essas alterações serão perdidas. Portanto, embora seja possível salvar o estado de um contêiner dentro de seu armazenamento local, criando um sistema isso entraria em conflito com o local do projeto do contêiner, que por padrão é sem monitoração de estado.

As soluções a seguir são usadas para gerenciar dados persistentes em aplicativos de Docker:

-   [Volumes de dados](https://docs.docker.com/engine/tutorials/dockervolumes/) que montar para o host.

-   [Contêineres de volume de dados](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) que fornecem armazenamento compartilhado em vários contêineres usando um contêiner externo.

-   [Plug-ins do volume](https://docs.docker.com/engine/tutorials/dockervolumes/) que montar volumes para os serviços remotos, fornecendo a persistência de longo prazo.

-   [Armazenamento do Azure](https://docs.microsoft.com/azure/storage/), que fornece armazenamento geograficamente distribuídos, fornecendo uma boa solução de persistência de longo prazo para contêineres.

-   Bancos de dados relacionais remotos como [banco de dados do SQL Azure](https://azure.microsoft.com/services/sql-database/) ou bancos de dados NoSQL, como [banco de dados do Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/introduction), ou serviços, como armazenar em cache [Redis](https://redis.io/).

O exemplo a seguir fornece mais detalhes sobre essas opções.

**Volumes de dados** são mapeados do sistema operacional do host para diretórios em contêineres de diretórios. Quando o código no contêiner tem acesso ao diretório, que o acesso é, na verdade, um diretório no sistema operacional host. Este diretório não está vinculado ao tempo de vida do contêiner em si e o diretório pode ser acessado pelo código executado diretamente no sistema operacional host ou por outro contêiner, que mapeia o mesmo diretório do host a mesmo. Assim, os volumes de dados são projetados para persistir dados independentemente da vida útil do contêiner. Se você excluir um contêiner ou uma imagem de host do Docker, os dados persistentes no volume de dados não é excluído. Os dados em um volume podem ser acessados do host de sistema operacional também.

**Contêineres de volume de dados** são uma evolução de volumes de dados regulares. Um contêiner de volume de dados é um contêiner simple que tem um ou mais volumes de dados nele. O contêiner de volume de dados fornece acesso aos contêineres de um ponto de montagem central. Esse método de acesso a dados é conveniente, porque ele abstrai o local dos dados originais. Além disso, seu comportamento é semelhante de um volume de dados regulares, para que dados são persistidos neste contêiner dedicado independentemente do ciclo de vida de contêineres do aplicativo.

Conforme mostrado na Figura 4-5, os volumes Docker regulares podem ser armazenados fora os contêineres de si, mas dentro dos limites físicos do servidor host ou máquina virtual. No entanto, contêineres do Docker não podem acessar um volume do servidor de um host ou máquina virtual para outro. Em outras palavras, com esses volumes, não é possível gerenciar os dados compartilhados entre contêineres que são executados em diferentes hosts de Docker

![](./media/image5.png)

**Figura 4-5**. Volumes de dados e fontes de dados externas para aplicativos baseados no contêiner

Além disso, quando gerenciados por um orquestrador de contêineres do Docker, contêineres podem "Mover" entre os hosts, dependendo de otimizações executadas pelo cluster. Portanto, não é recomendável que você use volumes de dados para dados de negócios. Mas eles são um bom mecanismo para trabalhar com arquivos de rastreamento, arquivos temporal, ou semelhante que não afetará a consistência dos dados de negócios.

**Plug-ins do volume** como [Flocker](https://clusterhq.com/flocker/) fornecer acesso a dados em todos os hosts em um cluster. Embora nem todos os plug-ins de volume são criados igualmente, plug-ins do volume normalmente fornecem externalizado armazenamento confiável persistente de contêineres imutáveis.

**Fontes de dados remotas e cache** ferramentas como o banco de dados do SQL Azure, o banco de dados do Azure Cosmos ou um cache remoto como o Redis pode ser usado em contêineres aplicativos da mesma forma que eles são usados durante o desenvolvimento sem contêineres. Isso é uma forma de armazenar dados de aplicativo de negócios.

**Armazenamento do Azure.** Dados corporativos geralmente precisa ser colocado em recursos externos ou bancos de dados, como o armazenamento do Azure. Armazenamento do Azure, no concreto, fornece os seguintes serviços na nuvem:

-   Armazenamento de blob armazena dados de objeto não estruturados. Um blob pode ser qualquer tipo de dados de texto ou binário, como documentos ou mídia de arquivos (imagens, áudio e vídeo). Armazenamento de blob também é chamado como armazenamento de objeto.

-   Armazenamento de arquivos oferece armazenamento compartilhado para aplicativos herdados que usam protocolo SMB padrão. Serviços de nuvem e máquinas virtuais do Azure podem compartilhar dados de arquivo entre componentes de aplicativos por meio de compartilhamentos montados. Aplicativos locais podem acessar dados de arquivo em um compartilhamento via o API REST do serviço de arquivo.

-   Armazenamento de tabela armazena conjuntos de dados estruturados. Armazenamento de tabela é um repositório de dados do atributo de chave NoSQL, que permite o rápido desenvolvimento e acesso rápido a grandes quantidades de dados.

**Bancos de dados relacionais e bancos de dados NoSQL.** Há muitas opções para bancos de dados externos, de bancos de dados relacionais, como bancos de dados NoSQL, PostgreSQL, Oracle ou SQL Server como banco de dados do Azure Cosmos, MongoDB, etc. Esses bancos de dados não vai ser explicado como parte deste guia, desde que eles estão em um assunto completamente diferente.


>[!div class="step-by-step"]
[Anterior] (coloca-monolítico-applications.md) [Avançar] (service-orientado-architecture.md)
