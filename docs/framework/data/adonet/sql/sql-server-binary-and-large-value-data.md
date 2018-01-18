---
title: "Dados de valor grande e binários do servidor SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5ce85e61ac001ec07c14cebbc8d07e6c031498fc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-binary-and-large-value-data"></a>Dados de valor grande e binários do servidor SQL
O SQL Server fornece a `max` especificador, que se expande a capacidade de armazenamento do `varchar`, `nvarchar`, e `varbinary` tipos de dados. `varchar(max)`, `nvarchar(max)`, e `varbinary(max)` são coletivamente chamados de *tipos de dados de valor grande*. Você pode usar os tipos de dados de valor grande para armazenar até 2 ^ 31-1 bytes de dados.  
  
 SQL Server 2008 apresenta o atributo FILESTREAM, que não é um tipo de dados, mas em vez disso, um atributo que pode ser definido em uma coluna, permitindo que os dados de valor grande ser armazenado no sistema de arquivos em vez de no banco de dados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Modificando dados de valor grande (max) no ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Descreve como trabalhar com os tipos de dados de valor grande.  
  
 [Dados FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Descreve como trabalhar com dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.  
  
## <a name="see-also"></a>Consulte também  
 [SQL Server Data Types and ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md) (Tipos de dados do SQL Server e o ADO.NET)  
 [SQL Server Data Operations in ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md) (Operações de dados do SQL Server no ADO.NET)  
 [Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
