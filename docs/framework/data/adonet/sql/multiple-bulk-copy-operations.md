---
title: Várias operações de cópia em massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 838f56311f165c99c71cc734576bbdb53a946b7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792071"
---
# <a name="multiple-bulk-copy-operations"></a>Várias operações de cópia em massa
Você pode executar várias operações de cópia em massa usando uma única instância <xref:System.Data.SqlClient.SqlBulkCopy> de uma classe. Se os parâmetros de operação forem alterados entre cópias (por exemplo, o nome da tabela de destino), você deverá atualizá-los antes de qualquer chamada subsequente para qualquer um dos métodos **WriteToServer** , conforme demonstrado no exemplo a seguir. A menos que seja alterado explicitamente, todos os valores de propriedade permanecem os mesmos que estavam na operação de cópia em massa anterior para uma determinada instância.  
  
> [!NOTE]
> Executar várias operações de cópia em massa usando a mesma <xref:System.Data.SqlClient.SqlBulkCopy> instância do é geralmente mais eficiente do que usar uma instância separada para cada operação.  
  
 Se você executar várias operações de cópia em massa usando <xref:System.Data.SqlClient.SqlBulkCopy> o mesmo objeto, não haverá restrições se as informações de origem ou destino forem iguais ou diferentes em cada operação. No entanto, você deve garantir que as informações de associação de coluna sejam definidas corretamente cada vez que você gravar no servidor.  
  
> [!IMPORTANT]
> Este exemplo não será executado a menos que você tenha criado as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](bulk-copy-example-setup.md). Esse código é fornecido para demonstrar a sintaxe somente para uso de **SqlBulkCopy** . Se as tabelas de origem e destino estiverem localizadas na mesma instância de SQL Server, será mais fácil e rápido usar uma instrução Transact `INSERT … SELECT` -SQL para copiar os dados.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Operações de cópia em massa no SQL Server](bulk-copy-operations-in-sql-server.md)
- [ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)
