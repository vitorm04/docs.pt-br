---
title: Dados binários e de valor grande do SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4b7a3f16726d6363cd702fb912bb7be281a25000
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192960"
---
# <a name="sql-server-binary-and-large-value-data"></a>Dados binários e de valor grande do SQL Server
O SQL Server fornece as `max` especificador, que expande a capacidade de armazenamento do `varchar`, `nvarchar`, e `varbinary` tipos de dados. `varchar(max)`, `nvarchar(max)`, e `varbinary(max)` são coletivamente chamados *tipos de dados de valor grande*. Você pode usar os tipos de dados de valor grande para armazenar até 2 ^ 31-1 bytes de dados.  
  
 SQL Server 2008 apresenta o atributo FILESTREAM, que é não um tipo de dados, mas em vez disso, um atributo que pode ser definido em uma coluna, permitindo que os dados de valor grande ser armazenado no sistema de arquivos em vez de no banco de dados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modificando dados de valores grandes (max) no ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Descreve como trabalhar com os tipos de dados de valor grande.  
  
 [Dados FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de dados do SQL Server e ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Operações de dados do SQL Server no ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [Recuperando e modificando dados no ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
