---
title: Relacional versus Dados NoSQL
description: Saiba mais sobre dados relacionais e NoSQL em aplicativos nativos da nuvem
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 3fb3dcc3a87e278c05f3e15d261245f4d61453d1
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805799"
---
# <a name="relational-vs-nosql-data"></a>Relacional versus Dados NoSQL

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relacional e NoSQL são dois tipos de sistemas de banco de dados comumente implementados em aplicativos nativos da nuvem. Eles são construídos de forma diferente, armazenam dados de forma diferente e acessados de forma diferente. Nesta seção, vamos olhar para ambos. Mais tarde, neste capítulo, veremos uma tecnologia emergente de banco de dados chamada *NewSQL*.

*As bases de dados relacionais* têm sido uma tecnologia predominante há décadas. Eles são maduros, comprovados e amplamente implementados. Produtos de banco de dados concorrentes, ferramentas e conhecimentos abundam. As bases de dados relacionais fornecem um armazenamento de tabelas de dados relacionadas. Essas tabelas têm um esquema fixo, usam SQL (Structured Query Language) para gerenciar dados e suportam garantias ACID.

*Os bancos de dados no-SQL* referem-se a armazenamentos de dados não relacionais de alto desempenho. Eles se destacam em suas características de facilidade de uso, escalabilidade, resiliência e disponibilidade. Em vez de juntar tabelas de dados normalizados, o NoSQL armazena dados não estruturados ou semiestruturados, muitas vezes em pares de valor-chave ou documentos JSON. Os bancos de dados no-SQL normalmente não fornecem garantias ACID além do escopo de uma única partição de banco de dados. Serviços de alto volume que requerem tempo de resposta sub segundo favorecem os datastores NoSQL.

O impacto das tecnologias [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) para sistemas nativos distribuídos em nuvem não pode ser exagerado. A proliferação de novas tecnologias de dados neste espaço tem interrompido soluções que antes dependiam exclusivamente de bases de dados relacionais.

Os bancos de dados NoSQL incluem vários modelos diferentes para acessar e gerenciar dados, cada um adequado a casos de uso específicos. A Figura 5-9 apresenta quatro modelos comuns.

![Modelos de dados NoSQL](./media/types-of-nosql-datastores.png)

**Figura 5-9**: Modelos de dados para bancos de dados NoSQL

| Modelo | Características |
| :-------- | :-------- |
| Loja de Documentos | Os dados e os metadados são armazenados hierarquicamente em documentos baseados em JSON dentro do banco de dados. |
| Loja de Valor Espora | O mais simples dos bancos de dados NoSQL, os dados são representados como uma coleção de pares de valor-chave. |
| Loja de colunas largas | Os dados relacionados são armazenados como um conjunto de pares de tecla/valor aninhadas dentro de uma única coluna. |
| Loja de gráficos | Os dados são armazenados em uma estrutura gráfica como propriedades de nó, borda e dados. |

## <a name="the-cap-theorem"></a>O teorema do CAP

Como forma de entender as diferenças entre esses tipos de bancos de dados, considere o teorema do CAP, um conjunto de princípios aplicados aos sistemas distribuídos que armazenam estado. A Figura 5-10 mostra as três propriedades do teorema do CAP.

![Teorema de CAP](./media/cap-theorem.png)

**Figura 5-10**. O teorema do CAP

O teorema afirma que os sistemas de dados distribuídos oferecerão uma troca entre consistência, disponibilidade e tolerância à partição. E que qualquer banco de dados só pode garantir *duas* das três propriedades:

- *Consistência.* Cada nó no cluster responde com os dados mais recentes, mesmo que o sistema deva bloquear a solicitação até que todas as réplicas sejam atualizadas. Se você consultar um "sistema consistente" para um item que está sendo atualizado no momento, você aguardará essa resposta até que todas as réplicas atualizem com sucesso. No entanto, você receberá os dados mais atuais.

- *Disponibilidade.* Cada nó retorna uma resposta imediata, mesmo que essa resposta não seja os dados mais recentes. Se você consultar um "sistema disponível" para um item que está sendo atualizado, você terá a melhor resposta possível que o serviço pode fornecer naquele momento.

