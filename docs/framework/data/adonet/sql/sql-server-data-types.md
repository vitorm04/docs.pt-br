---
title: Tipos de dados do SQL Server e ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780852"
---
# <a name="sql-server-data-types-and-adonet"></a>Tipos de dados do SQL Server e ADO.NET
O SQL Server e o .NET Framework são baseados em diferentes tipos de sistema, o que pode resultar em potencial perda de dados. Para preservar a integridade dos dados, o provedor de dados .NET Framework para SQL Server (<xref:System.Data.SqlClient>) fornece métodos tipados acessadores para trabalhar com dados do SQL Server. É possível usar enumerações nas classes <xref:System.Data.SqlDbType> para especificar tipos de dados <xref:System.Data.SqlClient.SqlParameter>.  
  
 Para obter mais informações e uma tabela que descreve os mapeamentos de tipo de dados entre SQL Server e .NET Framework tipos de dados, consulte [SQL Server mapeamentos de tipo de dados](../sql-server-data-type-mappings.md).  
  
 O SQL Server 2008 apresenta novos tipos de dados cujo objetivo é atender às necessidades de negócios de trabalhar com dados de data e hora, estruturados, semiestruturados e não estruturados. Esses tipos de dados estão documentados em Manuais Online do SQL Server 2008.  
  
 Os tipos de dados do SQL Server disponíveis para uso em seu aplicativo dependem da versão do SQL Server em uso. Para obter mais informações, consulte a versão relevante de Manuais Online do SQL Server na tabela a seguir.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1. [Tipos de dados (Mecanismo de Banco de Dados)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>Nesta seção  
 [SqlTypes e DataSet](sqltypes-and-the-dataset.md)  
 Descreve o suporte a tipos para `SqlTypes` em `DataSet`.  
  
 [Manipulando valores nulos](handling-null-values.md)  
 Demonstra como trabalhar com valores nulos e a lógica com três valores.  
  
 [Comparando valores de GUID e uniqueidentifier](comparing-guid-and-uniqueidentifier-values.md)  
 Demonstra como trabalhar com GUID e com valores uniqueidentifier no SQL Server e no .NET Framework.  
  
 [Dados de data e hora](date-and-time-data.md)  
 Descreve como usar os novos tipos de dados de data e hora introduzidos no SQL Server 2008.  
  
 [UDTs grandes](large-udts.md)  
 Demonstra como recuperar dados de UDTs de valor grande introduzidos no SQL Server 2008.  
  
 [Dados XML no SQL Server](xml-data-in-sql-server.md)  
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

- [Mapeamentos de tipo de dados do SQL Server](../sql-server-data-type-mappings.md)
- [Configurando parâmetros e tipos de dados de parâmetro](../configuring-parameters-and-parameter-data-types.md)
- [Parâmetros com valor de tabela](table-valued-parameters.md)
- [SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md) (Dados binários e de valor grande do SQL Server)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
