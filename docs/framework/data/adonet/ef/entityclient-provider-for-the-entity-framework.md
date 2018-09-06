---
title: Provedor EntityClient para Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 1bafdc250c7edc009352d668e8ee7962a86fe8bf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43806167"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Provedor EntityClient para Entity Framework
O provedor EntityClient é um provedor de dados usado por aplicativos Entity Framework para acessar dados descritos em um modelo conceitual. Para obter informações sobre modelos conceituais, consulte [modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). O EntityClient usa outros provedores de dados .NET Framework para acessar a fonte de dados. Por exemplo, o EntityClient usa o Provedor de Dados .NET Framework para SQL Server (SqlClient) ao acessar um banco de dados do SQL Server. Para obter informações sobre o provedor SqlClient, consulte [SqlClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). O provedor EntityClient é implementado no namespace <xref:System.Data.EntityClient>.  
  
## <a name="managing-connections"></a>Gerenciando conexões  
 O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] se baseia no armazenamento específicos [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] provedores de dados, fornecendo um <xref:System.Data.EntityClient.EntityConnection> para um provedor de dados subjacente e o banco de dados relacional. Para construir um <xref:System.Data.EntityClient.EntityConnection> do objeto, você deve fazer referência a um conjunto de metadados que contém os modelos necessários e mapeamento e também uma sequência nome e a conexão do provedor de dados específico do armazenamento. Após o <xref:System.Data.EntityClient.EntityConnection> está em vigor, as entidades podem ser acessadas por meio de classes geradas a partir do modelo conceitual.  
  
 Você pode especificar uma cadeia de conexão no arquivo app.config.  
  
 O <xref:System.Data.EntityClient> também inclui a classe <xref:System.Data.EntityClient.EntityConnectionStringBuilder>. Essa classe permite aos desenvolvedores criar, programaticamente, cadeias de conexão com sintaxe correta, bem como analisar e reconstruir cadeias de conexão existentes, usando as propriedades e os métodos da classe. Para obter mais informações, consulte [como: criar uma cadeia de caracteres de Conexão EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Criando consultas  
 O [!INCLUDE[esql](../../../../../includes/esql-md.md)] idioma é um dialeto independente de armazenamento do SQL que trabalha diretamente com esquemas conceituais de entidade e dá suporte a conceitos de modelo de dados de entidade como herança e relações. O <xref:System.Data.EntityClient.EntityCommand> classe é usada para executar um [!INCLUDE[esql](../../../../../includes/esql-md.md)] comando em um modelo de entidade. Quando você constrói objetos <xref:System.Data.EntityClient.EntityCommand>, é possível especificar um nome de procedimento armazenado ou um texto de consulta. O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] funciona com provedores de dados específicos ao armazenamento para converter a linguagem [!INCLUDE[esql](../../../../../includes/esql-md.md)] genérica em consultas específicas ao armazenamento. Para obter mais informações sobre como escrever [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultas, consulte [linguagem Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 O exemplo a seguir cria uma <xref:System.Data.EntityClient.EntityCommand> objeto e atribui uma [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultar texto para seu <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> propriedade. Isso [!INCLUDE[esql](../../../../../includes/esql-md.md)] consulta solicita os produtos ordenados pelo preço de lista no modelo conceitual. O código a seguir não tem nenhum conhecimento do modelo de armazenamento.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Executando consultas  
 Quando uma consulta é executada, ela é analisada e convertida em uma árvore de comandos canônica. Todo processamento subsequente é executado na árvore de comandos. A árvore de comandos é o meio de comunicação entre <xref:System.Data.EntityClient> e o provedor de dados [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] subjacente, como <xref:System.Data.SqlClient>.  
  
 O <xref:System.Data.EntityClient.EntityDataReader> expõe os resultados da execução de um <xref:System.Data.EntityClient.EntityCommand> em relação a um modelo conceitual. Para executar o comando que retorna <xref:System.Data.EntityClient.EntityDataReader>, chame <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. O <xref:System.Data.EntityClient.EntityDataReader> implementa <xref:System.Data.IExtendedDataRecord> para descrever resultados estruturados avançados.  
  
## <a name="managing-transactions"></a>Gerenciando transações  
 No Entity Framework, existem dois modos de usar transações: automático e explícito. As transações automáticas usam o namespace <xref:System.Transactions>, e as transações explícitas usam a classe <xref:System.Data.EntityClient.EntityTransaction>.  
  
 Para atualizar os dados que são expostos por meio de um modelo conceitual; ver [como: gerenciar transações no Entity Framework](https://msdn.microsoft.com/library/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como compilar uma cadeia de conexão EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Como executar uma consulta que retorna resultados PrimitiveType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Como executar uma consulta que retorna resultados StructuralType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Como executar uma consulta que retorna resultados RefType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Como executar uma consulta que retorna tipos complexos](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Como executar uma consulta que retorna coleções aninhadas](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Como executar uma consulta Entity SQL parametrizada usando EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Como executar um procedimento armazenado parametrizado usando EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Como executar uma consulta polimorfa](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Como navegar em relações com o operador Navigate](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando conexões e transações](https://msdn.microsoft.com/library/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [Entity Framework do ADO.NET](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Referência de Linguagem](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
