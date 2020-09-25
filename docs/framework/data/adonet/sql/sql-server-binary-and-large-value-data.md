---
title: Dados binários e de valor grande do SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: a9296e83b0f4e4352423470433670bb2cbe5a248
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183033"
---
# <a name="sql-server-binary-and-large-value-data"></a>Dados binários e de valor grande do SQL Server

O SQL Server fornece o especificador `max`, que expande a capacidade de armazenamento dos tipos de dados `varchar`, `nvarchar` e `varbinary`. `varchar(max)`, `nvarchar(max)` e `varbinary(max)` são coletivamente chamados de *tipos de dados do valor grande*. Você pode usar os tipos de dados de valor grande para armazenar até 2^31-1 bytes de dados.  
  
 O SQL Server 2008 introduz o atributo FILESTREAM, que não é um tipo de dados, mas um atributo que pode ser definido em uma coluna, permitindo que dados de valor grande sejam armazenados no sistema de arquivos em vez de no banco de dados.  
  
## <a name="in-this-section"></a>Nesta seção  

 [Modificando dados de valor grande (max) em ADO.NET](modifying-large-value-max-data.md)  
 Descreve como trabalhar com tipos de dados de valores grandes.  
  
 [Dados FILESTREAM](filestream-data.md)  
 Descreve como trabalhar usando dados de valor grande armazenados no SQL Server 2008 com o atributo FILESTREAM.  
  
## <a name="see-also"></a>Veja também

- [Tipos de dados do SQL Server e ADO.NET](sql-server-data-types.md)
- [SQL Server operações de dados no ADO.NET](sql-server-data-operations.md)
- [Recuperando e modificando dados no ADO.NET](../retrieving-and-modifying-data.md)
- [Visão geral do ADO.NET](../ado-net-overview.md)
