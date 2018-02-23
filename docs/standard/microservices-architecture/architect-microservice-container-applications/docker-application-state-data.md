---
title: Estado e dados em aplicativos do Docker
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Estado e dados em aplicativos do Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner, SQL, CosmosDB, Docker"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ef11d89c39ee02d52dab29f949d1ac6be981d87f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="state-and-data-in-docker-applications"></a>Estado e dados em aplicativos do Docker

Na maioria dos casos, você pode considerar um contêiner uma instância de um processo. Um processo não mantém o estado persistente. Enquanto um contêiner pode gravar em seu armazenamento local, supondo que uma instância permanecerá indefinidamente seria como presumir que um único local na memória será durável. Deve-se supor que imagens de contêiner, assim como processos, têm várias instâncias ou que serão eventualmente eliminadas. Se forem gerenciadas com um orquestrador de contêineres, deve-se presumir que podem ser movidas de um nó ou VM para outra.

O Docker oferece um recurso chamado *sistema de arquivos de sobreposição*. Ele implementa uma tarefa de cópia em gravação que armazena informações atualizadas no sistema de arquivos de raiz do contêiner. Essas informações são adicionais à imagem original na qual o contêiner se baseia. Se o contêiner for excluído do sistema, essas alterações serão perdidas. Portanto, embora seja possível salvar o estado de um contêiner em seu armazenamento local, criar um sistema com base nisso entraria em conflito com o local do projeto do contêiner, que por padrão é sem estado.

As soluções a seguir são usadas para gerenciar dados persistentes em aplicativos do Docker:

-   [Volumes de dados](https://docs.docker.com/engine/tutorials/dockervolumes/) que remontam ao host.

-   [Contêineres de volume de dados](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) que fornecem armazenamento compartilhado em vários contêineres usando um contêiner externo.

-   [Plug-ins de volume](https://docs.docker.com/engine/tutorials/dockervolumes/) que montam volumes para serviços remotos, fornecendo a persistência de longo prazo.

-   [Armazenamento do Azure](https://docs.microsoft.com/azure/storage/), que oferece armazenamento geograficamente distribuído, fornecendo uma boa solução de persistência de longo prazo para contêineres.

-   Bancos de dados relacionais remotos, como [Banco de Dados SQL do Azure](https://azure.microsoft.com/services/sql-database/); bancos de dados NoSQL, como o [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction); ou serviços de cache, como o [Redis](https://redis.io/).

O exemplo a seguir fornece mais detalhes sobre essas opções.

**Volumes de dados** são diretórios mapeados do sistema operacional do host para diretórios em contêineres. Quando o código no contêiner tem acesso ao diretório, o acesso é, na verdade, a um diretório no sistema operacional host. Esse diretório não está vinculado ao tempo de vida do contêiner em si e pode ser acessado pelo código executado diretamente no sistema operacional host ou por outro contêiner, que mapeia o mesmo diretório do host para si mesmo. Assim, os volumes de dados são projetados para persistir dados independentemente do tempo de vida do contêiner. Se você excluir um contêiner ou uma imagem do host do Docker, os dados persistentes no volume de dados não serão excluídos. Os dados em um volume podem ser acessados do sistema operacional do host também.

**Contêineres de volume de dados** são uma evolução de volumes de dados regulares. Um contêiner de volume de dados é um contêiner simples que tem um ou mais volumes de dados nele. O contêiner de volume de dados dá acesso aos contêineres de um ponto de montagem central. Esse método de acesso a dados é conveniente, porque abstrai o local dos dados originais. Além disso, seu comportamento é semelhante ao de um volume de dados regular, então, os dados são persistidos nesse contêiner dedicado independentemente do ciclo de vida dos contêineres do aplicativo.

Conforme mostrado na Figura 4-5, os volumes Docker regulares podem ser armazenados fora dos contêineres de si, mas dentro dos limites físicos do servidor host ou VM. No entanto, contêineres do Docker não podem acessar um volume de um servidor host ou VM para outro. Em outras palavras, com esses volumes, não é possível gerenciar os dados compartilhados entre contêineres executados em diferentes hosts do Docker.

![](./media/image5.png)

**Figura 4-5**. Volumes de dados e fontes de dados externas para aplicativos baseados em contêiner

Além disso, quando gerenciados por um orquestrador, contêineres do Docker podem se "mover" entre os hosts de acordo com as otimizações realizadas pelo cluster. Portanto, não é recomendável usar volumes de dados para dados de negócios. Porém, eles são um bom mecanismo para trabalhar com arquivos de rastreamento, arquivos temporais ou similares que não afetarão a consistência dos dados de negócios.

**Plug-ins de volume** como o [Flocker](https://clusterhq.com/flocker/) dão acesso a dados em todos os hosts em um cluster. Embora nem todos os plug-ins de volume sejam criados igualmente, normalmente eles fornecem armazenamento externo persistente confiável de contêineres imutáveis.

**Fontes de dados remotas e ferramentas de cache** como o Banco de Dados SQL do Azure, o Azure Cosmos DB ou um cache remoto como o Redis podem ser usados em aplicativos em contêineres da mesma forma que são usados durante o desenvolvimento sem contêineres. Essa é uma forma comprovada de armazenar dados de aplicativo de negócios.

**Armazenamento do Azure.** Os dados de negócios geralmente precisarão ser colocados em recursos ou em bancos de dados externos, como o Armazenamento do Azure. O Armazenamento do Azure fornece os seguintes serviços na nuvem:

-   O Armazenamento de Blobs armazena dados de objeto não estruturados. Um blob pode ser qualquer tipo de texto ou dados binários, como documentos ou arquivos de mídia (imagens, áudio e vídeo). O Armazenamento de Blobs também é conhecido como armazenamento de objeto.

-   O armazenamento de arquivos oferece armazenamento compartilhado para aplicativos herdados que usam protocolo SMB padrão. Os serviços de nuvem e as máquinas virtuais do Azure podem compartilhar dados de arquivos em vários componentes de aplicativo por meio de compartilhamentos montados. Aplicativos locais podem acessar dados de arquivo em um compartilhamento por meio da API REST do serviço de arquivo.

-   O Armazenamento de Tabelas armazena conjuntos de dados estruturados. O Armazenamento de Tabelas é um armazenamento de dados do atributo-chave NoSQL, que permite o rápido desenvolvimento e acesso a grandes quantidades de dados.

**Bancos de dados relacionais e bancos de dados NoSQL.** Há muitas opções de bancos de dados externos, de bancos de dados relacionais, como SQL Server, PostgreSQL, Oracle ou bancos de dados NoSQL, como Azure Cosmos DB, MongoDB, etc. Esses bancos de dados não serão explicados neste guia, pois estão em um tópico completamente diferente.


>[!div class="step-by-step"]
[Anterior] (containerize-monolithic-applications.md) [Próximo] (service-oriented-architecture.md)
