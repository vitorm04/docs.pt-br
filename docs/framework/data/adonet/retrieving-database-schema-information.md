---
title: Recuperando informações de esquema de banco de dados
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782728"
---
# <a name="retrieving-database-schema-information"></a>Recuperando informações de esquema de banco de dados
A obtenção de informações de esquema de um banco de dados é realizada com o processo de descoberta de esquema. A descoberta de esquema permite que os aplicativos solicitem que os provedores gerenciados localizem e retornem informações sobre o esquema de banco de dados, também conhecidos como *metadados*de um determinado banco de dados. Os diferentes elementos de esquema de banco de dados, como tabelas, colunas e procedimentos armazenados, são expostos por meio de coleções de esquema. Cada coleção de esquema contém uma variedade de informações de esquema específicas ao provedor em uso.  
  
 Cada um dos provedores gerenciados .NET Framework implementa o método **GetSchema** na classe **Connection** , e as informações de esquema que são retornadas do método **GetSchema** vêm na forma de um <xref:System.Data.DataTable>. O método **GetSchema** é um método sobrecarregado que fornece parâmetros opcionais para especificar a coleção de esquema a ser retornada e restringir a quantidade de informações retornadas.  
  
 O .NET Framework provedores de dados para OLE DB, ODBC, Oracle e SqlClient fornecem um método **GetSchemaTable** que retorna uma DataTable que descreve os metadados da coluna de **DataReader**.  
  
 O Provedor de Dados .NET Framework para OLE DB também expõe informações de esquema usando o método <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> do objeto <xref:System.Data.OleDb.OleDbConnection>. Como argumentos, **GetOleDbSchemaTable** Obtém um <xref:System.Data.OleDb.OleDbSchemaGuid> que identifica as informações de esquema a serem retornadas e uma matriz de restrições nessas colunas retornadas. **GetOleDbSchemaTable** retorna um <xref:System.Data.DataTable> populado com as informações de esquema solicitadas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [GetSchema e coleções de esquema](getschema-and-schema-collections.md)  
 Descreve o método **GetSchema** e como ele pode ser usado para recuperar e restringir informações de esquema de um banco de dados.  
  
 Restrições de esquema  
 Descreve as restrições de esquema que podem ser usadas com **GetSchema**.  
  
 [Coleções de esquema comuns](common-schema-collections.md)  
 Descreve todas as coleções de esquema comuns com suporte em todos os provedores gerenciados .NET Framework.  
  
 [Coleções de esquema do SQL Server](sql-server-schema-collections.md)  
 Descreve a coleção de esquema com suporte pelo provedor .NET Framework para SQL Server.  
  
 [Coleções de esquema do Oracle](oracle-schema-collections.md)  
 Descreve a coleção de esquema com suporte pelo provedor .NET Framework para Oracle.  
  
 [Coleções de esquema ODBC](odbc-schema-collections.md)  
 Descreve as coleções de esquema para drivers ODBC.  
  
 [Coleções de esquema de OLE DB](ole-db-schema-collections.md)  
 Descreve as coleções de esquema para provedores OLE DB.  
  
## <a name="reference"></a>Referência  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Descreve o método **GetSchema** da <xref:System.Data.Common.DbConnection> classe.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Descreve o método **GetSchema** da <xref:System.Data.Odbc.OdbcConnection> classe.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Descreve o método **GetSchema** da <xref:System.Data.OleDb.OleDbConnection> classe.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Descreve o método **GetSchema** da <xref:System.Data.OracleClient.OracleConnection> classe.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Descreve o método **GetSchema** da <xref:System.Data.SqlClient.SqlConnection> classe.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Descreve o método **GetSchemaTable** da <xref:System.Data.Common.DbDataReader> classe.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Descreve o método **GetSchemaTable** da <xref:System.Data.Odbc.OdbcDataReader> classe.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Descreve o método **GetSchemaTable** da <xref:System.Data.OleDb.OleDbDataReader> classe.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Descreve o método **GetSchemaTable** da <xref:System.Data.OracleClient.OracleDataReader> classe.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Descreve o método **GetSchemaTable** da <xref:System.Data.SqlClient.SqlDataReader> classe.  
  
## <a name="see-also"></a>Consulte também

- [Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
