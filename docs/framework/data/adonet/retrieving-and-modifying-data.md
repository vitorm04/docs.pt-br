---
title: Recuperando e modificando dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: a5ac8fbd2a53d2670471c1ef5e59508f582ed944
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881429"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Recuperando e modificando dados no ADO.NET
A função principal de qualquer aplicativo de banco de dados é conectar-se a uma fonte de dados e recuperar os dados que ele contém. Os provedores de dados .NET Framework do ADO.NET funcionam como uma ponte entre um aplicativo e uma fonte de dados, permitindo que você execute comandos e recuperar dados usando um **DataReader** ou um **DataAdapter** . A função principal de qualquer aplicativo de banco de dados é a capacidade de atualizar os dados que estão armazenados no banco de dados. No ADO.NET, atualização de dados envolve o uso de **DataAdapter** e <xref:System.Data.DataSet>, e **comando** objetos; e ele também podem envolver o uso de transações.  
  
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
 Fornece um exemplo de como mapear valores gerados para um **identity** coluna em uma tabela do SQL Server ou para um **Autonumber** campo em uma tabela do Microsoft Access, para uma coluna de uma linha inserida em uma tabela. Discute como mesclar valores de identidade em `DataTable`.  
  
 [Recuperando dados binários](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 Descreve como recuperar dados binários ou grandes estruturas de dados usando `CommandBehavior`.`SequentialAccess` Para modificar o comportamento padrão de um `DataReader`.  
  
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
 Descreve o suporte do ADO.NET para programação assíncrona.  
  
 [Suporte de Streaming do SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Discute como escrever aplicativos que transmitir dados do SQL Server sem a necessidade de ele totalmente carregado na memória.  
  
## <a name="see-also"></a>Consulte também

- [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md) (Mapeamentos de tipo de dados no ADO.NET)
- [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [Securing ADO.NET Applications](../../../../docs/framework/data/adonet/securing-ado-net-applications.md) (Protegendo aplicativos ADO.NET)
- [SQL Server and ADO.NET](../../../../docs/framework/data/adonet/sql/index.md) (SQL Server e ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
