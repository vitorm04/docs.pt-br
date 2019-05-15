---
title: Mapeamentos de tipos de dados no ADO.NET
ms.date: 03/30/2017
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
ms.openlocfilehash: 4e85db4732da664848cee2ef48f9a880a86fef18
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583766"
---
# <a name="data-type-mappings-in-adonet"></a>Mapeamentos de tipos de dados no ADO.NET
O .NET Framework é baseado no Common Type System, que define como os tipos são declarados, usados e gerenciados em tempo de execução. Consiste nos tipos de valor e nos tipos de referência, que derivam do tipo de base <xref:System.Object>. Ao trabalhar com uma fonte de dados, o tipo de dados será inferido no provedor de dados se não for especificado explicitamente. Por exemplo, um objeto <xref:System.Data.DataSet> é independente de qualquer fonte de dados específica. Os dados de um `DataSet` são recuperados de uma fonte de dados, e as alterações são persistidas de volta para a fonte de dados usando o `DataAdapter`. Isso significa que, quando um `DataAdapter` preenche uma <xref:System.Data.DataTable> em um `DataSet` com valores de uma fonte de dados, os tipos de dados resultantes das colunas no `DataTable` são os tipos do .NET Framework, em vez de tipos específicos ao provedor de dados .NET Framework que é usado para se conectar à fonte de dados.  
  
 Da mesma forma, quando um `DataReader` retorna um valor de uma fonte de dados, o valor resultante é armazenado em uma variável local que tem um tipo .NET Framework. Para ambos os `Fill` operações do `DataAdapter` e o `Get` métodos do `DataReader`, o tipo do .NET Framework é inferido do valor retornado do provedor de dados .NET Framework.  
  
 Em vez de depender do tipo de dados inferido, você pode usar os métodos acessadores tipados do `DataReader` quando souber o tipo específico do valor que está sendo retornado. Métodos acessadores tipados oferecem melhor desempenho, retornando um valor como um tipo específico do .NET Framework, que elimina a necessidade de conversão de tipo adicionais.  
  
> [!NOTE]
>  Valores nulos para tipos de dados do provedor de dados do .NET Framework são representados por `DBNull.Value`.  
  
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

- [SQL Server Data Types and ADO.NET](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)
- [Configurando parâmetros e tipos de dados de parâmetro](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [Recuperando informações de esquema de banco de dados](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [Common Type System](../../../../docs/standard/base-types/common-type-system.md)
- [Convertendo tipos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t8s7t9bf(v=vs.90))
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
