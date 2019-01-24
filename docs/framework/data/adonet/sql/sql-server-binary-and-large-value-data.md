---
title: SQL Server Data binário e de valor grande
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: f6bd62d2e9d2f87947e01b7964c5d151690b62bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643021"
---
# <a name="sql-server-binary-and-large-value-data"></a>SQL Server Data binário e de valor grande
O SQL Server fornece as `max` especificador, que expande a capacidade de armazenamento do `varchar`, `nvarchar`, e `varbinary` tipos de dados. `varchar(max)`, `nvarchar(max)`, e `varbinary(max)` são coletivamente chamados *tipos de dados de valor grande*. Você pode usar os tipos de dados de valor grande para armazenar até 2 ^ 31-1 bytes de dados.  
  
 SQL Server 2008 apresenta o atributo FILESTREAM, que é não um tipo de dados, mas em vez disso, um atributo que pode ser definido em uma coluna, permitindo que os dados de valor grande ser armazenado no sistema de arquivos em vez de no banco de dados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modificando dados de valor grande (max) no ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Descreve como trabalhar com os tipos de dados de valor grande.  
  
 [Dados FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.  
  
## <a name="see-also"></a>Consulte também
- [SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)
- [SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)
- [Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)
- [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
