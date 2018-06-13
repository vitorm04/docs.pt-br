---
title: Recuperando e modificando dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 0c970c01352aecf6a25bac1b89b9f79c96f80d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361537"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Recuperando e modificando dados no ADO.NET
A função principal de qualquer aplicativo de banco de dados é conectar-se a uma fonte de dados e recuperar os dados que ele contém. Os provedores de dados do .NET Framework do ADO.NET servem como uma ponte entre um aplicativo e uma fonte de dados, permitindo que você execute comandos, bem como para recuperar dados usando um **DataReader** ou um **DataAdapter** . A função principal de qualquer aplicativo de banco de dados é a capacidade de atualizar os dados que estão armazenados no banco de dados. No ADO.NET, atualização de dados envolve o uso de **DataAdapter** e <xref:System.Data.DataSet>, e **comando** objetos; e ele também podem envolver o uso de transações.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Conectando a uma fonte de dados](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Descreve como estabelecer uma conexão com uma fonte de dados e como trabalhar com eventos de conexão.  
  
 [Cadeia de Conexão](../../../../docs/framework/data/adonet/connection-strings.md)  
 Contém os tópicos que descrevem os vários aspectos do uso de cadeias de conexão, incluindo palavras-chave de cadeias de conexão, informações de segurança e seu respectivo armazenamento e recuperação.  
  
 [Pooling de Conexão](../../../../docs/framework/data/adonet/connection-pooling.md)  
 Descreve o pool de conexões para provedores de dados .NET Framework.  
  
 [Comandos e parâmetros](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Contém os tópicos que descrevem como criar comandos e construtores de comandos, configurar parâmetros e executar comandos para recuperar e modificar dados.  
  
 [DataAdapters e DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Contém os tópicos que descrevem DataReaders, DataAdapters, parâmetros, manipulação de eventos DataAdapter e execução de operações em lote.  
  
 [Transações e simultaneidade](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Contém os tópicos que descrevem como executar transações locais, transações distribuídas e trabalho com concorrência otimista.  
  
 [Recuperando identidade ou valores de Autonumber](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Fornece um exemplo de mapeamento de valores gerados para uma **identidade** coluna em uma tabela do SQL Server ou para um **Autonumber** campo em uma tabela do Microsoft Access, para uma coluna de uma linha inserida em uma tabela. Discute como mesclar valores de identidade em `DataTable`.  
  
 [Recuperando dados binários](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 Descreve como recuperar dados binários ou estruturas de dados grandes usando `CommandBehavior`.`SequentialAccess` Para modificar o comportamento padrão de um `DataReader`.  
  
 [Modificando dados com procedimentos armazenados](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Descreve como usar parâmetros de entrada e de saída de procedimentos armazenados para inserir uma linha em um banco de dados, retornando um novo valor de identidade.  
  
 [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Descreve como obter bancos de dados ou catálogos disponíveis, tabelas e modos de exibição em um banco de dados, restrições existentes para tabelas e outras informações de esquema de uma fonte de dados.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Descreve o modelo de fábrica do provedor e demonstra como usar as classes base no namespace `System.Data.Common`.  
  
 [Rastreamento de dados no ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md)  
 Descreve como o ADO.NET fornece a funcionalidade interna de rastreamento de dados.  
  
 [Contadores de desempenho](../../../../docs/framework/data/adonet/performance-counters.md)  
 Descreve os contadores de desempenho disponíveis para `SqlClient` e `OracleClient`.  
  
 [Programação Assíncrona](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Descreve o suporte do [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] à programação assíncrona.  
  
 [Suporte de Streaming do SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Discute como escrever aplicativos esses fluxo de dados do SQL Server sem ter que ele totalmente carregado na memória.  
  
## <a name="see-also"></a>Consulte também  
 [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)  
 [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)  
 [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)  
 [SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
