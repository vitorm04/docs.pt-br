---
title: Padrões de dados nativos de nuvem
description: Arquitetando aplicativos .NET nativos da nuvem para o Azure | Padrões de dados nativos de nuvem
ms.date: 06/30/2019
ms.openlocfilehash: 9e90409b0b633796b452cfcfecb3896e79002d4d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337417"
---
# <a name="cloud-native-data-patterns"></a>Padrões de dados nativos de nuvem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Embora os dados descentralizados possam levar a um melhor desempenho, escalabilidade e economia de custos, ele também apresenta muitos desafios. Consultar dados em microservices é complexo. Uma transação que abrange microservices deve ser gerenciada programaticamente, pois as transações distribuídas não têm suporte em aplicativos nativos de nuvem. Você passa de um mundo de *consistência imediata* para *consistência eventual*.

Discutimos esses desafios agora.

## <a name="cross-service-queries"></a>Consultas entre serviços

Como um aplicativo consulta dados que se espalham por muitos microservices independentes?

A Figura 5-4 mostra esse cenário.

![Consultando em microserviços](./media/cross-service-query.png)

**Figura 5-4**. Consultando em microserviços

Observe como na figura anterior, vemos um microserviço de cesta de compras que adiciona um item ao carrinho de compras de um usuário. Embora o armazenamento de dados da cesta de compras contenha uma tabela basket e lineItem, ela não contém dados de produtos ou preços, pois esses itens são encontrados nos microserviços de produto e preço. Para adicionar um item, o microserviço da cesta de compras precisa de dados de produtos e dados de preços. Quais são as opções para obter os dados de produto e preço?

A Figura 5-5 mostra o microserviço da cesta de compras fazendo uma chamada HTTP direta para o catálogo de produtos e os microserviços de preços.

![Comunicação direta de http](./media/direct-http-communication.png)

**Figura 5-5**. Comunicação direta de HTTP

Embora seja possível implementar, no capítulo 4, discutimos como chamadas HTTP diretas em todos os microserviços associam o sistema e não são consideradas uma boa prática.

Poderíamos implementar um microserviço agregador mostrado na Figura 5-6.

![Microserviço agregador](./media/aggregator-microservice.png)

**Figura 5-6.** Microserviço agregador

Embora essa abordagem encapsula o fluxo de trabalho de operações de negócios em um microserviço individual, ela adiciona complexidade e ainda resulta em chamadas HTTP diretas.

Uma abordagem comum para executar consultas entre serviços usa o [padrão de exibição materializado](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), mostrado na Figura 5-7.

![Padrão de exibição materializada](./media/materialized-view-pattern.png)

**Figure5-7**. Padrão de exibição materializada

Com esse padrão, você coloca diretamente uma tabela local (conhecida como *modelo de leitura*) no serviço de cesta de compras que contém uma cópia desnormalizada dos dados necessários dos microserviços de produto e preço. Colocar esses dados dentro do microserviço da cesta de compras elimina a necessidade de invocar chamadas caras entre serviços. Com os dados locais para o serviço, você melhora o tempo de resposta e a confiabilidade.