- *Tolerância à partição.* Garante que o sistema continua a operar mesmo se um nó de dados replicado falhar ou perder a conectividade com outros nós de dados replicados.

Bancos de dados relacionais normalmente fornecem consistência e disponibilidade, mas não tolerância à partição. Eles são normalmente provisionados para um único servidor e escalam verticalmente adicionando mais recursos à máquina.

Muitos sistemas de banco de dados relacionais suportam recursos de replicação incorporados onde cópias do banco de dados principal podem ser feitas para outras instâncias de servidor secundário. As operações de gravação são feitas na instância primária e replicadas para cada um dos secundários. Após uma falha, a instância primária pode falhar em um secundário para fornecer alta disponibilidade. Os secundários também podem ser usados para distribuir operações de leitura. Enquanto as operações de gravações sempre vão contra a réplica primária, as operações de leitura podem ser roteadas para qualquer um dos secundários para reduzir a carga do sistema.

Os dados também podem ser particionados horizontalmente em vários nós, como com [fragmentação](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction). Mas, o fragmento aumenta drasticamente a sobrecarga operacional cuspindo dados em muitas peças que não podem se comunicar facilmente. Pode ser caro e demorado para gerenciar. Ele pode acabar impactando o desempenho, as junções de tabela e a integridade referencial.

Se as réplicas de dados perdessem a conectividade da rede em um cluster de banco de dados relacional "altamente consistente", você não seria capaz de escrever para o banco de dados. O sistema rejeitaria a operação de gravação, pois não pode replicar essa alteração para a outra réplica de dados. Cada réplica de dados tem que ser atualizada antes que a transação possa ser concluída.

Os bancos de dados NoSQL normalmente suportam alta disponibilidade e tolerância à partição. Eles se dimensionam horizontalmente, muitas vezes em servidores de mercadorias. Essa abordagem proporciona uma tremenda disponibilidade, tanto dentro como em regiões geográficas a um custo reduzido. Você particiona e replica dados através dessas máquinas, ou nós, fornecendo redundância e tolerância a falhas. A desvantagem é a consistência. Uma alteração nos dados de um nó NoSQL pode levar algum tempo para se propagar para outros nódulos. Normalmente, um nó de banco de dados NoSQL fornecerá uma resposta imediata a uma consulta - mesmo que os dados apresentados sejam obsoletos e ainda não sejam atualizados.

Se as réplicas de dados perdessem a conectividade em um cluster de banco de dados NoSQL "altamente disponível", você ainda poderia concluir uma operação de gravação no banco de dados. O cluster de banco de dados permitiria a operação de gravação e atualizaria cada réplica de dados à medida que ela se tornasse disponível.

Esse tipo de resultado é conhecido como consistência eventual, uma característica de sistemas de dados distribuídos onde as transações ACID não são suportadas. É um breve atraso entre a atualização de um item de dados e o tempo que leva para propagar essa atualização para cada um dos nós de réplica. Em condições normais, o atraso é tipicamente curto, mas pode aumentar quando os problemas surgem. Por exemplo, o que aconteceria se você atualizasse um item do produto em um banco de dados NoSQL nos Estados Unidos e consultasse esse mesmo item de dados de um nó de réplica na Europa? Você receberia as informações anteriores do produto, até que o cluster atualize o nó europeu com a alteração do produto. Ao retornar imediatamente um resultado de consulta e não esperar que todos os nós de réplica sejam atualizados, você ganha enorme escala e volume, mas com a possibilidade de apresentar dados mais antigos.

Alta disponibilidade e escalabilidade maciça são muitas vezes mais críticas para o negócio do que uma forte consistência. Os desenvolvedores podem implementar técnicas e padrões como Sagas, CQRS e mensagens assíncronas para abraçar uma eventual consistência.

> Atualmente, deve-se ter cuidado ao conider as restrições do teorema do CAP. Um novo tipo de banco de dados, chamado NewSQL, surgiu que amplia o mecanismo de banco de dados relacional para suportar tanto a escalabilidade horizontal quanto o desempenho escalável dos sistemas NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Considerações para sistemas relacionais vs. NoSQL

