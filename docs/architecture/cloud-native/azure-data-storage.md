---
title: Armazenamento de dados no Azure
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Armazenamento de dados no Azure
ms.date: 06/30/2019
ms.openlocfilehash: 1a86cecf005c6dbdfda5cf4cacfafaad4711c076
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087762"
---
# <a name="data-storage-in-azure"></a>Armazenamento de dados no Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Como vimos em todo este livro, a nuvem está mudando a maneira como os aplicativos são projetados, implantados e gerenciados. Ao mudar para a nuvem, uma pergunta crítica é como você move seus dados? Felizmente, a nuvem do Azure oferece muitas opções.

Você poderia apenas provisionar uma máquina virtual do Azure e instalar seu banco de dados de sua escolha. Isso é conhecido como [IaaS (infraestrutura como serviço)](https://www.techopedia.com/definition/141/infrastructure-as-a-service-iaas). Essa abordagem simplifica a movimentação de um banco de dados local para a nuvem, no estado em que se encontra, mas muda a carga de gerenciar a máquina virtual e o banco de dados para você.

Em vez disso, um [DBaaS (banco de dados como serviço)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) totalmente gerenciado é uma opção melhor. Você obtém muitos recursos internos enquanto a hospedagem, a manutenção e o licenciamento são gerenciados pela Microsoft. O Azure apresenta diferentes tipos de opções de armazenamento de dados totalmente gerenciadas, cada uma com benefícios específicos. Todos eles dão suporte à capacidade just-in-time e a um modelo pago conforme o uso.

Em seguida, vamos examinar as opções de DBaaS disponíveis no Azure. Você verá como a Microsoft continua sendo o compromisso de manter o Azure uma "plataforma aberta", oferecendo suporte gerenciado para muitos bancos de dados relacionais e NoSQL de software livre e fazendo contribuições importantes para as várias bases de código-fonte aberto como um membro ativo.

## <a name="azure-sql-database"></a>Banco de dados SQL do Azure

O [banco de dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/) é um DBaaS (banco de dados como serviço) de uso geral, repleto de recursos, com base no mecanismo de banco de dados do Microsoft SQL Server. Ele é totalmente gerenciado pela Microsoft e é um banco de dados de nuvem seguro, confiável e de alto desempenho. O serviço compartilha muitos dos recursos encontrados na versão local do SQL Server.

Você pode provisionar um servidor de banco de dados SQL e um banco de dados em minutos. Quando a demanda por seu aplicativo cresce de alguns clientes para milhões, o banco de dados SQL do Azure é dimensionado dinamicamente com tempo de inatividade mínimo. Você pode adicionar ou remover recursos dinamicamente, incluindo capacidade de CPU, memória, taxa de transferência de e/s e armazenamento alocado para seus bancos de dados.

A Figura 5-12 mostra as opções de implantação para o banco de dados SQL do Azure.

![Opções de implantação do Azure SQL](./media/azure-sql-database-deployment-options.png)

**Figura 5-12**. Opções de implantação do Azure SQL

Observe as alternativas na figura anterior ao implantar um banco de dados SQL:

- Um [banco de dados individual](https://docs.microsoft.com/azure/sql-database/sql-database-single-database)  with seu próprio conjunto de recursos gerenciados por um [servidor de banco de dados SQL](https://docs.microsoft.com/azure/sql-database/sql-database-servers). Um banco de dados individual é semelhante a um [banco de dados independente](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases)  in uma implantação de SQL Server local.

- Um [pool elástico](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-pool) no qual uma coleção de bancos de dados SQL compartilha um único servidor de banco de dados SQL por um preço definido. Bancos de dados individuais podem ser movidos para dentro e para fora de um pool elástico, conforme necessário, para otimizar o desempenho do preço de um grupo de bancos de dados.

- Uma [instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) no, que é uma coleção de bancos de dados de sistema e de usuário, fornece compatibilidade quase 100% com uma SQL Server local. Essa opção dá suporte a bancos de dados maiores, até 35 TB e é colocada em uma [rede virtual do Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) para um melhor isolamento.

O banco de dados SQL do Azure é uma [mecanismo de banco de dados de PaaS (plataforma como serviço)](https://docs.microsoft.com/azure/sql-database/sql-database-paas) totalmente gerenciada que lida com atualização, aplicação de patches, backups e monitoramento sem envolvimento do usuário. Ele sempre executa a versão estável mais recente do SQL Server Mecanismo de Banco de Dados e o sistema operacional corrigido e garante 99,99% de disponibilidade. Um recurso, [a replicação geográfica ativa](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication), permite criar bancos de dados secundários legíveis no mesmo ou em um data center do Azure diferente. Após a falha, um failover para um banco de dados secundário pode ser iniciado. Nesse ponto, os outros secundários se vinculam automaticamente ao novo primário. Há suporte para até quatro réplicas secundárias no mesmo ou em regiões diferentes, e esses secundários também podem ser usados para consultas de acesso somente leitura.

O banco de dados SQL do Azure inclui recursos [internos de monitoramento e ajuste inteligente](https://docs.microsoft.com/azure/sql-database/sql-database-monitoring-tuning-index) que podem ajudá-lo a maximizar o desempenho e reduzir os custos operacionais. Por exemplo, o recurso de [ajuste automático](https://docs.microsoft.com/azure/sql-database/sql-database-automatic-tuning) fornece ajuste de desempenho contínuo com base no ia e no aprendizado de máquina. O serviço aprende com suas cargas de trabalho em execução e pode aplicar recomendações de ajuste. Quanto mais tempo um banco de dados SQL do Azure for executado com o ajuste automático habilitado, melhor será o desempenho.

O [banco de dados SQL do Azure sem servidor](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) (disponível para visualização no momento da gravação deste livro) é uma camada de computação para bancos de dados individuais que são dimensionados automaticamente com base na demanda de carga de trabalho e cobra pela quantidade de computação usada por segundo. A camada de computação sem servidor também pausa automaticamente os bancos de dados durante períodos inativos para que somente os encargos de armazenamento sejam cobrados. Ela é retomada automaticamente quando a atividade retorna.

Por fim, há o novo tipo de preço de [hiperescala do banco de dados SQL do Azure](https://azure.microsoft.com/services/sql-database/) . Ele é alimentado por uma arquitetura de armazenamento altamente escalonável e permite que seu banco de dados cresça conforme necessário, eliminando a necessidade de pré-configurar os recursos de armazenamento. Você pode dimensionar os recursos de computação e armazenamento de forma independente, fornecendo a flexibilidade para otimizar o desempenho de cada carga de trabalho. A hiperescala do banco de dados SQL do Azure é otimizada para processamento [OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) e cargas de trabalho analíticas de alta taxa de transferência com armazenamento de até 100 TB.  Com cargas de trabalho com uso intensivo de leitura, o hiperscale fornece expansão rápida ao provisionar réplicas de leitura adicionais conforme necessário para descarregar cargas de trabalho de leitura.

Além da pilha de Microsoft SQL Server tradicional, o Azure também apresenta versões gerenciadas de vários bancos de dados de software livre populares.

## <a name="azure-database-for-mysql"></a>Banco de dados do Azure para MySQL

O [MySQL](https://en.wikipedia.org/wiki/MySQL)  is um [banco de dados relacional](https://en.wikipedia.org/wiki/Relational_database_management_system) [de código aberto](https://en.wikipedia.org/wiki/Open-source_software). É um componente da pilha de [software da lâmpada](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) e é usado por muitas organizações de grande porte, incluindo o Facebook, o Twitter e o YouTube. A Community Edition está disponível gratuitamente e a Enterprise Edition requer uma compra de licença. Originalmente criado em 1995, o produto foi adquirido pela Sun Microsystems no 2008, que foi adquirido pela Oracle na 2010.

O [banco de dados do Azure para MySQL](https://azure.microsoft.com/services/mysql/) é um serviço de banco de dados relacional totalmente gerenciado e pronto para empresas com base no mecanismo de servidor MySQL de software livre. Implementando o MySQL Community Edition, ele inclui os seguintes recursos de PaaS sem custo adicional:

- [Alta disponibilidade](https://docs.microsoft.com/azure/mysql/concepts-high-availability)interna.

- Desempenho previsível, usando [preços de pagamento conforme o uso](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers)inclusivo.

- [Dimensione](https://docs.microsoft.com/azure/mysql/concepts-high-availability) conforme necessário em segundos.

- Protegido para proteger dados confidenciais em repouso e em movimento.

- [Backups automáticos](https://docs.microsoft.com/azure/mysql/concepts-backup) e [restauração pontual](https://docs.microsoft.com/azure/mysql/concepts-backup) por até 35 dias.

- Segurança e conformidade de nível empresarial.

Esses recursos internos de PaaS são importantes para organizações que têm centenas de bancos de dados "táticos" (não estratégicos) em seus data centers, mas não têm os recursos para executar patches, backup, segurança e monitoramento de desempenho.

Além disso, o [serviço de migração de dados do Azure](https://azure.microsoft.com/services/database-migration/) pode migrar dados de várias fontes de banco de dados para plataformas do Azure data com tempo de inatividade mínimo. O serviço gera relatórios de avaliação e fornece recomendações para orientá-lo pelas alterações necessárias à execução de uma migração, pequena ou grande.

O [servidor MySQL do Azure](https://docs.microsoft.com/azure/mysql/concepts-servers) gerenciado é o ponto administrativo central para o serviço. É o mesmo mecanismo de servidor MySQL usado para implantações locais. Com ele, você pode criar um único banco de dados por servidor para consumir todos os recursos ou criar vários bancos por servidor para compartilhar recursos. Sua equipe pode continuar a desenvolver aplicativos com as ferramentas de software livre e a plataforma de sua escolha sem precisar aprender novas habilidades ou gerenciar máquinas virtuais e infraestrutura.

## <a name="azure-database-for-mariadb"></a>Banco de dados do Azure para MariaDB

[MariaDB](https://mariadb.com/) O servidor é outro servidor de banco de dados de software livre popular. Ele foi criado como uma bifurcação do MySQL pelos desenvolvedores originais do MySQL no momento em que a Oracle comprou a Sun Microsystems que teve Propriedade do MySQL. A intenção era garantir que MariaDB permanecia Open-Source.

Como MariaDB é uma [bifurcação do MySQL](https://blog.panoply.io/a-comparative-vmariadb-vs-mysql), as definições de tabela e de dados são compatíveis, e os protocolos, estruturas e APIs do cliente são close-spojit. Os conectores de dados MySQL funcionarão MariaDB sem modificação.

O MariaDB tem um forte e é usado por muitas empresas de grande porte. Embora a Oracle continue a manter, aprimorar e oferecer suporte a MySQL, o MariaDB é gerenciado pelo MariaDB Foundation, permitindo contribuições públicas ao produto e à documentação.

O [banco de dados do Azure para MariaDB](https://azure.microsoft.com/services/mariadb/) é um banco de dados totalmente gerenciado como um serviço na nuvem do Azure. Ele é baseado no mecanismo de servidor do [MariaDB Community Edition](https://mariadb.org/download/) . Ele pode lidar com cargas de trabalho críticas com desempenho previsível e escalabilidade dinâmica. Semelhante às outras plataformas de banco de dados do Azure, ele inclui muitos recursos de plataforma como serviço sem custo adicional:

- [Alta disponibilidade](https://docs.microsoft.com/azure/mariadb/concepts-high-availability)interna.

- Desempenho previsível, usando [preços de pagamento conforme o uso](https://docs.microsoft.com/azure/mariadb/concepts-pricing-tiers)inclusivo.

- [Dimensionamento](https://docs.microsoft.com/azure/mariadb/concepts-high-availability) conforme necessário em segundos.

- Proteção protegida de dados confidenciais em repouso e em movimento.

- [Backups automáticos](https://docs.microsoft.com/azure/mariadb/concepts-backup) e [restauração pontual](https://docs.microsoft.com/azure/mariadb/concepts-backup) por até 35 dias.

- Segurança e conformidade de nível empresarial.

## <a name="azure-database-for-postgresql"></a>Banco de dados do Azure para PostgreSQL

[PostgreSQL](https://www.postgresql.org/) é outro banco de dados relacional popular de código aberto com mais de 30 anos de desenvolvimento ativo. É uma finalidade geral e um sistema de gerenciamento de banco de dados relacional de objeto. Seu licenciamento é considerado "liberal" e o produto está livre para usar, modificar e distribuir em qualquer forma. Muitas empresas de grande porte, incluindo Apple, Red Hat e Fujitsu, têm produtos criados usando PostgreSQL.

O [banco de dados do Azure para PostgreSQL](https://azure.microsoft.com/services/postgresql/) é um serviço de banco de dados relacional totalmente gerenciado, baseado no mecanismo de banco de dados Postgres de código aberto. Ele pode lidar com cargas de trabalho críticas com desempenho previsível, segurança, alta disponibilidade e escalabilidade dinâmica. Ele oferece suporte a várias estruturas e linguagens de software livre C++, incluindo Java, Python, Node, C \# e php. Ele permite a [migração](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) de bancos de dados PostgreSQL por meio de uma interface de linha de comando ou do [serviço de migração de dado do Azure](https://azure.microsoft.com/services/database-migration/).

O serviço inclui [inteligência interna](https://docs.microsoft.com/azure/postgresql/concepts-monitoring) que estuda seus padrões de banco de dados exclusivos e fornece recomendações e informações personalizadas para ajudá-lo a maximizar o desempenho do seu banco de dados PostgreSQL. A [proteção avançada contra ameaças](https://docs.microsoft.com/azure/postgresql/concepts-data-access-and-security-threat-protection) monitora o banco de dados em todo o relógio e detecta possíveis atividades mal-intencionadas, alertando você sobre a detecção para que você possa intervir imediatamente.

O banco de dados do Azure para PostgreSQL está disponível como duas opções de implantação: servidor único e hiperescala (Citus), disponível para visualização no momento da gravação deste livro

- A opção de implantação de [servidor único](https://docs.microsoft.com/azure/postgresql/concepts-servers) é um ponto administrativo central para vários bancos de dados. É o mesmo mecanismo de servidor PostgreSQL disponível para implantações locais. Com ele, você pode criar um único banco de dados por servidor para consumir todos os recursos ou criar vários bancos de dados para compartilhar os recursos. O preço é estruturado por servidor com base nos núcleos e no armazenamento.

- A [opção de hiperescala (Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) é alimentada por [Citus data](https://www.citusdata.com/)  technology. Ele permite o dimensionamento de alto desempenho, dimensionando horizontalmente um único banco de dados em centenas de nós para fornecer desempenho e escala extremamente rápidos. Essa opção permite que o mecanismo caiba mais dados na memória, paraleliza consultas em centenas de nós e indexe dados mais rapidamente. O recurso de hiperescala é compatível com as inovações, versões e ferramentas mais recentes para PostgreSQL, para que você possa aproveitar sua experiência de PostgreSQL existente.

## <a name="cosmos-db"></a>Cosmos DB

Azure Cosmos DB é um serviço de banco de dados NoSQL totalmente gerenciado e distribuído globalmente, projetado para fornecer baixa latência, escalabilidade elástica, consistência de dados gerenciados e alta disponibilidade. Em suma, se seu aplicativo precisar de tempo de resposta rápido garantido em qualquer lugar do mundo, se for necessário estar sempre online e precisar de escalabilidade ilimitada e elástica de taxa de transferência e armazenamento, Cosmos DB será uma ótima opção. A Figura 5-13 mostra uma visão geral de alto nível do Cosmos DB.

![Visão geral do Cosmos DB](./media/cosmos-db-overview.png)

**Figura 5-13**: visão geral do cosmos DB

Observe na Figura 5-13 como o Cosmos DB é um serviço de banco de dados robusto e altamente versátil com muitos recursos nativos de nuvem internos. Nesta seção, vamos examiná-las mais detalhadamente.

### <a name="global-support"></a>Suporte global

Você pode distribuir globalmente bancos de dados do cosmos em todas as regiões do Azure em todo o mundo, colocando-os perto dos seus usuários, melhorando o tempo de resposta e reduzindo a latência. Você pode adicionar ou remover um banco de dados de uma região sem pausar ou reimplantar seu aplicativo. Em segundo plano, Cosmos DB replica os dados de forma transparente para todas as regiões configuradas.

O Cosmos DB dá suporte ao clustering [ativo/ativo](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) no nível global, permitindo que você configure qualquer ou todas as suas regiões de banco de dados para dar suporte a gravações e leituras.

O recurso de protocolo de [vários mestres](https://docs.microsoft.com/azure/cosmos-db/how-to-multi-master) no cosmos DB permite a seguinte funcionalidade:

- Gravação e escalabilidade de leitura elástica ilimitada.

- 99,999% de disponibilidade de leitura e gravação em todo o mundo.

- Leituras e gravações Garantidas servidas em menos de 10 milissegundos no 99 º percentil.

Internamente, o Cosmos DB lida com a replicação de dados entre regiões com garantias de nível de consistência e contratos de nível de serviço com suporte financeiro.

Com o Cosmos DB [APIs de hospedagem múltipla](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), seu aplicativo pode ficar automaticamente ciente da região do Azure mais próxima e enviar solicitações para ele. A região mais próxima é identificada por Cosmos DB sem nenhuma alteração de configuração. Se uma região ficar indisponível, Cosmos DB dá suporte ao failover automático e o recurso de hospedagem múltipla roteará automaticamente sua solicitação para a próxima região disponível mais próxima.

### <a name="multi-model-support"></a>Suporte a vários modelos

O Cosmos DB é uma *plataforma de dados multimodelo* que permite que você interaja com seus dados usando vários modelos NoSQL com suporte, incluindo documentos, pares chave-valor, largura de coluna e representações de gráfico. Internamente, os dados são armazenados em um formato [struct](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/using-structs) simples composto por tipos de dados primitivos, incluindo cadeias de caracteres, BOOLs e números. Para cada solicitação, o mecanismo de banco de dados converte os dados na representação de modelo que você selecionou. Você pode escolher entre uma API proprietária do Cosmos DB baseada em SQL ou qualquer uma das [APIs de compatibilidade](https://www.wikiwand.com/en/Cosmos_DB) mostradas na Figura 5-14.

![Provedores de Cosmos DB](./media/cosmos-db-providers.png)

**Figura 5-14**: provedores de Cosmos DB

Observação na Figura 5-14 como o Cosmos DB dá suporte ao [armazenamento de tabela](https://azure.microsoft.com/services/storage/tables/). Tanto Cosmos DB quanto o [armazenamento de tabelas do Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) compartilham o mesmo modelo de tabela subjacente e expõem muitas das mesmas operações de tabela. No entanto, o [Cosmos DB API de tabela](https://docs.microsoft.com/azure/cosmos-db/table-introduction) fornece muitos aprimoramentos Premium não disponíveis na API de armazenamento do Azure. Esses recursos estão em contraste com a Figura 5-15.

![API de Tabela do Azure](./media/azure-table-api.png)

**Figura 5-15**: API de tabela do Azure

Os aplicativos escritos para o armazenamento de tabelas do Azure podem migrar para Azure Cosmos DB usando o API de Tabela sem alterações de código.

Nos cenários de aplicativos [Brownfield](https://en.wikipedia.org/wiki/Brownfield_(software_development)) , as equipes de desenvolvimento podem migrar os bancos de dados Mongo, Gremlin ou Cassandra existentes para Cosmos DB com alterações mínimas no código do aplicativo ou dos aplicativos existentes. Para cenários [Greenfield](https://en.wikipedia.org/wiki/Greenfield_project) , as equipes de desenvolvimento podem escolher o modelo de dados que melhor atenda aos seus requisitos e preferências, incluindo opções de software livre totalmente suportadas para as plataformas MongoDB, Cassandra e Gremlin.

### <a name="consistency-models"></a>Modelos de consistência

Anteriormente, na seção *relacional versus NoSQL* , discutimos o assunto da *consistência de dados*, que é um termo que se refere à integridade de seus dados. Os bancos de dados distribuídos que dependem da replicação para alta disponibilidade, baixa latência ou ambos, devem tomar uma compensação fundamental entre consistência de leitura, disponibilidade e latência.

A maioria dos bancos de dados distribuídos permite que os desenvolvedores escolham entre dois modelos de consistência: [consistência forte](https://en.wikipedia.org/wiki/Strong_consistency) e [consistência eventual](https://en.wikipedia.org/wiki/Eventual_consistency). A *consistência forte* é o padrão ouro de programação de dados. Ele garante que um resultado da consulta sempre retornará os dados mais atuais, mesmo que o sistema deva incorrer em latência aguardando que uma atualização seja replicada em todas as cópias de banco de dados. Por outro lado, um sistema configurado para *consistência eventual* retornará dados imediatamente, mesmo que os dados não sejam a cópia mais atual. Essa opção permite maior disponibilidade, maior escala e melhor desempenho.

O Azure Cosmos DB oferece um espectro de [cinco modelos de consistência bem definidos](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) mostrados na Figura 5-16. Essas opções permitem que você faça opções precisas e compensações granulares em relação à disponibilidade e ao desempenho com base nas necessidades do seu aplicativo. Esses modelos são bem definidos, intuitivos e apoiados pelos SLAs (contratos de nível de serviço).

![Níveis de consistência do Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Figura 5-16**: níveis de consistência de Cosmos DB

### <a name="partitioning"></a>Divisão

O Azure Cosmos DB usa o [particionamento](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) automático para dimensionar o banco de dados para atender às necessidades de desempenho do seu aplicativo.

Você gerencia dados em Cosmos DB dados criando bancos de dados [, contêineres e itens](https://docs.microsoft.com/azure/cosmos-db/databases-containers-items), mostrados na Figura 5-17.

![Entidades de Cosmos DB](./media/cosmos-db-entities.png)

**Figura 5-17**: hierarquia de entidades de Cosmos DB

Observação na Figura 5-17 como você começa criando um banco de dados Cosmos DB dentro de uma conta de banco de dados. Esse banco de dados se torna a unidade de gerenciamento para um conjunto de contêineres. Um contêiner é um agrupamento independente de esquema de itens que podem ser expressos como uma coleção, tabela ou gráfico, com base no provedor de API selecionado (discutido na seção anterior). Os itens são os dados que você adiciona ao contêiner e são representados como documentos, linhas, nós ou bordas. Por padrão, todos os itens que você adiciona a um contêiner são indexados automaticamente sem a necessidade de um índice explícito ou gerenciamento de esquema.

Para particionar o contêiner, os itens são divididos em subconjuntos distintos chamados [partições lógicas](https://docs.microsoft.com/azure/cosmos-db/partition-data). As partições lógicas são criadas com base no valor de uma chave de partição associada a cada item em um contêiner. A Figura 5-18 mostra como todos os itens em uma partição lógica têm o mesmo valor de chave de partição.

![Mecânica de particionamento de Cosmos DB](./media/cosmos-db-partitioning.png)

**Figura 5-18**: Cosmos dB a mecânica de particionamento

Observação na Figura 5-18 como cada item inclui uma chave de partição de ' City ' ou ' Airport '. Essa chave de partição determina a partição lógica do item. Cada código de cidade é atribuído a uma partição lógica no contêiner no lado esquerdo e àqueles com um código de aeroporto para o contêiner à direita. A combinação do valor da chave de partição com o valor de ID de um item cria o índice do item, que identifica exclusivamente o item.

Internamente, Cosmos DB gerencia automaticamente o posicionamento de [partições lógicas](https://docs.microsoft.com/azure/cosmos-db/partition-data) em [partições físicas](https://docs.microsoft.com/azure/cosmos-db/partition-data) para atender com eficiência às necessidades de escalabilidade e desempenho do contêiner. À medida que os requisitos de taxa de transferência e armazenamento de um aplicativo aumentam, Azure Cosmos DB move partições lógicas para redistribuir a carga em um número maior de servidores. Essas operações de redistribuição são gerenciadas pelo Cosmos DB e são executadas sem nenhuma interrupção ou tempo de inatividade.

## <a name="azure-redis-cache"></a>Cache Redis do Azure

Os benefícios do armazenamento em cache para melhorar o desempenho e a escalabilidade são bem compreendidos.

Para um aplicativo nativo de nuvem, um local comum para adicionar o cache está dentro do gateway de API. O gateway serve como um front-end para todas as solicitações de entrada. Ao adicionar o cache, você pode aumentar o desempenho e a capacidade de resposta retornando dados armazenados em cache e evitando viagens de ida e volta para um banco de dados local ou um serviço downstream. A Figura 5-19 mostra uma arquitetura de cache para um aplicativo nativo de nuvem.

![Caching em um aplicativo nativo de nuvem](./media/caching-in-a-cloud-native-app.png)

**Figura 5-19**: Caching em um aplicativo nativo de nuvem

Um padrão de cache comum é o [padrão de reserva de cache](https://docs.microsoft.com/azure/architecture/patterns/cache-aside). Para uma solicitação de entrada, primeiro você consulta o cache para a resposta, mostrada na etapa #1 na Figura 5-19. Se for encontrado, os dados serão retornados imediatamente. Se os dados não existirem no cache (conhecido como [erro de cache](https://www.techopedia.com/definition/6308/cache-miss)), eles são recuperados do banco de dados local ou do serviço downstream (etapa #2), gravados no cache para solicitações futuras (etapa #3) e retornados ao chamador. Deve-se ter cuidado para remover periodicamente os dados armazenados em cache para que o sistema permaneça consistente e preciso.

Além disso, observe na Figura 5-19 como o cache não é implementado localmente dentro dos limites do serviço, mas, em vez disso, é consumido como um serviço de backup baseado em nuvem, conforme discutido no capítulo 1.

O [cache Redis do Azure](https://azure.microsoft.com/services/cache/) é um serviço de agente de mensagens e cache de dados. Ele fornece alta taxa de transferência e acesso de baixa latência aos dados para aplicativos. Ele é totalmente gerenciado pela Microsoft, hospedado no Azure e acessível a qualquer aplicativo dentro ou fora do Azure.

Internamente, o cache do Azure para Redis é apoiado pelo [servidor Redis](https://redis.io/) de código-fonte aberto e oferece suporte nativo a estruturas de dados como [cadeias de caracteres](https://redis.io/topics/data-types#strings), [hashes](https://redis.io/topics/data-types#hashes), [listas](https://redis.io/topics/data-types#sets), [conjuntos](https://redis.io/topics/data-types#sets)e [conjuntos classificados](https://redis.io/topics/data-types#sorted-sets). Se seu aplicativo usar Redis, ele funcionará no estado em que se encontra com o cache do Azure para Redis.

O cache do Azure para Redis também pode ser usado como um cache de dados na memória, um banco de dado não relacional distribuído e um agente de mensagem. Ele está disponível em três tipos de preço diferentes. A camada Premium apresenta muitos recursos de nível empresarial, como clustering, persistência de dados, replicação geográfica e segurança e isolamento de rede virtual.

>[!div class="step-by-step"]
>[Anterior](data-patterns.md)
>[Próximo](resiliency.md)