O problema dessa abordagem é que agora você tem dados duplicados em seu sistema. Em sistemas nativos de nuvem, os dados duplicados não são considerados um [antipadrão](https://en.wikipedia.org/wiki/Anti-pattern) e normalmente são implementados em sistemas nativos de nuvem. No entanto, um e apenas um sistema pode ser o proprietário de qualquer conjunto de dados, e você precisará implementar um mecanismo de sincronização para o sistema de registro para atualizar todos os modelos de leitura associados, sempre que ocorrer uma alteração em seus dados subjacentes.

## <a name="transactional-support"></a>Suporte transacional

Embora as consultas em microserviço sejam desafiadoras, a implementação de uma transação em microserviços pode ser complexa. O desafio inerente de manter a consistência de dados entre fontes de dados que residem em diferentes microservices não pode ser subestado. A Figura 5-8 mostra o problema.

![Transação no padrão saga](./media/saga-transaction-operation.png)

**Figura 5-8**. Implementando uma transação em microserviços

Observe como na figura anterior, cinco microserviços independentes participam de uma transação de *ordem de criação* distribuída. No entanto, a transação para cada um dos cinco microserviços individuais deve ter sucesso ou todas devem abortar e reverter a operação. Embora o suporte interno transacional esteja disponível dentro de cada um dos microserviços, não há suporte para uma transação distribuída em todos os cinco serviços.

Como o suporte transacional é essencial para essa operação manter os dados consistentes em cada um dos microserviços, você precisa construir programaticamente uma transação distribuída.

Um padrão popular para adicionar programaticamente suporte transacional é o [padrão saga](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/). Ele é implementado por meio do agrupamento de transações locais e invocada sequencialmente cada uma delas. Se uma transação local falhar, o saga anulará a operação e invocará um conjunto de [Transações de compensação](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) para desfazer as alterações feitas pelas transações locais anteriores. A Figura 5-9 mostra uma transação com falha com o padrão saga.

![Reverter no padrão saga](./media/saga-rollback-operation.png)

**Figura 5-9**. Reverter uma transação

Observe como, na figura anterior, a operação *GenerateContent* falhou no microserviço Music. O saga invoca transações de compensação (em vermelho) para remover o conteúdo, cancelar o pagamento e cancelar o pedido, retornando os dados para cada microserviço de volta para um estado consistente.

Os padrões de Saga geralmente são coreografado como uma série de eventos relacionados ou orquestrados como um conjunto de comandos relacionados.

## <a name="cqrs-pattern"></a>Padrão CQRS

O CQRS, ou [separação das operações de comando e de consulta](https://docs.microsoft.com/azure/architecture/patterns/cqrs), é um padrão de arquitetura que separa as operações que lêem os dados daqueles que gravam dados. Esse padrão pode ajudar a maximizar o desempenho, a escalabilidade e a segurança.

Em cenários de acesso a dados normais, você implementa um modelo único (objeto de entidade e de repositório) *que executa operações* de leitura e gravação de dados.

No entanto, um cenário de acesso a dados mais avançado pode se beneficiar de modelos e tabelas de dados separados para leituras e gravações. Para melhorar o desempenho, a operação de leitura, conhecida como *consulta*, pode consultar uma representação altamente desnormalizada dos dados para evitar junções de tabela repetitivas dispendiosas. Enquanto a operação de *gravação* , conhecida como um *comando*, pode ser atualizada em uma representação totalmente normalizada dos dados. Em seguida, você precisaria implementar um mecanismo para manter ambas as representações em sincronia. Normalmente, sempre que a tabela de gravação é modificada, ela gera um evento que Replica a modificação de dados para a tabela de leitura.

A Figura 5-10 mostra uma implementação do padrão CQRS.

![Implementação de CQRS](./media/cqrs-implementation.png)

**Figura 5-10**. Implementação de CQRS

Observe como, na figura anterior, os modelos de comando e consulta separados são implementados. Além disso, cada operação de gravação de dados é salva no armazenamento de gravação e, em seguida, propagada para o repositório de leitura. Preste muita atenção à forma como o processo de propagação opera no princípio da [consistência eventual](https://www.cloudcomputingpatterns.org/eventual_consistency/), enquanto o modelo de leitura eventualmente sincroniza com o modelo de gravação, mas pode haver algum atraso no processo.

Ao implementar a separação, você tem a capacidade de dimensionar leituras e gravações separadamente. Além de isso, você pode impor uma segurança mais rígida em operações de gravação do que aquelas relacionadas a leituras.

Normalmente, os padrões de CQRS são aplicados a seções limitadas do seu sistema com base em necessidades específicas.

## <a name="relational-vs-nosql"></a>Relacional vs NoSQL

O impacto das tecnologias [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) não pode ser sobredimensionado, especialmente para sistemas nativos de nuvem distribuída. A proliferação de novas tecnologias de dados neste espaço interrompeu as soluções que, uma vez, contavam exclusivamente com os bancos dados relacionais.

Por outro lado, os bancos de dados relacionais têm sido uma tecnologia predominante há décadas. Eles são maduros, comprovados e amplamente implementados. Produtos de banco de dados concorrentes, experiência e abounds de ferramentas. Os bancos de dados relacionais fornecem um armazenamento de tabelas relacionadas. Essas tabelas têm um esquema fixo, usam o SQL (linguagem SQL) para gerenciar dados e têm garantias de [Acid](https://www.geeksforgeeks.org/acid-properties-in-dbms/) (também conhecido como atomicidade, consistência, isolamento e durabilidade).

Os bancos de dados não SQL, por outro lado, referem-se a armazenamentos não relacionais de alto desempenho. Eles se destacam em suas características de facilidade de uso, escalabilidade, resiliência e disponibilidade. Em vez de unir tabelas de dados normalizados, o NoSQL armazena dados autodescritivos (sem esquema) normalmente em documentos JSON. Eles não oferecem garantias [Acid](https://www.geeksforgeeks.org/acid-properties-in-dbms/) .

Uma maneira de entender as diferenças entre esses tipos de bancos de dados pode ser encontrada no [Cap teorema](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e), um conjunto de princípios que pode ser aplicado a sistemas distribuídos que armazenam o estado. A Figura 5-11 mostra as três propriedades do CAP teorema.

![Teorema CAP](./media/cap-theorem.png)

**Figura 5-11**. Teorema CAP

O teorema afirma que qualquer sistema de dados distribuído oferecerá uma compensação entre consistência, disponibilidade e tolerância de partição, e que qualquer banco de dado só poderá garantir duas das três propriedades:

- *Consistência*: cada nó no cluster responderá com os dados mais recentes, mesmo que ele exija o bloqueio de uma solicitação até que todas as réplicas sejam atualizadas corretamente.

- *Disponibilidade*: cada nó retornará uma resposta em um período razoável, mesmo se essa resposta não for a data mais recente.

- *Tolerância a partição*: garante que o sistema continuará operando se um nó falhar ou perder a conectividade com outra.

Bancos de dados relacionais exibem consistência e disponibilidade, mas não a tolerância de partição. O particionamento de um banco de dados relacional, como fragmentação, é difícil e pode impactar o desempenho.

Por outro lado, os bancos de dados NoSQL normalmente exibem a tolerância de partição, conhecida como escalabilidade horizontal e alta disponibilidade. Como a extremidade teorema especifica, você só pode ter dois dos três princípios e perde a propriedade de consistência.

Os bancos de dados NoSQL são distribuídos e geralmente dimensionados em servidores de mercadoria. Isso pode fornecer grande disponibilidade, tanto dentro quanto entre regiões geográficas a um custo reduzido. Os dados podem ser particionados e replicados entre esses computadores, ou nós, fornecendo redundância e tolerância a falhas. A desvantagem é a consistência. Uma alteração nos dados em um nó NoSQL pode levar algum tempo para ser propagada para outros nós. Normalmente, um nó de banco de dados NoSQL fornecerá uma resposta imediata a uma consulta, mesmo se os dados que ele está apresentando estiverem obsoletos e ainda não tiverem sido atualizados.

Essa é uma [consistência eventual](https://www.cloudcomputingpatterns.org/eventual_consistency/)conhecida, uma característica de sistemas de dados distribuídos em que não há suporte para transações ACID. É um breve atraso entre a atualização de um item de dados e o tempo necessário para propagar essa atualização para cada um dos nós de réplica. Se você atualizar um item de produto em um banco de dados NoSQL no Estados Unidos, mas, ao mesmo tempo, consultar o mesmo item de dado de um nó de réplica na Europa, você poderá recuperar as informações anteriores do produto-até que o nó Europeu tenha sido atualizado com a alteração do produto. A desvantagem é que, ao fornecer uma [consistência forte](https://en.wikipedia.org/wiki/Strong_consistency), aguardando a atualização de todos os nós de réplica antes de retornar um resultado da consulta, você pode oferecer suporte a enorme escala e volume de tráfego, mas com a possibilidade de apresentar dados mais antigos.

Os bancos de dados NoSQL podem ser categorizados pelos quatro modelos a seguir:

- *Repositório de documentos* (MongoDB, CouchDB, Couchbase): os dados (e metadados correspondentes) são armazenados de forma não relacional em documentos desnormalizados baseados em JSON dentro do banco de dados.

- *Repositório de chave/valor* (Redis, Riak, memcached): os dados são armazenados em pares chave-valor simples com operações do sistema executadas em uma chave de acesso exclusiva que é mapeada para um valor de dados do usuário.

- *Repositório de coluna larga* (HBase, Cassandra): os dados relacionados são armazenados em um formato de coluna como um conjunto de pares de chave/valor aninhados em uma única coluna com dados normalmente recuperados como uma única unidade sem a necessidade de unir várias tabelas.

- *Repositórios de grafo* (neo4j, Titan): os dados são armazenados como uma representação gráfica em um nó junto com as bordas que especificam a relação entre os nós.

Os bancos de dados NoSQL podem ser otimizados para lidar com grandes escalas, especialmente quando os dados são relativamente simples. Considere um banco de dados NoSQL quando:

- Sua carga de trabalho requer uma grande escala e alta simultaneidade.
- Você tem um grande número de usuários.
- Seus dados podem ser expressos simplesmente sem relações.
- Você precisa distribuir geograficamente seus dados.
- Você não precisa de garantias de ACID.
- Será implantado no hardware de mercadoria.

Em seguida, considere um banco de dados relacional quando:

- Suas cargas de trabalho exigem escala de médio a grande porte.
- A simultaneidade não é uma preocupação importante.
- Garantias de ACID são necessárias.
- Os dados são mais bem expressos de forma relacional.
- Seu aplicativo será implantado em hardware grande e high-end.

Em seguida, examinaremos o armazenamento de dados na nuvem do Azure.

>[!div class="step-by-step"]
>[Anterior](distributed-data.md)
>[Próximo](azure-data-storage.md)
