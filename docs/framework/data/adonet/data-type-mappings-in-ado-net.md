---
title: Mapeamentos de tipo de dados
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 610cdc1a679b0c51125075076120e12db97da421
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980191"
---
# <a name="data-type-mappings-in-adonet"></a>Mapeamentos de tipos de dados no ADO.NET
O .NET Framework é baseado no Common Type System, que define como os tipos são declarados, usados e gerenciados em runtime. Consiste nos tipos de valor e nos tipos de referência, que derivam do tipo de base <xref:System.Object>. Ao trabalhar com uma fonte de dados, o tipo de dados será inferido no provedor de dados se não for especificado explicitamente. Por exemplo, um objeto <xref:System.Data.DataSet> é independente de qualquer fonte de dados específica. Os dados de um `DataSet` são recuperados de uma fonte de dados, e as alterações são persistidas de volta para a fonte de dados usando o `DataAdapter`. Isso significa que, quando um `DataAdapter` preenche uma <xref:System.Data.DataTable> em um `DataSet` com valores de uma fonte de dados, os tipos de dados resultantes das colunas no `DataTable` são tipos de .NET Framework, em vez de tipos específicos para o provedor de dados .NET Framework que é usado para se conectar à fonte de dados.  
  
 Da mesma forma, quando um `DataReader` retorna um valor de uma fonte de dados, o valor resultante é armazenado em uma variável local que tem um tipo de .NET Framework. Para as operações de `Fill` do `DataAdapter` e os métodos de `Get` do `DataReader`, o tipo de .NET Framework é inferido do valor retornado do provedor de dados .NET Framework.  
  
 Em vez de depender do tipo de dados inferido, você pode usar os métodos acessadores tipados do `DataReader` quando souber o tipo específico do valor que está sendo retornado. Os métodos de acessadores tipados oferecem melhor desempenho retornando um valor como um tipo específico de .NET Framework, o que elimina a necessidade de conversão de tipo adicional.  
  
> [!NOTE]
> Os valores nulos para .NET Framework tipos de dados do provedor de dados são representados por `DBNull.Value`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeamentos de tipo de dados do SQL Server](sql-server-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.SqlClient>.  
  
 [Mapeamentos de tipo de dados do OLE DB](ole-db-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.OleDb>.  
  
 [Mapeamentos de tipo de dados ODBC](odbc-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.Odbc>.  
  
 [Mapeamentos de tipo de dados Oracle](oracle-data-type-mappings.md)  
 As listas inferiram mapeamentos de tipos de dados e de métodos de acessador de dados para <xref:System.Data.OracleClient>.  
  
 [Números de ponto flutuante](floating-point-numbers.md)  
 Descreve os problemas que os desenvolvedores geralmente encontram ao trabalhar com números de ponto flutuante.  
  
## <a name="see-also"></a>Veja também

- [SQL Server Data Types and ADO.NET](./sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)
- [Configurando parâmetros e tipos de dados de parâmetro](configuring-parameters-and-parameter-data-types.md)
- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [Common Type System](../../../standard/base-types/common-type-system.md)
- [Convertendo tipos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)
