---
title: SqlTypes e DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 61308d6c2c66e1c163431ced8d9c66980705b9c7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes e DataSet
O ADO.NET 2.0 introduziu suporte avançado a tipos para `DataSet` por meio do namespace <xref:System.Data.SqlTypes>. Os tipos em <xref:System.Data.SqlTypes> são criados para fornecer tipos de dados com a mesma semântica e precisão que os tipos de dados em um banco de dados do SQL Server. Cada tipo de dados em <xref:System.Data.SqlTypes> tem um tipo de dados equivalente no SQL Server, com a mesma representação de dados subjacentes.  
  
 Usar <xref:System.Data.SqlTypes> diretamente em um <xref:System.Data.DataSet> confere vários benefícios no trabalho com tipos de dados do SQL Server. <xref:System.Data.SqlTypes> oferece suporte à mesma semântica que os tipos de dados nativos do SQL Server. Especificar um dos <xref:System.Data.SqlTypes> na definição de <xref:System.Data.DataColumn> elimina a perda de precisão que pode ocorrer ao converter tipos de dados decimais ou numéricos em um dos tipos de dados CLR (Common Language Runtime).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um objeto <xref:System.Data.DataTable>, definindo explicitamente os tipos de dados <xref:System.Data.DataColumn> usando <xref:System.Data.SqlTypes> em vez de tipos CLR. O código preenche <xref:System.Data.DataTable> com dados da tabela Sales.SalesOrderDetail no banco de dados AdventureWorks no SQL Server. A saída exibida na janela do console mostra o tipo de dados de cada coluna e os valores recuperados do SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Mapeamentos de tipo de dados do SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Configurando parâmetros e tipos de dados de parâmetro](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
