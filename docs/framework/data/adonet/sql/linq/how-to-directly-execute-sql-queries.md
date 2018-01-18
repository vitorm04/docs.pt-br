---
title: Como executar diretamente consultas SQL
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 000a7c50edacbae09675a9f9069f56aa6cd211f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-directly-execute-sql-queries"></a>Como executar diretamente consultas SQL
O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL parametrizadas (em formato de texto) e as envia para o SQL Server para processamento.  
  
 O SQL não pode executar a variedade de métodos que podem estar disponíveis localmente para seu aplicativo. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta converter esses métodos locais em operações e funções equivalentes que estão disponíveis no ambiente SQL. A maioria dos métodos e operadores em tipos internos de [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] têm conversões diretas para comandos SQL. Alguns podem ser gerados das funções que estão disponíveis. Aqueles que não podem ser produzidos geram exceções em tempo de execução. Para obter mais informações, consulte [mapeamento de tipo CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Nos casos em que uma consulta de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é insuficiente para uma tarefa especializada, você pode usar o método <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> para executar uma consulta SQL e, depois, converter o resultado da consulta diretamente em objetos.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, suponha que os dados da classe `Customer` são espalhados em duas tabelas (customer1 e customer2). A consulta retorna uma sequência de objetos `Customer`.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Como os nomes de coluna nos resultados da tabela correspondem a propriedades de coluna de sua classe de entidade, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria os objetos fora de qualquer consulta SQL.  
  
## <a name="example"></a>Exemplo  
 O método <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> também permite parâmetros. Use um código como o mostrado a seguir para executar uma consulta parametrizada.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Os parâmetros são expressos no texto da consulta usando as mesmas chaves usadas por `Console.WriteLine()` e `String.Format()`. Na verdade, `String.Format()` é chamado de fato na cadeia de consulta que você fornecer, substituir os parâmetros entre chaves com nomes de parâmetro gerados como @p0, @p1 ..., @p(n).  
  
## <a name="see-also"></a>Consulte também  
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Consultando o banco de dados](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
