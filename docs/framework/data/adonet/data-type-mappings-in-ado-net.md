---
title: Mapeamentos de tipo de dados
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 52e64714a17448cd94723bdc216d8ea069fc5eef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177742"
---
# <a name="data-type-mappings-in-adonet"></a>Mapeamentos de tipos de dados no ADO.NET

O .NET Framework é baseado no Common Type System, que define como os tipos são declarados, usados e gerenciados em runtime. Consiste nos tipos de valor e nos tipos de referência, que derivam do tipo de base <xref:System.Object>. Ao trabalhar com uma fonte de dados, o tipo de dados será inferido no provedor de dados se não for especificado explicitamente. Por exemplo, um objeto <xref:System.Data.DataSet> é independente de qualquer fonte de dados específica. Os dados de um `DataSet` são recuperados de uma fonte de dados, e as alterações são persistidas de volta para a fonte de dados usando o `DataAdapter`. Isso significa que, quando um `DataAdapter` preenche um <xref:System.Data.DataTable> `DataSet` com valores de uma fonte de dados, os tipos de dados resultantes das colunas no `DataTable` são .NET Framework tipos, em vez de tipos específicos para o provedor de dados de .NET Framework que é usado para se conectar à fonte de dados.  
  
 Da mesma forma, quando um `DataReader` retorna um valor de uma fonte de dados, o valor resultante é armazenado em uma variável local que tem um tipo de .NET Framework. Para ambas as `Fill` operações do `DataAdapter` e os `Get` métodos do `DataReader` , o tipo de .NET Framework é inferido a partir do valor retornado do provedor de dados de .NET Framework.  
  
 Em vez de depender do tipo de dados inferido, você pode usar os métodos acessadores tipados do `DataReader` quando souber o tipo específico do valor que está sendo retornado. Os métodos de acessadores tipados oferecem melhor desempenho retornando um valor como um tipo específico de .NET Framework, o que elimina a necessidade de conversão de tipo adicional.  
  
> [!NOTE]
> Valores nulos para .NET Framework tipos de dados do provedor de dados são representados por `DBNull.Value` .  
  
## <a name="in-this-section"></a>Nesta seção  

 [Mapeamentos de tipos de dados do SQL Server](sql-server-data-type-mappings.md)  
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

- [Tipos de dados do SQL Server e ADO.NET](./sql/sql-server-data-types.md)
- [Configurar parâmetros e tipos de dados de parâmetro](configuring-parameters-and-parameter-data-types.md)
- [Recuperando informações de esquema de banco de dados](retrieving-database-schema-information.md)
- [Sistema de tipos comum](../../../standard/base-types/common-type-system.md)
- [Convertendo tipos](/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [Visão geral do ADO.NET](ado-net-overview.md)
