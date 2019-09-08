---
title: Comandos e parâmetros
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 1d0c3adb56e5ff44b5c5e065ac040f25584a1946
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784961"
---
# <a name="commands-and-parameters"></a>Comandos e parâmetros
Depois de estabelecer uma conexão a uma fonte de dados, você pode executar comandos e retornar resultados da fonte de dados usando um objeto <xref:System.Data.Common.DbCommand>. Você pode criar um comando usando um dos construtores de comando do provedor de dados .NET Framework com o qual está trabalhando. Os construtores podem usar argumentos opcionais, como uma instrução SQL para executar na fonte de dados, em um objeto <xref:System.Data.Common.DbConnection> ou em um objeto <xref:System.Data.Common.DbTransaction>. Você também pode configurar esses objetos como propriedades do comando. Pode também criar um comando para uma conexão específica usando o método <xref:System.Data.Common.DbConnection.CreateCommand%2A> de um objeto `DbConnection`. A instrução SQL que está sendo executada pelo comando pode ser configurada usando a propriedade <xref:System.Data.Common.DbCommand.CommandText%2A>.  
  
 Cada provedor de dados .NET Framework incluído com o .NET Framework tem um objeto `Command`. O Provedor de Dados .NET Framework para OLE DB inclui um objeto <xref:System.Data.OleDb.OleDbCommand>, o Provedor de Dados .NET Framework para SQL Server inclui um objeto <xref:System.Data.SqlClient.SqlCommand>, o Provedor de Dados .NET Framework para ODBC inclui um objeto <xref:System.Data.Odbc.OdbcCommand> e o Provedor de Dados .NET Framework para Oracle inclui um objeto <xref:System.Data.OracleClient.OracleCommand>.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Executar um comando](executing-a-command.md)  
 Descreve o objeto `Command` ADO.NET e como usá-lo para executar consultas e comandos em uma fonte de dados.  
  
 [Configurando parâmetros e tipos de dados de parâmetro](configuring-parameters-and-parameter-data-types.md)  
 Descreve como trabalhar com os parâmetros de `Command`, incluindo a direção, os tipos de dados e a sintaxe de parâmetro.  
  
 [Gerando comandos com CommandBuilders](generating-commands-with-commandbuilders.md)  
 Descreve como usar construtores de comando para gerar automaticamente comandos INSERT, UPDATE, e DELETE para um `DataAdapter` que possui um comando SELECT de uma única tabela.  
  
 [Obter um único valor de um banco de dados](obtaining-a-single-value-from-a-database.md)  
 Descreve como usar o método `ExecuteScalar` de um objeto `Command` para retornar um único valor de uma consulta de banco de dados.  
  
 [Usando os comandos para modificar dados](using-commands-to-modify-data.md)  
 Descreve como usar um provedor de dados para executar procedimentos armazenados ou instruções DDL (linguagem de definição de dados).  
  
## <a name="see-also"></a>Consulte também

- [DataAdapters e DataReaders](dataadapters-and-datareaders.md)
- [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)
- [Conectando a uma fonte de dados](connecting-to-a-data-source.md)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
