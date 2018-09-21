---
title: Visão geral do Entity Framework
ms.date: 09/17/2018
ms.assetid: a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0
ms.openlocfilehash: 35eb3b1503c8754752662aef0c5101251d60d49c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493500"
---
# <a name="entity-framework-overview"></a>Visão geral do Entity Framework

O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] é um conjunto de tecnologias no ADO.NET que dão suporte ao desenvolvimento de aplicativos de software orientados a dados. Os arquitetos e desenvolvedores de aplicativos orientados a dados lutam com a necessidade de realizar dois objetivos muito diferentes. Precisam modelar as entidades, as relações e a lógica dos problemas de negócios que estão solucionando e também precisam trabalhar com os mecanismos de dados usados para armazenar e recuperar os dados. Os dados podem se estender por vários sistemas de armazenamento, cada um com seus próprios protocolos. Mesmo aplicativos que trabalhem com um único sistema de armazenamento devem balancear os requisitos do sistema de armazenamento com os requisitos de gravação eficiente e código de aplicativo que possa ser mantido.

O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] permite aos desenvolvedores trabalhar com dados na forma de objetos específicos de domínio e propriedades, como os clientes e endereços de clientes, sem se preocupar com as tabelas de banco de dados e colunas onde esses dados são armazenados de base . Com o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], os desenvolvedores podem trabalhar em um nível mais alto de abstração ao lidar com dados e pode criar e manter aplicativos orientados a dados com menos código do que em aplicativos tradicionais. Porque o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] é um componente dos [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)], [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativos podem ser executados em qualquer computador no qual o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] começando com a versão 3.5 SP1 está instalado.

## <a name="give-life-to-models"></a>Dê vida aos modelos
 Uma abordagem de design antiga e comum ao criar um aplicativo ou serviço é a divisão do aplicativo ou serviço em três partes: um modelo de domínio, um modelo lógico e um modelo físico. O modelo de domínio define as entidades e as relações no sistema que está sendo modelado. O modelo lógico de um banco de dados relacional normaliza as entidades e relações em tabelas com restrições de chave estrangeira. O modelo físico aborda os recursos de um mecanismo de dados específico definindo detalhes de armazenamento, como o particionamento e a indexação.

 O modelo físico é refinado pelos administradores de banco de dados para melhorar o desempenho, mas os programadores que escrevem código de aplicativos limitam-se principalmente a trabalhar com o modelo lógico escrevendo consultas SQL e chamando procedimentos armazenados. Os modelos de domínio geralmente são usados como uma ferramenta para capturar e comunicar os requisitos de um aplicativo, geralmente como diagramas inertes, que são exibidos e discutidos nas etapas iniciais de um projeto e em seguida abandonados. Muitas equipes de desenvolvimento ignoram a criação de um modelo conceitual e começam especificando tabelas, colunas e chaves em um banco de dados relacional.

 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dá vida aos modelos de permitir que os desenvolvedores consultem as entidades e relações no modelo de domínio (chamado um *conceitual* modelo no [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]) contando o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] traduzir aqueles operações de comandos específico da fonte de dados. Isso libera os aplicativos de dependências embutidas no código em uma fonte de dados específica.

 Ao trabalhar com Code First, o modelo conceitual está mapeado para o modelo de armazenamento no código. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pode inferir o modelo conceitual com base nos tipos de objeto e configurações adicionais que você define. Os metadados de mapeamento são gerados durante o tempo de execução com base em uma combinação de como você definiu seus tipos de domínio e informações de configurações adicionais que você fornece no código. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gera o banco de dados conforme o necessário com base nos metadados. Para obter mais informações, consulte [criando e mapeando um modelo conceitual](https://go.microsoft.com/fwlink/?LinkID=235382).

 Ao trabalhar com as Ferramentas do Modelo de Dados de Entidade, o modelo conceitual, o modelo de armazenamento e os mapeamentos entre os dois são expressos em esquemas baseados em XML e definidos em arquivos que têm extensões de nome correspondentes:

-   O CSDL (linguagem de definição de esquema conceitual) define o modelo conceitual. O CSDL é o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]da implementação do [modelo de dados de entidade](../../../../../docs/framework/data/adonet/entity-data-model.md). A extensão do arquivo é .csdl.

-   O SSDL (linguagem de definição de esquema de repositório) define o modelo de armazenamento, que também é chamado de modelo lógico. A extensão do arquivo é .ssdl.

-   O MSL (linguagem de especificação de mapeamento) define os mapeamentos entre o armazenamento e os modelos conceituais. A extensão do arquivo é .msl.

O modelo e os mapeamentos de armazenamento podem ser alterados quando necessário sem necessidade de alterações no modelo conceitual, nas classes de dados ou no código do aplicativo. Como os modelos de armazenamento são específicos ao provedor, você pode trabalhar com um modelo conceitual consistente entre várias fontes de dados.

O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usa esse modelo e arquivos de mapeamento para criar, ler, atualizar e excluir operações em entidades e relações no modelo conceitual para operações equivalentes na fonte de dados. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] oferece suporte até mesmo a entidades de mapeamento no modelo conceitual para procedimentos armazenados na fonte de dados. Para obter mais informações, consulte [CSDL, SSDL e MSL especificações](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md).