Com base em requisitos específicos de dados, um microserviço baseado em nuvem pode implementar um datastore relacional, NoSQL ou ambos.

|  Considere um armazenamento de dados NoSQL quando: | Considere um banco de dados relacional quando: |
| :-------- | :-------- |
| Você tem cargas de trabalho de alto volume que requerem grande escala | Seu volume de carga de trabalho é consistente e requer média a grande escala |
| Suas cargas de trabalho não requerem garantias acidiálas |  Garantias acidiásas são necessárias |
| Seus dados são dinâmicos e frequentemente mudam | Seus dados são previsíveis e altamente estruturados |
| Os dados podem ser expressos sem relacionamentos | Os dados são melhor expressos relacionalmente |  
| Você precisa de gravações rápidas e escrever segurança não é crítico | A segurança de gravação é um requisito |  
| A recuperação de dados é simples e tende a ser plana | Você trabalha com consultas e relatórios complexos|
| Seus dados exigem uma ampla distribuição geográfica | Seus usuários são mais centralizados |
| Seu aplicativo será implantado em hardware de mercadorias, como com nuvens públicas | Seu aplicativo será implantado em hardware grande e high-end |
|||

Nas próximas seções, exploraremos as opções disponíveis na nuvem do Azure para armazenar e gerenciar seus dados nativos da nuvem.

## <a name="database-as-a-service"></a>Banco de dados como serviço

Para começar, você pode provisionar uma máquina virtual do Azure e instalar seu banco de dados de escolha para cada serviço. Enquanto você teria controle total sobre o ambiente, você ignoraria muitos recursos incorporados da plataforma de nuvem. Você também seria responsável pelo gerenciamento da máquina virtual e do banco de dados de cada serviço. Essa abordagem pode rapidamente se tornar demorada e cara.

