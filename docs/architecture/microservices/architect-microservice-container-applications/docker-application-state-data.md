---
title: Estado e dados em aplicativos do Docker
description: Gerenciamento de dados e de estado em aplicativos do Docker. Instâncias de Microsserviços são descartáveis, mas os DADOS NÃO O SÃO, como lidar com isso com microsserviços.
ms.date: 09/20/2018
ms.openlocfilehash: bd0ac007479dcd51f2c639881273b81d1fd8b6d7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039589"
---
# <a name="state-and-data-in-docker-applications"></a>Estado e dados em aplicativos do Docker

Na maioria dos casos, você pode considerar um contêiner uma instância de um processo. Um processo não mantém o estado persistente. Enquanto um contêiner pode gravar em seu armazenamento local, supondo que uma instância permanecerá indefinidamente seria como presumir que um único local na memória será durável. Você deve presumir que as imagens de contêiner, assim como os processos, têm várias instâncias ou serão eventualmente eliminadas. Se forem gerenciadas com um orquestrador de contêineres, você deverá presumir que podem ser movidas de um nó ou VM para outro.

As soluções a seguir são usadas para gerenciar dados persistentes em aplicativos do Docker:

Do host do Docker, como [Volumes do Docker](https://docs.docker.com/engine/admin/volumes/):

- **Volumes** são armazenados em uma área do sistema de arquivos de host que é gerenciado pelo Docker.

- **Montagens de associação** podem mapear para qualquer pasta no sistema de arquivos de host, portanto, o acesso não pode ser controlado do processo do Docker e pode representar um risco de segurança, já que um contêiner pode acessar pastas confidenciais do sistema operacional.

- **Montagens tmpfs** são como pastas virtuais que só existem na memória do host e nunca são gravadas no sistema de arquivos.

Do armazenamento remoto:

- [Armazenamento do Azure](https://azure.microsoft.com/documentation/services/storage/), que oferece armazenamento geograficamente distribuído, fornecendo uma boa solução de persistência de longo prazo para contêineres.

- Bancos de dados relacionais remotos, como [Banco de Dados SQL do Azure](https://azure.microsoft.com/services/sql-database/); bancos de dados NoSQL, como o [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction); ou serviços de cache, como o [Redis](https://redis.io/).

Do contêiner do Docker:

> O Docker oferece um recurso chamado *sistema de arquivos de sobreposição*. Ele implementa uma tarefa de cópia em gravação que armazena informações atualizadas no sistema de arquivos de raiz do contêiner. Essas informações são adicionais à imagem original na qual o contêiner se baseia. Se o contêiner for excluído do sistema, essas alterações serão perdidas. Portanto, embora seja possível salvar o estado de um contêiner em seu armazenamento local, criar um sistema com base nisso entraria em conflito com o local do projeto do contêiner, que por padrão é sem estado.
>
> No entanto, os volumes do Docker anteriormente introduzidos agora são a maneira preferencial para manipulação de dados locais com o Docker. Se você precisar de mais informações sobre o armazenamento em contêineres, procure em [Drivers de armazenamento do Docker](https://docs.docker.com/storage/storagedriver/select-storage-driver/) e [Sobre drivers de armazenamento](https://docs.docker.com/storage/storagedriver/).

O exemplo a seguir fornece mais detalhes sobre essas opções:

**Volumes** são diretórios mapeados do sistema operacional do host para diretórios em contêineres. Quando o código no contêiner tem acesso ao diretório, o acesso é, na verdade, a um diretório no sistema operacional host. Esse diretório não está vinculado ao tempo de vida do contêiner em si, sendo que o diretório é gerenciado pelo Docker e isolado em relação à funcionalidade básica do computador host. Assim, os volumes de dados são projetados para persistir dados independentemente do tempo de vida do contêiner. Se você excluir um contêiner ou uma imagem do host do Docker, os dados persistentes no volume de dados não serão excluídos.

Volumes podem ser nomeados ou anônimos (o padrão). Volumes nomeados são a evolução dos **Contêineres de Volume de Dados** e facilitam o compartilhamento de dados entre contêineres. Volumes também dão suporte a drivers de volume, que permitem que você armazene dados em hosts remotos, entre outras opções.

**Montagens de associação** estão disponíveis há muito tempo e permitem o mapeamento de qualquer pasta para um ponto de montagem em um contêiner. Montagens de associação têm mais limitações que os volumes e alguns problemas de segurança importantes, por isso os volumes são a opção recomendada.

**Montagens tmpfs** são basicamente pastas virtuais que só existem na memória do host e nunca são gravadas no sistema de arquivos. Elas são rápidas e seguras, mas usam a memória e destinam-se somente a dados não persistentes.

Conforme mostrado na Figura 4-5, os volumes Docker regulares podem ser armazenados fora dos contêineres de si, mas dentro dos limites físicos do servidor host ou VM. No entanto, contêineres do Docker não podem acessar um volume de um servidor host ou VM para outro. Em outras palavras, com esses volumes, não é possível gerenciar os dados compartilhados entre contêineres executados em hosts diferentes do Docker, embora esses dados possam ser obtidos com um driver de volume que dá suporte a hosts remotos.

![Volumes podem ser compartilhados entre contêineres, mas apenas no mesmo host, a menos que você use um driver remoto que dá suporte a hosts remotos.](./media/image5.png)

**Figura 4-5**. Volumes e fontes de dados externas para aplicativos baseados em contêiner

Além disso, quando gerenciados por um orquestrador, contêineres do Docker podem se "mover" entre os hosts de acordo com as otimizações realizadas pelo cluster. Portanto, não é recomendável usar volumes de dados para dados empresariais. Porém, eles são um bom mecanismo para trabalhar com arquivos de rastreamento, arquivos temporais ou similares que não afetarão a consistência dos dados empresariais.

**Fontes de dados remotas e ferramentas de cache** como o Banco de Dados SQL do Azure, o Azure Cosmos DB ou um cache remoto como o Redis podem ser usados em aplicativos em contêineres da mesma forma que são usados durante o desenvolvimento sem contêineres. Essa é uma forma comprovada de armazenar dados de aplicativo de negócios.

**Armazenamento do Azure.** Os dados de negócios geralmente precisarão ser colocados em recursos ou em bancos de dados externos, como o Armazenamento do Azure. O Armazenamento do Azure fornece os seguintes serviços na nuvem:

- O Armazenamento de Blobs armazena dados de objeto não estruturados. Um blob pode ser qualquer tipo de texto ou dados binários, como documentos ou arquivos de mídia (imagens, áudio e vídeo). O Armazenamento de Blobs também é conhecido como armazenamento de objeto.

- O armazenamento de arquivos oferece armazenamento compartilhado para aplicativos herdados que usam protocolo SMB padrão. Os serviços de nuvem e as máquinas virtuais do Azure podem compartilhar dados de arquivos em vários componentes de aplicativo por meio de compartilhamentos montados. Aplicativos locais podem acessar dados de arquivo em um compartilhamento por meio da API REST do serviço de arquivo.

- O Armazenamento de Tabelas armazena conjuntos de dados estruturados. O Armazenamento de Tabelas é um armazenamento de dados do atributo-chave NoSQL, que permite o rápido desenvolvimento e acesso a grandes quantidades de dados.

**Bancos de dados relacionais e bancos de dados NoSQL.** Há muitas opções de bancos de dados externos, de bancos de dados relacionais, como SQL Server, PostgreSQL, Oracle ou bancos de dados NoSQL, como Azure Cosmos DB, MongoDB, etc. Esses bancos de dados não serão explicados neste guia, pois estão em um tópico completamente diferente.

>[!div class="step-by-step"]
>[Anterior](containerize-monolithic-applications.md)
>[Próximo](service-oriented-architecture.md)
