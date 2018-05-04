---
title: Mapeamentos de tipos de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 1064f3be7f2548337b5dd6653c76b70a04fad980
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-mappings-in-adonet"></a>Mapeamentos de tipos de dados no ADO.NET
O .NET Framework é baseado no Common Type System, que define como os tipos são declarados, usados e gerenciados em tempo de execução. Consiste nos tipos de valor e nos tipos de referência, que derivam do tipo de base <xref:System.Object>. Ao trabalhar com uma fonte de dados, o tipo de dados será inferido no provedor de dados se não for especificado explicitamente. Por exemplo, um objeto <xref:System.Data.DataSet> é independente de qualquer fonte de dados específica. Os dados de um `DataSet` são recuperados de uma fonte de dados, e as alterações são persistidas de volta para a fonte de dados usando o `DataAdapter`. Isso significa que quando o `DataAdapter` preenche um <xref:System.Data.DataTable> em um `DataSet` com valores de uma fonte de dados, os tipos de dados resultantes das colunas no `DataTable` são tipos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], em vez de tipos específicos ao provedor de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], que é usado para conectar a fonte de dados.  
  
 Da mesma forma, quando um `DataReader` retorna um valor de uma fonte de dados, o valor resultante é armazenado em uma variável local que tenha um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo. Para ambos os `Fill` operações do `DataAdapter` e o `Get` métodos do `DataReader`, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo é inferido do valor retornado do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provedor de dados.  
  
 Em vez de depender do tipo de dados inferido, você pode usar os métodos acessadores tipados do `DataReader` quando souber o tipo específico do valor que está sendo retornado. Os métodos acessadores tipados oferecem melhor desempenho devolvendo um valor como um tipo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] específico, que elimina a necessidade de conversão de tipos adicionais.  
  
> [!NOTE]
>  Valores nulos para tipos de dados do provedor de dados [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] são representados por `DBNull.Value`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeamentos de tipo de dados do SQL Server](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.SqlClient>.  
  
 [Mapeamentos de tipo de dados do OLE DB](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.OleDb>.  
  
 [Mapeamentos de tipo de dados ODBC](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.Odbc>.  
  
 [Mapeamentos de tipo de dados Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.OracleClient>.  
  
 [Números de ponto flutuante](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 Descreve os problemas que os desenvolvedores geralmente encontram ao trabalhar com números de ponto flutuante.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Data Types and ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)  
 [Configurando parâmetros e tipos de dados de parâmetro](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Common Type System](../../../../docs/standard/base-types/common-type-system.md)  
 [Convertendo tipos](http://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