## <a name="map-objects-to-data"></a>Mapa de objetos para dados
 A programação orientada a objeto impõe um desafio para interagir com os sistemas de armazenamento de dados. Embora a organização das classes com frequência espelhe a organização de tabelas de banco de dados relacional, o ajuste não é perfeito. Com frequência, várias tabelas normalizadas correspondem a uma única classe, e as relações entre classes são representadas de maneira diferente de como as relações entre tabelas são representadas. Por exemplo, para representar o cliente para um pedido de venda, uma classe `Order` pode usar uma propriedade que contém uma referência a uma instância de uma classe `Customer`, enquanto uma linha da tabela `Order` em um banco de dados contém uma coluna (ou conjunto de colunas) de chave estrangeira com um valor que corresponde a um valor de chave primária na tabela `Customer`. Uma classe `Customer` pode ter uma propriedade denominada `Orders` que contém uma coleção de instâncias da classe `Order`, enquanto a tabela `Customer` em um banco de dados não tem nenhuma coluna comparável. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fornece aos desenvolvedores a flexibilidade de representar relações dessa maneira ou de modelar relações de maneira mais restrita conforme são representadas no banco de dados.

 As soluções existentes tentaram preencher essa lacuna, que é frequentemente chamada de “incompatibilidade de impedância”, mapeando apenas classes e propriedades orientados a objetos para tabelas e colunas relacionais. Em vez de utilizar essa abordagem tradicional, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] mapeia tabelas relacionais, colunas e restrições de chave estrangeira em modelos lógicos para entidades e relações em modelos conceituais. Isso permite maior flexibilidade para definir objetos e otimizar o modelo lógico. As ferramentas do [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] geram classes de dados extensíveis baseadas no modelo conceitual. Essas classes são classes parciais que podem ser estendidas com a adição de membros feita pelo desenvolvedor. Por padrão, as classes geradas para um modelo conceitual específico derivam de classes base que fornecem serviços para materializar entidades como objetos e para controlar e salvar alterações. Os desenvolvedores podem usar essas classes para trabalhar com as entidades e relações como objetos relacionados por associações. Os desenvolvedores também podem personalizar as classes que são geradas para um modelo conceitual. Para obter mais informações, consulte [trabalhando com objetos](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).

## <a name="access-and-change-entity-data"></a>Acessar e alterar dados de entidade

Mais do que apenas outra solução de mapeamento relacional de objeto, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] é fundamentalmente sobre como habilitar aplicativos acessar e alterar dados que são representados como entidades e relações no modelo conceitual. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usa informações nos arquivos de mapeamento do modelo e para converter consultas de objeto em relação a tipos de entidade representados no modelo conceitual em consultas específicas à fonte de dados. Os resultados da consulta são materializados em objetos que o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] gerencia. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fornece as seguintes maneiras para consultar um modelo conceitual e retornar objetos:

-   [!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]. Fornece suporte de consulta integrada à linguagem (LINQ) para consultar os tipos de entidade que são definidos em um modelo conceitual. Para obter mais informações, consulte [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).

-   [!INCLUDE[esql](../../../../../includes/esql-md.md)]. Um dialeto de independente de armazenamento do SQL que trabalha diretamente com entidades no modelo conceitual e que dá suporte a [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] conceitos. [!INCLUDE[esql](../../../../../includes/esql-md.md)] é usado com consultas de objeto e consultas que são executadas usando o provedor EntityClient. Para obter mais informações, consulte [visão geral do Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md).

O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclui o provedor de dados EntityClient. Esse provedor gerencia conexões, converte consultas de entidade em consultas específicas à fonte de dados e retorna um leitor de dados que o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usa para materializar dados de entidade em objetos. Quando a materialização do objeto não for necessária, o provedor EntityClient também pode ser usado como um padrão [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] provedor de dados, permitindo que aplicativos sejam executados [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultas e consumam o leitor de dados retornados de somente leitura. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

O diagrama a seguir ilustra a arquitetura do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] para acessar dados:

![Diagrama de arquitetura do Entity Framework](../../../../../docs/framework/data/adonet/ef/media/wd-efarchdiagram.gif "wd_EFArchDiagram")

As ferramentas do [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] podem gerar uma classe derivada de `System.Data.Objects.ObjectContext` ou `System.Data.Entity.DbContext` que representa o contêiner de entidade no modelo conceitual. Esse contexto de objeto fornece os recursos para controlar alterações e gerenciar identidades, simultaneidade e relações. Essa classe também expõe um método `SaveChanges` que grava inserções, atualizações e exclusões na fonte de dados. Como consultas, essas alterações são feitas pelos comandos gerados automaticamente pelo sistema ou por procedimentos armazenados especificados pelo desenvolvedor.

## <a name="data-providers"></a>Provedores de dados

O provedor do `EntityClient` estende o modelo de provedor do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] acessando dados em termos de entidades e relações conceituais. Executa consultas que usam [!INCLUDE[esql](../../../../../includes/esql-md.md)]. O [!INCLUDE[esql](../../../../../includes/esql-md.md)] fornece a linguagem de consulta subjacente que permite que o `EntityClient` se comunique com o banco de dados. Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).

O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclui um provedor de dados SqlClient atualizado que dá suporte a árvores de comandos canônicas. Para obter mais informações, consulte [SqlClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md).

## <a name="entity-data-model-tools"></a>Ferramentas do modelo de dados de entidade

Junto com o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] em tempo de execução, o Visual Studio inclui o mapeamento e as ferramentas de modelagem. Para obter mais informações, consulte [modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).

## <a name="learn-more"></a>Saiba mais

Para saber mais sobre o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], consulte:

[Guia de Introdução](../../../../../docs/framework/data/adonet/ef/getting-started.md) – fornece informações sobre como entrar em funcionamento rapidamente usando o [guia de início rápido](https://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675), que mostra como criar um simples [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativo.

[Terminologia do Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md) -define muitos dos termos que são introduzidos pelo modelo de dados de entidade e o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] e que são usados no [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentação.

[Recursos do Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md) - fornece links para tópicos conceituais e links para tópicos e recursos para compilação externos [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativos.

## <a name="see-also"></a>Consulte também

- [Entity Framework do ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)
