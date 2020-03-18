---
title: Banco de dados por microsserviço
description: Contraste o armazenamento de dados em aplicativos monolíticos e nativos da nuvem.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c0c5611fa866d70f155e4bdad2eee1181b13c065
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141439"
---
# <a name="database-per-microservice"></a>Banco de dados por microsserviço

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Como vimos ao longo deste livro, uma abordagem nativa da nuvem muda a maneira como você projeta, implanta e gerencia aplicativos. Também muda a forma como você gerencia e armazena dados.

A Figura 5-1 contrasta as diferenças.

![Armazenamento de dados em aplicativos nativos da nuvem](./media/distributed-data.png)

**Figura 5-1**. Gerenciamento de dados em aplicativos nativos da nuvem

Desenvolvedores experientes reconhecerão facilmente a arquitetura no lado esquerdo da figura 5-1. Nesta *aplicação monolítica,* os componentes de serviços de negócios se agrupam em um nível de serviços compartilhados, compartilhando dados de um único banco de dados relacional.

Em muitos aspectos, um único banco de dados mantém o gerenciamento de dados simples. Consultar dados em várias tabelas é simples. Alterações na atualização de dados em conjunto ou todas elas reversão. [As transações ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) garantem consistência forte e imediata.

Projetando para nativos da nuvem, tomamos uma abordagem diferente. No lado direito da Figura 5-1, observe como a funcionalidade do negócio se segrega em microsserviços pequenos e independentes. Cada microserviço encapsula uma capacidade de negócios específica e seus próprios dados. O banco de dados monolítico se decompõe em um modelo de dados distribuídos com muitos bancos de dados menores, cada um alinhado a um microserviço. Quando a fumaça se dissipa, emergimos com um design que expõe um *banco de dados por microserviço.*

## <a name="why"></a>Por quê?

Este banco de dados por microserviço oferece muitos benefícios, especialmente para sistemas que devem evoluir rapidamente e suportar escala maciça. Com este modelo...

- Os dados de domínio são encapsulados dentro do serviço
- Esquema de dados pode evoluir sem impactar diretamente outros serviços
- Cada armazenamento de dados pode dimensionar independentemente
- Uma falha no armazenamento de dados em um serviço não afetará diretamente outros serviços

A segregação de dados também permite que cada microserviço implemente o tipo de armazenamento de dados que é melhor otimizado para sua carga de trabalho, necessidades de armazenamento e padrões de leitura/gravação. As opções incluem armazenamentos de dados relacionais, documentos, de valor-chave e até mesmo de gráficos.

A Figura 5-2 apresenta o princípio da persistência do poliglota em um sistema nativo da nuvem.

![Persistência de dados poliglotas](./media/polyglot-data-persistence.png)

**Figura 5-2**. Persistência de dados poliglotas

Observe na figura anterior como cada microserviço suporta um tipo diferente de armazenamento de dados.

- O microserviço do catálogo de produtos consome um banco de dados relacional para acomodar a rica estrutura relacional de seus dados subjacentes.
- O microserviço do carrinho de compras consome um cache distribuído que suporta seu simples armazenamento de dados de valor-chave.
- O microserviço de pedidos consome tanto um banco de dados de documentos NoSql para operações de gravação, juntamente com uma loja de chaves/valor altamente desnormalizada para acomodar grandes volumes de operações de leitura.
  
Embora as bases de dados relacionais permaneçam relevantes para microserviços com dados complexos, os bancos de dados NoSQL ganharam considerável popularidade. Eles fornecem escala maciça e alta disponibilidade. Sua natureza sem esquemas permite que os desenvolvedores se afastem de uma arquitetura de classes de dados digitadas e ORMs que tornam a mudança cara e demorada. Nós cobrimos bancos de dados NoSQL mais tarde neste capítulo.

 Embora encapsular dados em microsserviços separados possa aumentar a agilidade, o desempenho e a escalabilidade, ele também apresenta muitos desafios. Na próxima seção, discutimos esses desafios juntamente com padrões e práticas para ajudar a superá-los.  

