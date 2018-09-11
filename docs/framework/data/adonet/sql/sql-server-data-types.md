---
title: Tipos de dados do SQL Server e ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272482"
---
# <a name="sql-server-data-types-and-adonet"></a>Tipos de dados do SQL Server e ADO.NET
O SQL Server e o .NET Framework são baseados em diferentes tipos de sistema, o que pode resultar em potencial perda de dados. Para preservar a integridade dos dados, o provedor de dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>) fornece métodos tipados acessadores para trabalhar com dados do SQL Server. É possível usar enumerações nas classes <xref:System.Data.SqlDbType> para especificar tipos de dados <xref:System.Data.SqlClient.SqlParameter>.  
  
 Para obter mais informações e uma tabela que descreve os dados de tipo mapeamentos entre tipos de dados do .NET Framework e do SQL Server, consulte [mapeamentos de tipo de dados do SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 O SQL Server 2008 apresenta novos tipos de dados cujo objetivo é atender às necessidades de negócios de trabalhar com dados de data e hora, estruturados, semiestruturados e não estruturados. Esses tipos de dados estão documentados em Manuais Online do SQL Server 2008.  
  
 Os tipos de dados do SQL Server disponíveis para uso em seu aplicativo dependem da versão do SQL Server em uso. Para obter mais informações, consulte a versão relevante de Manuais Online do SQL Server na tabela a seguir.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1.  [Tipos de dados (mecanismo de banco de dados)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>Nesta seção  
 [SqlTypes e DataSet](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Descreve o suporte a tipos para `SqlTypes` em `DataSet`.  
  
 [Manipulando valores nulos](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Demonstra como trabalhar com valores nulos e a lógica com três valores.  
  
 [Comparando valores de GUID e uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Demonstra como trabalhar com GUID e com valores uniqueidentifier no SQL Server e no .NET Framework.  
  
 [Dados de data e hora](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Descreve como usar os novos tipos de dados de data e hora introduzidos no SQL Server 2008.  
  
 [UDTs grandes](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Demonstra como recuperar dados de UDTs de valor grande introduzidos no SQL Server 2008.  
  
 [Dados XML no SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 Descreve como trabalhar com dados XML recuperados do SQL Server.  
  
## <a name="reference"></a>Referência  
 <xref:System.Data.DataSet>  
 Descreve a classe `DataSet` e todos os seus membros.  
  
 <xref:System.Data.SqlTypes>  
 Descreve o namespace `SqlTypes` e todos os seus membros.  
  
 <xref:System.Data.SqlDbType>  
 Descreve a enumeração `SqlDbType` e todos os seus membros.  
  
 <xref:System.Data.DbType>  
 Descreve a enumeração `DbType` e todos os seus membros.  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamentos de tipo de dados do SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Configurando parâmetros e tipos de dados de parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Parâmetros com valor de tabela](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [SQL Server Binary and Large-Value Data](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
