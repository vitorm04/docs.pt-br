---
title: Estado e dados em aplicativos do Docker
description: Aprenda a opção disponível para salvar o estado em aplicativos em contêineres.
ms.date: 02/15/2019
ms.openlocfilehash: bc171a419632f2ac61c7c9bf6b201b84e0691c3a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641266"
---
# <a name="state-and-data-in-docker-applications"></a>Estado e dados em aplicativos do Docker

Na maioria dos casos, você pode considerar um contêiner uma instância de um processo. Um processo não mantém o estado persistente. Enquanto um contêiner pode gravar em seu armazenamento local, supondo que uma instância permanecerá indefinidamente é como presumir que um único local na memória será durável. Imagens de contêiner, assim como processos, devem ser consideradas ter várias instâncias, e eles serão eventualmente eliminados; Se forem gerenciadas com um orquestrador de contêiner, deve-se assumir que eles podem ser movidos de um nó ou VM para outro.

As soluções a seguir são usadas para gerenciar dados persistentes em aplicativos do Docker:

Do host do Docker, como [Volumes do Docker](https://docs.docker.com/engine/admin/volumes/):

- **Volumes** são armazenados em uma área do sistema de arquivos de host que é gerenciado pelo Docker.

- **Associar montagens** pode mapear para qualquer pasta no sistema de arquivos do host, portanto, o acesso não pode ser controlado a partir de um processo de Docker e pode representar um risco de segurança como um contêiner pode acessar as pastas de sistema operacional confidenciais.

- **Montagens tmpfs** são como pastas virtuais que só existem na memória do host e nunca são gravadas no sistema de arquivos.

Do armazenamento remoto:

- [O armazenamento do Azure](https://azure.microsoft.com/documentation/services/storage/) oferece armazenamento geograficamente distribuído, fornecendo uma boa solução de persistência de longo prazo para contêineres.

- Bancos de dados relacionais remotos, como [banco de dados SQL](https://azure.microsoft.com/services/sql-database/), como bancos de dados NoSQL [do Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), ou serviços, como armazenar em cache [Redis](https://redis.io/).

Do contêiner do Docker:

- O Docker oferece um recurso chamado *sistema de arquivos de sobreposição*. Esse recurso implementa uma tarefa de cópia na gravação que armazena informações atualizadas para o sistema de arquivos raiz do contêiner. Essas informações "apresenta na parte superior de" a imagem original na qual o contêiner se baseia. Se o contêiner for excluído do sistema, essas alterações serão perdidas. Portanto, embora seja possível salvar o estado de um contêiner em seu armazenamento local, criando um sistema baseado neste recurso entraria em conflito com a premissa de design de contêiner, que é sem monitoração de estado por padrão.

- No entanto, os Volumes Docker agora é a maneira preferencial para lidar com dados locais no Docker. Se você precisar de mais informações sobre o armazenamento em contêineres, verificar [drivers de armazenamento do Docker](https://docs.docker.com/engine/userguide/storagedriver/) e [sobre drivers de armazenamento, contêineres e imagens](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).

O exemplo a seguir fornece detalhes adicionais sobre essas opções.

**Volumes** são diretórios mapeados do sistema operacional do host para diretórios em contêineres. Quando o código no contêiner tem acesso ao diretório, o acesso é, na verdade, a um diretório no sistema operacional host. Esse diretório não está vinculado ao tempo de vida do contêiner em si, sendo que o diretório é gerenciado pelo Docker e isolado em relação à funcionalidade básica do computador host. Assim, os volumes de dados são projetados para persistir dados independentemente do tempo de vida do contêiner. Se você excluir um contêiner ou uma imagem do host do Docker, os dados persistentes no volume de dados não serão excluídos.

Volumes podem ser nomeados ou anônimos (o padrão). Volumes nomeados são a evolução dos **Contêineres de Volume de Dados** e facilitam o compartilhamento de dados entre contêineres. Volumes também dão suporte a drivers de volume que permitem que você armazene dados em hosts remotos, entre outras opções.

**Associar montagens** estiveram disponíveis por um longo tempo e permitir que o mapeamento de qualquer pasta para um ponto de montagem em um contêiner. Montagens de associação têm mais limitações que os volumes e alguns problemas de segurança importantes, por isso os volumes são a opção recomendada.

**`tmpfs` monta** são pastas virtuais que live apenas na memória do host e nunca são gravadas no sistema de arquivos. Elas são rápidas e seguras, mas usam a memória e destinam-se somente a dados não persistentes.

Conforme mostrado na Figura 4-5, os volumes Docker regulares podem ser armazenados fora dos contêineres de si, mas dentro dos limites físicos do servidor host ou VM. No entanto, contêineres do Docker não podem acessar um volume de um servidor host ou VM para outro. Em outras palavras, com esses volumes, não é possível gerenciar os dados compartilhados entre contêineres executados em hosts diferentes do Docker, embora esses dados possam ser obtidos com um driver de volume que dá suporte a hosts remotos.

![Volumes podem ser compartilhados entre contêineres, mas apenas no mesmo host, a menos que você use um driver remoto que dá suporte a hosts remotos. ](./media/image5.png)

**Figura 4-5**. Volumes e fontes de dados externas para aplicativos baseados em contêiner

Além disso, quando gerenciados por um orquestrador, contêineres do Docker podem se "mover" entre os hosts de acordo com as otimizações realizadas pelo cluster. Portanto, não é recomendável usar volumes de dados para dados empresariais. Mas eles são um bom mecanismo para trabalhar com arquivos de rastreamento, arquivos temporais ou similares, que não afetarão a consistência dos dados de negócios.

**Fontes de dados remotas e ferramentas de cache** como o Banco de Dados SQL do Azure, o Azure Cosmos DB ou um cache remoto como o Redis podem ser usados em aplicativos em contêineres da mesma forma que são usados durante o desenvolvimento sem contêineres. Essa é uma forma comprovada de armazenar dados de aplicativo de negócios.

**Armazenamento do Azure.** Dados de negócios geralmente precisam ser colocado em recursos externos ou bancos de dados, como o armazenamento do Azure. O armazenamento do Azure fornece os seguintes serviços na nuvem:

- O Armazenamento de Blobs armazena dados de objeto não estruturados. Um blob pode ser qualquer tipo de texto ou dados binários, como documentos ou arquivos de mídia (imagens, áudio e vídeo). O Armazenamento de Blobs também é conhecido como armazenamento de objeto.

- O armazenamento de arquivos oferece armazenamento compartilhado para aplicativos herdados que usam o protocolo SMB padrão. Os serviços de nuvem e as máquinas virtuais do Azure podem compartilhar dados de arquivos em vários componentes de aplicativo por meio de compartilhamentos montados. Aplicativos locais podem acessar dados de arquivo em um compartilhamento por meio da API de REST do serviço de arquivo.

- O Armazenamento de Tabelas armazena conjuntos de dados estruturados. O Armazenamento de Tabelas é um armazenamento de dados do atributo-chave NoSQL, que permite o rápido desenvolvimento e acesso a grandes quantidades de dados.

**Bancos de dados relacionais e bancos de dados NoSQL.** Há muitas opções de bancos de dados externos, de bancos de dados relacionais, como SQL Server, PostgreSQL, Oracle ou bancos de dados NoSQL, como Azure Cosmos DB, MongoDB, etc. Esses bancos de dados não forem ser explicado como parte deste guia, pois são completamente um tópico diferente.

>[!div class="step-by-step"]
>[Anterior](monolithic-applications.md)
>[Próximo](soa-applications.md)