## <a name="cross-service-queries"></a>Consultas de serviço cruzado

Embora os microserviços sejam independentes e se concentrem em recursos funcionais específicos, como inventário, envio ou encomenda, eles frequentemente requerem integração com outros microserviços. Muitas vezes, a integração envolve um microserviço *consultando* outro para dados. A Figura 5-3 mostra o cenário.

![Consultando microsserviços](./media/cross-service-query.png)

**Figura 5-3**. Consultando microsserviços

No número anterior, vemos um microserviço de cesta de compras que adiciona um item à cesta de compras do usuário. Embora o armazenamento de dados para este microserviço contenha dados de cesta e item de linha, ele não mantém dados de produtos ou preços. Em vez disso, esses itens de dados são de propriedade do catálogo e dos microsserviços de preços. Isso apresenta um problema. Como o microserviço da cesta de compras pode adicionar um produto à cesta de compras do usuário quando ele não tem produtos nem dados de preços em seu banco de dados?

Uma opção discutida no Capítulo 4 é uma [chamada HTTP direta](service-to-service-communication.md#queries) da cesta de compras para o catálogo e microsserviços de preços. No entanto, no capítulo 4, dissemos que o HTTP síncrono chama os microsserviços *de casal* juntos, reduzindo sua autonomia e diminuindo seus benefícios arquitetônicos.

Também podemos implementar um padrão de solicitação-resposta com filas separadas de entrada e saída para cada serviço. No entanto, esse padrão é complicado e requer encanamento para correlacionar mensagens de solicitação e resposta.
Embora isso desacopla as chamadas de microserviço back-end, o serviço de chamada ainda deve aguardar sincronizadamente a chamada ser concluída. Congestionamento da rede, falhas transitórias ou um microserviço sobrecarregado e pode resultar em operações de longa duração e até mesmo fracassadas.

Em vez disso, um padrão amplamente aceito para remover dependências de serviço cruzado é o [Padrão de Exibição Materializado,](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)mostrado na Figura 5-4.

![Padrão de visualização materializado](./media/materialized-view-pattern.png)

**Figura 5-4**. Padrão de exibição materializado

Com este padrão, você coloca uma tabela de dados local (conhecida como *modelo de leitura*) no serviço de cesta de compras. Esta tabela contém uma cópia desnormalizada dos dados necessários do produto e dos microsserviços de preços. Copiar os dados diretamente no microserviço da cesta de compras elimina a necessidade de chamadas de serviço saqueadas caras. Com os dados locais para o serviço, você melhora o tempo de resposta e a confiabilidade do serviço. Além disso, ter sua própria cópia dos dados torna o serviço de cesta de compras mais resistente. Se o serviço de catálogo ficar indisponível, não afetaria diretamente o serviço de cesta de compras. A cesta de compras pode continuar operando com os dados de sua própria loja.

A pegadinha com essa abordagem é que agora você tem dados duplicados em seu sistema. No entanto, a duplicação *estratégica* de dados em sistemas nativos da nuvem é uma prática estabelecida e não considerada um antipadrão ou uma prática ruim. Tenha em mente que *um e apenas um serviço* pode possuir um conjunto de dados e ter autoridade sobre ele. Você precisará sincronizar os modelos de leitura quando o sistema de registro for atualizado. A sincronização é normalmente implementada através de mensagens assíncronas com um [padrão de publicação/assinatura,](service-to-service-communication.md#events)conforme mostrado na Figura 5.4.

## <a name="distributed-transactions"></a>Transações distribuídas

Embora a consulta de dados em microsserviços seja difícil, implementar uma transação em vários microsserviços é ainda mais complexo. O desafio inerente de manter a consistência dos dados entre fontes de dados independentes em diferentes microsserviços não pode ser subestimado. A falta de transações distribuídas em aplicativos nativos da nuvem significa que você deve gerenciar as transações distribuídas de forma programática. Você passa de um mundo de *consistência imediata* para o de *consistência eventual.*

A Figura 5-5 mostra o problema.

![Transação no padrão saga](./media/saga-transaction-operation.png)

**Figura 5-5**. Implementação de uma transação em microsserviços

No número anterior, cinco microsserviços independentes participam de uma transação distribuída que cria um pedido. Cada microserviço mantém seu próprio armazenamento de dados e implementa uma transação local para sua loja. Para criar o pedido, a transação local para *cada* microserviço individual deve ter sucesso, ou *todos* devem abortar e reverter a operação. Embora o suporte transacional incorporado esteja disponível dentro de cada um dos microserviços, não há suporte para uma transação distribuída que se estenderia por todos os cinco serviços para manter os dados consistentes.

Em vez disso, você deve construir esta transação distribuída *de forma programática.*

Um padrão popular para adicionar suporte transacional distribuído é o padrão Saga. É implementado agrupando transações locais de forma programática e sequencial invocando cada uma delas. Se alguma das transações locais falhar, a Saga aborta a operação e invoca um conjunto de [transações compensatórias.](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) As transações compensatórias desfazem as alterações feitas pelas transações locais anteriores e restauram a consistência dos dados. A Figura 5-6 mostra uma transação fracassada com o padrão Saga.

![Reverter para trás no padrão da saga](./media/saga-rollback-operation.png)

**Figura 5-6**. Revertendo uma transação

No número anterior, a operação *Inventário de Atualização* falhou no microserviço Inventário. A Saga invoca um conjunto de transações compensatórias (em vermelho) para ajustar as contagens de estoque, cancelar o pagamento e a ordem e devolver os dados de cada microserviço de volta a um estado consistente.

Padrões de saga são tipicamente coreografados como uma série de eventos relacionados, ou orquestrados como um conjunto de comandos relacionados. No Capítulo 4, discutimos o padrão agregador de serviços que seria a base para uma implementação orquestrada da saga. Também discutimos o evento juntamente com os tópicos Azure Service Bus e Azure Event Grid que seriam a base para uma implementação coreografada da saga.

## <a name="high-volume-data"></a>Dados de alto volume

Grandes aplicativos nativos da nuvem geralmente suportam requisitos de dados de alto volume. Nesses cenários, as técnicas tradicionais de armazenamento de dados podem causar gargalos. Para sistemas complexos que são implantados em larga escala, tanto a Segregação de Responsabilidade de Comando e Consulta (CQRS) quanto o Sourcing de Eventos podem melhorar o desempenho do aplicativo.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs), é um padrão arquitetônico que pode ajudar a maximizar o desempenho, escalabilidade e segurança. O padrão separa as operações que leem dados das operações que escrevem dados.

Para cenários normais, o mesmo modelo de entidade e o objeto de repositório de dados são usados para operações *de* leitura e gravação.

No entanto, um cenário de dados de alto volume pode beneficiar de modelos e tabelas de dados separados para leituras e gravações. Para melhorar o desempenho, a operação leitura poderia consultar uma representação altamente desnormalizada dos dados para evitar adesões de tabela repetitivas caras e bloqueios de mesa. A operação *de gravação,* conhecida como *comando,* seria atualizada contra uma representação totalmente normalizada dos dados que garantiriam consistência. Em seguida, você precisa implementar um mecanismo para manter ambas as representações em sincronia. Normalmente, sempre que a tabela de gravação é modificada, ela publica um evento que replica a modificação na tabela de leitura.

A Figura 5-7 mostra uma implementação do padrão CQRS.

![Segregação de Responsabilidade de Comando e Consulta](./media/cqrs-implementation.png)

**Figura 5-7**. Implementação do CQRS

Na figura anterior, modelos separados de comando e consulta são implementados. Cada operação de gravação de dados é salva no armazenamento de gravação e, em seguida, propagada para o armazenamento de leitura. Preste muita atenção em como o processo de propagação de dados opera no princípio da [eventual consistência](http://www.cloudcomputingpatterns.org/eventual_consistency/). O modelo de leitura eventualmente sincroniza com o modelo de gravação, mas pode haver alguma defasagem no processo. Discutimos uma eventual consistência na próxima seção.

Esta separação permite que leituras e gravações dimensionem de forma independente. As operações de leitura usam um esquema otimizado para consultas, enquanto as gravações usam um esquema otimizado para atualizações. As consultas de leitura vão contra dados desnormalizados, enquanto a lógica de negócios complexa pode ser aplicada ao modelo de gravação. Além disso, você pode impor mais segurança nas operações de gravação do que aquelas que expõem leituras.

A implementação do CQRS pode melhorar o desempenho do aplicativo para serviços nativos da nuvem. No entanto, resulta em um design mais complexo. Aplique este princípio cuidadosamente e estrategicamente às seções do seu aplicativo nativo da nuvem que se beneficiarão dele. Para obter mais informações sobre o CQRS, consulte o livro da Microsoft [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Sourcing de eventos

Outra abordagem para otimizar cenários de dados de alto volume envolve [o Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

Um sistema normalmente armazena o estado atual de uma entidade de dados. Se um usuário altera seu número de telefone, por exemplo, o registro do cliente é atualizado com o novo número. Sempre sabemos o estado atual de uma entidade de dados, mas cada atualização substitui o estado anterior.

Na maioria dos casos, esse modelo funciona bem. Em sistemas de alto volume, no entanto, a sobrecarga de operações de bloqueio transacional e de atualização frequentes pode afetar o desempenho do banco de dados, a capacidade de resposta e a escalabilidade de limite.

O Event Sourcing adota uma abordagem diferente para capturar dados. Cada operação que afeta os dados é persistindo a um armazenamento de eventos. Em vez de atualizar o estado de um registro de dados, anexamos cada alteração a uma lista seqüencial de eventos passados - semelhante ao livro-razão de um contador. O Event Store torna-se o sistema de registro dos dados. É usado para propagar várias visões materializadas dentro do contexto limitado de um microserviço. A Figura 5.8 mostra o padrão.

![Fornecimento do evento](./media/event-sourcing.png)

**Figura 5-8**. Fornecimento do evento

Na figura anterior, observe como cada entrada (em azul) para o carrinho de compras de um usuário é anexada a uma loja de eventos subjacente. Na visão materializada adjacente, o sistema projeta o estado atual reproduzindo todos os eventos associados a cada carrinho de compras. Esta visão, ou modelo de leitura, é então exposta de volta à ui. Os eventos também podem ser integrados a sistemas e aplicações externas ou consultados para determinar o estado atual de uma entidade. Com essa abordagem, você mantém a história. Você sabe não só o estado atual de uma entidade, mas também como você chegou a este estado.

Mecanicamente falando, o sourcing de eventos simplifica o modelo de gravação. Não há atualizações ou exclusões. Anexar cada entrada de dados como um evento imutável minimiza conflitos de contenção, bloqueio e concorrência associados a bancos de dados relacionais. Construir modelos de leitura com o padrão de visualização materializado permite desacoplar a exibição do modelo de gravação e escolher o melhor armazenamento de dados para otimizar as necessidades da interface do motorista do seu aplicativo.

Para esse padrão, considere um armazenamento de dados que suporte diretamente o sourcing de eventos. Azure Cosmos DB, MongoDB, Cassandra, CouchDB e RavenDB são bons candidatos.

Como em todos os padrões e tecnologias, implementar estrategicamente e quando necessário. Embora o sourcing de eventos possa proporcionar maior desempenho e escalabilidade, ele vem às custas da complexidade e de uma curva de aprendizado.

>[!div class="step-by-step"]
>[Próximo](service-mesh-communication-infrastructure.md)
>[anterior](relational-vs-nosql-data.md)