Em vez disso, aplicativos nativos na nuvem favorecem serviços de dados expostos como um [Banco de Dados como Serviço (DBaaS).](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) Totalmente gerenciados por um fornecedor de nuvem, esses serviços fornecem segurança, escalabilidade e monitoramento incorporados. Em vez de possuir o serviço, você simplesmente o consome como um [serviço de apoio.](./definition.md#backing-services) O provedor opera o recurso em escala e assume a responsabilidade pelo desempenho e manutenção.

Eles podem ser configurados em zonas e regiões de disponibilidade de nuvem para obter alta disponibilidade. Todos eles suportam a capacidade just-in-time e um modelo de pagamento como você vai. O Azure possui diferentes tipos de opções de serviço de dados gerenciados, cada uma com benefícios específicos.

Vamos primeiro olhar para os serviços relacionais DBaaS disponíveis no Azure. Você verá que o principal banco de dados SQL Server da Microsoft está disponível, juntamente com várias opções de código aberto. Em seguida, falaremos sobre os serviços de dados NoSQL no Azure.

## <a name="azure-relational-databases"></a>Bancos de dados relacionais azure

Para microserviços nativos em nuvem que requerem dados relacionais, o Azure oferece quatro bancos de dados relacionais gerenciados como ofertas de serviço (DBaaS), mostrados na Figura 5-11.

![Bancos de dados relacionais gerenciados no Azure](./media/azure-managed-databases.png)

**Figura 5-11**. Bancos de dados relacionais gerenciados disponíveis no Azure

Na figura anterior, observe como cada um se senta em cima de uma infra-estrutura DBaaS comum que apresenta recursos-chave sem custo adicional.

Esses recursos são especialmente importantes para organizações que prover um grande número de bancos de dados, mas têm recursos limitados para administrá-los.
Você pode provisionar um banco de dados Azure em minutos selecionando a quantidade de núcleos de processamento, memória e armazenamento subjacente. Você pode dimensionar o banco de dados em tempo real e ajustar dinamicamente os recursos com pouco ou nenhum tempo de inatividade.

## <a name="azure-sql-database"></a>Banco de Dados SQL do Azure

As equipes de desenvolvimento com expertise no Microsoft SQL Server devem considerar [o Banco de Dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/). É um banco de dados relacional totalmente gerenciado como um serviço (DBaaS) com base no Microsoft SQL Server Database Engine. O serviço compartilha muitos recursos encontrados na versão local do SQL Server e executa a versão estável mais recente do SQL Server Database Engine.

Para uso com um microserviço nativo da nuvem, o Azure SQL Database está disponível com três opções de implantação:

- Um banco de dados único representa um banco de dados SQL totalmente gerenciado em execução em um [servidor de banco de dados SQL do Azure](https://docs.microsoft.com/azure/sql-database/sql-database-servers) na nuvem Azure. O banco de dados é considerado [*contido,*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) pois não possui dependências de configuração no servidor de banco de dados subjacente.
  
- Uma [instância gerenciada](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) é uma instância totalmente gerenciada do Microsoft SQL Server Database Engine que fornece quase 100% de compatibilidade com um SQL Server no local. Essa opção suporta bancos de dados maiores, de até 35 TB e é colocado em uma [Rede Virtual Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) para melhor isolamento.

- [O Azure SQL Database serverless](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) é um nível de computação para um único banco de dados que é dimensionado automaticamente com base na demanda de carga de trabalho. Ele cobra apenas a quantidade de cálculo usado por segundo. O serviço é adequado para cargas de trabalho com padrões de uso intermitentes e imprevisíveis, intercalados com períodos de inatividade. O nível de computação sem servidor também pausa automaticamente os bancos de dados durante períodos inativos para que apenas as taxas de armazenamento sejam cobradas. Ele é retomado automaticamente quando a atividade retorna.

Além da tradicional pilha do Microsoft SQL Server, o Azure também apresenta versões gerenciadas de três bancos de dados de código aberto populares.

## <a name="open-source-databases-in-azure"></a>Bancos de dados de código aberto no Azure

Os bancos de dados relacionais de código aberto tornaram-se uma escolha popular para aplicativos nativos da nuvem. Muitas empresas os favorecem em relação aos produtos de banco de dados comerciais, especialmente pela redução de custos. Muitas equipes de desenvolvimento desfrutam de sua flexibilidade, desenvolvimento apoiado pela comunidade e ecossistema de ferramentas e extensões. Os bancos de dados de código aberto podem ser implantados em vários provedores de nuvem, ajudando a minimizar a preocupação de "bloqueio de fornecedores".

Os desenvolvedores podem facilmente hospedar qualquer banco de dados de código aberto em uma VM Azure. Ao mesmo tempo em que fornece controle total, essa abordagem coloca você no gancho para o gerenciamento, monitoramento e manutenção do banco de dados e VM.

No entanto, a Microsoft continua seu compromisso de manter o Azure uma "plataforma aberta" oferecendo vários bancos de dados de código aberto populares como serviços DBaaS *totalmente gerenciados.*

### <a name="azure-database-for-mysql"></a>Banco de Dados do Azure para MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) é um banco de dados relacional de código aberto e um pilar para aplicações construídas na [pilha de software LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)). Amplamente escolhido para ler cargas de trabalho *pesadas,* é usado por muitas grandes organizações, incluindo Facebook, Twitter e YouTube. A edição comunitária está disponível gratuitamente, enquanto a edição corporativa requer uma compra de licença. Originalmente criado em 1995, o produto foi comprado pela Sun Microsystems em 2008. A Oracle adquiriu a Sun e a MySQL em 2010.

[O Azure Database for MySQL](https://azure.microsoft.com/services/mysql/) é um serviço de banco de dados relacional gerenciado com base no mecanismo MySQL Server de código aberto. Ele usa a edição MySQL Community. O servidor Azure MySQL é o ponto administrativo do serviço. É o mesmo mecanismo de servidor MySQL usado para implantações no local. O mecanismo pode criar um único banco de dados por servidor ou vários bancos de dados por servidor que compartilham recursos. Você pode continuar a gerenciar dados usando as mesmas ferramentas de código aberto sem ter que aprender novas habilidades ou gerenciar máquinas virtuais.

### <a name="azure-database-for-mariadb"></a>Banco de Dados do Azure para MariaDB

[MariaDB](https://mariadb.com/) O Servidor é outro servidor de banco de dados de código aberto popular. Foi criado como um *garfo* do MySQL quando a Oracle comprou a Sun Microsystems, dona da MySQL. A intenção era garantir que o MariaDB permanecesse de código aberto. Como o MariaDB é um garfo do MySQL, as definições de dados e tabelas são compatíveis, e os protocolos, estruturas e APIs do cliente são próximos.

A MariaDB tem uma comunidade forte e é usada por muitas grandes empresas. Enquanto a Oracle continua a manter, aprimorar e apoiar o MySQL, a fundação MariaDB gerencia o MariaDB, permitindo contribuições públicas para o produto e documentação.

[O Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) é um banco de dados relacional totalmente gerenciado como um serviço na nuvem Azure. O serviço é baseado no mecanismo de servidor de edição comunitária do MariaDB. Ele pode lidar com cargas de trabalho essenciais com desempenho previsível e escalabilidade dinâmica.

### <a name="azure-database-for-postgresql"></a>Banco de Dados do Azure para PostgreSQL

[PostgreSQL](https://www.postgresql.org/) é um banco de dados relacional de código aberto com mais de 30 anos de desenvolvimento ativo. PostgresSQL tem uma forte reputação de confiabilidade e integridade de dados. É rico em recursos, compatível com SQL e considerado mais desempenho do que o MySQL - especialmente para cargas de trabalho com consultas complexas e gravações pesadas. Muitas grandes empresas, incluindo Apple, Red Hat e Fujitsu, construíram produtos usando o PostgreSQL.

[O Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) é um serviço de banco de dados relacional totalmente gerenciado, baseado no mecanismo de banco de dados postgres de código aberto. O serviço suporta muitas plataformas de desenvolvimento, incluindo C++,\#Java, Python, Node, C e PHP. Você pode migrar os bancos de dados PostgreSQL para ele usando a ferramenta [de interface de linha de comando](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) ou o Azure Data Migration Service.

O Banco de Dados Azure para PostgreSQL está disponível com duas opções de implantação:

- A opção de implantação [do Servidor Único](https://docs.microsoft.com/azure/postgresql/concepts-servers) é um ponto administrativo central para vários bancos de dados aos quais você pode implantar muitos bancos de dados. Os preços são estruturados por servidor com base em núcleos e armazenamento.

- A [opção Hyperscale (Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) é alimentada pela tecnologia Citus Data. Ele permite um alto *desempenho, dimensionando horizontalmente* um único banco de dados em centenas de nós para fornecer desempenho e escala rápidos. Essa opção permite que o mecanismo encaixe mais dados na memória, paraparalize consultas em centenas de nós e indexe dados mais rapidamente.

## <a name="nosql-data-in-azure"></a>Dados NoSQL no Azure

Cosmos DB é um serviço de banco de dados NoSQL totalmente gerenciado e distribuído globalmente na nuvem Azure. Foi adotado por muitas grandes empresas em todo o mundo, incluindo Coca-Cola, Skype, ExxonMobil e Liberty Mutual.

Se seus serviços exigem resposta rápida de qualquer lugar do mundo, alta disponibilidade ou escalabilidade elástica, o Cosmos DB é uma ótima escolha. A Figura 5-12 mostra cosmos DB.

![Visão geral do Cosmos DB](./media/cosmos-db-overview.png)

**Figura 5-12**: Visão geral do Cosmos DB

A figura anterior apresenta muitas das capacidades nativas da nuvem incorporadas disponíveis no Cosmos DB. Nesta seção, vamos dar uma olhada mais de perto neles.

### <a name="global-support"></a>Suporte global

Aplicativos nativos da nuvem geralmente têm uma audiência global e exigem escala global.

Você pode distribuir bancos de dados cosmos em regiões ou em todo o mundo, colocando dados próximos aos seus usuários, melhorando o tempo de resposta e reduzindo a latência. Você pode adicionar ou remover um banco de dados de uma região sem pausar ou reimplantar seus serviços. No plano de fundo, o Cosmos DB replica os dados de forma transparente em cada uma das regiões configuradas.

O Cosmos DB suporta clustering [ativo/ativo](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) em nível global, permitindo que você configure qualquer uma de suas regiões de banco de dados para suportar *gravações e leituras.*

O protocolo [Multi-Master](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) é um recurso importante no Cosmos DB que permite a seguinte funcionalidade:

- Gravação elástica ilimitada e escalabilidade de leitura.

- 99,999% de leitura e gravação de disponibilidade em todo o mundo.

- Garantia de leituras e gravações atendidas em menos de 10 milissegundos no percentil 99.

Com as [APIs Multi-Homing](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)do Cosmos DB, seu microserviço está automaticamente ciente da região azure mais próxima e envia solicitações para ele. A região mais próxima é identificada pelo Cosmos DB sem alterações de configuração. Se uma região ficar indisponível, o recurso Multi-Homing encaminhará automaticamente as solicitações para a próxima região disponível.

### <a name="multi-model-support"></a>Suporte a vários modelos

Ao replataformar aplicativos monolíticos para uma arquitetura nativa da nuvem, as equipes de desenvolvimento às vezes têm que migrar de código aberto, armazenamentode dados NoSQL. O Cosmos DB pode ajudá-lo a preservar seu investimento nestes datastores NoSQL com sua plataforma de dados *multimodelo.* A Figura 5-13 mostra as [APIs de compatibilidade](https://www.wikiwand.com/en/Cosmos_DB)NoSQL suportadas .

![Provedores de DB do Cosmos](./media/cosmos-db-providers.png)

**Figura 5-13**: Provedores de Cosmos DB

As equipes de desenvolvimento podem migrar os bancos de dados Existentes de Mongo, Gremlin ou Cassandra para o Cosmos DB com alterações mínimas nos dados ou códigos. Para novos aplicativos, as equipes de desenvolvimento podem escolher entre opções de código aberto ou o modelo de API SQL incorporado.

> Internamente, a Cosmos armazena os dados em um formato simples de estruturação composto por tipos de dados primitivos. Para cada solicitação, o mecanismo de banco de dados traduz os dados primitivos para a representação do modelo que você selecionou.

No valor anterior, 5-13, observe a opção [Tabela API.](https://docs.microsoft.com/azure/cosmos-db/table-introduction) Esta API é uma evolução do Armazenamento de Tabelas Do Azure. Ambos compartilham o mesmo modelo de tabela subjacente, mas a API da Tabela Cosmos DB adiciona aprimoramentos premium não disponíveis na API de armazenamento do Azure. Essas características são contrastadas na Figura 5-4.

![API de Tabela do Azure](media/azure-table-api.png)

**Figura 5-14**: Provedores de API de tabela azure

Microserviços que consomem o armazenamento de tabela do Azure podem migrar facilmente para a API de tabela do Cosmos DB. Nenhuma alteração de código é necessária.

### <a name="tunable-consistency"></a>Consistência ajustável

Mais cedo, na seção *Relacional vs. NoSQL,* discutimos o tema da consistência dos *dados*. A consistência dos dados refere-se à *integridade* de seus dados. Os serviços nativos da nuvem com dados distribuídos dependem da replicação e devem fazer uma troca fundamental entre consistência de leitura, disponibilidade e latência.

A maioria dos bancos de dados distribuídos permite que os desenvolvedores escolham entre dois modelos de consistência: consistência forte e eventual consistência. *Forte consistência* é o padrão ouro da programação de dados. Ele garante que uma consulta sempre retornará os dados mais atuais - mesmo que o sistema deva incorrer em latência à espera de uma atualização para se replicar em todas as cópias do banco de dados. Enquanto um banco de dados configurado para *eventual consistência* retornará os dados imediatamente, mesmo que esses dados não sejam a cópia mais atual. Esta última opção permite maior disponibilidade, maior escala e maior desempenho.

O Azure Cosmos DB oferece cinco modelos de consistência bem [definidos mostrados](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) na Figura 5-15.

![Gráfico de consistência do Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Figura 5-15**: Cosmos DB Níveis de consistência

 Essas opções permitem que você faça escolhas precisas e compensações granulares para consistência, disponibilidade e desempenho de seus dados. A Figura 5-16 descreve cada nível.

![Níveis de consistência do Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Figura 5-16**: Descrição do nível de consistência do Cosmos DB

No artigo [Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), Microsoft Cloud Developer Advocate Jeremy Likeness fornece uma excelente explicação dos cinco modelos.

### <a name="partitioning"></a>Particionamento

O Azure Cosmos DB adota [particionamento](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) automático para dimensionar um banco de dados para atender às necessidades de desempenho de seus serviços nativos na nuvem.

Você gerencia dados em dados do Cosmos DB criando bancos de dados, contêineres e itens.

Os contêineres vivem em um banco de dados do Cosmos DB e representam um agrupamento esquema-agnóstico de itens. Os itens são os dados que você adiciona ao contêiner. Eles são representados como documentos, linhas, nódulos ou bordas. Todos os itens adicionados a um contêiner são automaticamente indexados.

Para particionar o contêiner, os itens são divididos em subconjuntos distintos chamados partições lógicas. As partições lógicas são preenchidas com base no valor de uma chave de partição associada a cada item em um contêiner. A Figura 5-18 mostra dois contêineres cada um com uma partição lógica baseada em um valor-chave de partição.

![Mecânica de particionamento do Cosmos DB](./media/cosmos-db-partitioning.png)

**Figura 5-18**: Mecânica de particionamento Cosmos DB

Observe na figura anterior como cada item inclui uma chave de partição de 'cidade' ou 'aeroporto'. A chave determina a partição lógica do item. Itens com um código da cidade são atribuídos ao contêiner à esquerda, e itens com um código do aeroporto, para o contêiner à direita. A combinação do valor da chave de partição com o valor de ID cria o índice de um item, que identifica exclusivamente o item.

Internamente, o Cosmos DB gerencia automaticamente a colocação de [partições lógicas](https://docs.microsoft.com/azure/cosmos-db/partition-data) em partições físicas para satisfazer as necessidades de escalabilidade e desempenho do contêiner. À medida que os requisitos de throughput e armazenamento do aplicativo aumentam, o Azure Cosmos DB redistribui partições lógicas em um maior número de servidores. As operações de redistribuição são gerenciadas pela Cosmos DB e invocadas sem interrupção ou tempo de inatividade.

## <a name="newsql-databases"></a>Bancos de dados NewSQL

*NewSQL* é uma tecnologia de banco de dados emergente que combina a escalabilidade distribuída do NoSQL com as garantias ACID de um banco de dados relacional. Os bancos de dados NewSQL são importantes para sistemas de negócios que devem processar grandes volumes de dados, em ambientes distribuídos, com suporte transacional completo e conformidade ACID. Embora um banco de dados NoSQL possa fornecer escalabilidade maciça, ele não garante a consistência dos dados. Problemas intermitentes de dados inconsistentes podem colocar um fardo na equipe de desenvolvimento. Os desenvolvedores devem construir salvaguardas em seu código de microserviço para gerenciar problemas causados por dados inconsistentes.

A Cloud Native Computing Foundation (CNCF) apresenta vários projetos de banco de dados NewSQL.

| Project | Características |
| :-------- | :-------- |
| Barata DB |Um banco de dados relacional compatível com ÁCIDO que se dimensiona globalmente. Adicione um novo nó a um cluster e o CockroachDB se preocupa em equilibrar os dados entre instâncias e geografias. Ele cria, gerencia e distribui réplicas para garantir a confiabilidade. É de código aberto e livremente disponível.  |
| TiDB | Um banco de dados de código aberto que suporta cargas de trabalho híbridas transacionais e de processamento analítico (HTAP). É compatível com MySQL e possui escalabilidade horizontal, forte consistência e alta disponibilidade.  O TiDB age como um servidor MySQL. Você pode continuar a usar bibliotecas de clientes MySQL existentes, sem exigir extensas alterações de código em seu aplicativo. |
| YugabyteDB | Um banco de dados SQL distribuído de código aberto, de alto desempenho. Suporta baixa latência de consulta, resiliência contra falhas e distribuição global de dados. O YugabyteDB é compatível com PostgressSQL e lida com a escala de RDBMS e cargas de trabalho OLTP em escala de internet. O produto também suporta NoSQL e é compatível com Cassandra. |
|Vitess | Vitess é uma solução de banco de dados para implantação, dimensionamento e gerenciamento de grandes clusters de instâncias MySQL. Pode ser executado em uma arquitetura de nuvem pública ou privada. Ele combina e estende muitos recursos importantes do MySQL e apresenta suporte de fragmentação vertical e horizontal. Originada pelo YouTube, a Vitess atende todo o tráfego de banco de dados do YouTube desde 2011 . |

Os projetos de código aberto na figura anterior estão disponíveis na Cloud Native Computing Foundation. Três das ofertas são produtos completos de banco de dados, que incluem suporte ao .NET Core. O outro, Vitess, é um sistema de clustering de banco de dados que escala horizontalmente grandes clusters de instâncias MySQL.

Um dos principais objetivos de design para os bancos de dados NewSQL é trabalhar nativamente em Kubernetes, aproveitando a resiliência e escalabilidade da plataforma.

Os bancos de dados NewSQL são projetados para prosperar em ambientes de nuvem efêmeros onde máquinas virtuais subjacentes podem ser reiniciadas ou reagendadas a qualquer momento. Os bancos de dados são projetados para sobreviver a falhas de nó sem perda de dados ou tempo de inatividade. O CockroachDB, por exemplo, é capaz de sobreviver a uma perda de máquina mantendo três réplicas consistentes de quaisquer dados através dos álos em um cluster.

O Kubernetes usa um *conjunto de serviços* para permitir que um cliente aborde um grupo de processos de bancos de dados NewSQL idênticos a partir de uma única entrada de DNS. Ao desacoplar as instâncias do banco de dados do endereço do serviço com o qual ele está associado, podemos dimensionar sem interromper as instâncias de aplicativos existentes. Enviar uma solicitação a qualquer serviço em um determinado momento sempre produzirá o mesmo resultado.

Neste cenário, todas as instâncias de banco de dados são iguais. Não há relações primárias ou secundárias. Técnicas como *a replicação de consenso* encontrada no CockroachDB permitem que qualquer nó de banco de dados lide com qualquer solicitação. Se o nó que recebe uma solicitação balanceada de carga tiver os dados necessários localmente, ele responderá imediatamente. Caso assim, o nó se torne um gateway e encaminhe a solicitação aos nós apropriados para obter a resposta correta. Do ponto de vista do cliente, cada nó de banco de dados é o mesmo: eles aparecem como um único banco de dados *lógico* com as garantias de consistência de um sistema de uma máquina única, apesar de ter dezenas ou até centenas de nós que estão trabalhando nos bastidores.

Para obter uma olhada detalhada na mecânica por trás dos bancos de dados NewSQL, consulte o artigo [DASH: Four Properties of Kubernetes-Native Databases.](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

## <a name="data-migration-to-the-cloud"></a>Migração de dados para a nuvem

Uma das tarefas mais demoradas é migrar dados de uma plataforma de dados para outra. O [Serviço de Migração de Dados do Azure](https://azure.microsoft.com/services/database-migration/) pode ajudar a acelerar esses esforços. Ele pode migrar dados de várias fontes de banco de dados externos para plataformas azure Data com tempo mínimo de inatividade. As plataformas-alvo incluem os seguintes serviços:

- Banco de Dados SQL do Azure
- Banco de Dados do Azure para MySQL
- Banco de Dados do Azure para MariaDB
- Banco de Dados do Azure para PostgreSQL
- CosmosDB
  
O serviço fornece recomendações para guiá-lo através das alterações necessárias para executar uma migração, tanto pequena quanto grande.

>[!div class="step-by-step"]
>[Próximo](database-per-microservice.md)
>[anterior](azure-caching.md)
