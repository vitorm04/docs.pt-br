---
title: 'Como: Chamar funções definidas pelo usuário in-line'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 39eeab06952e1d8a1128580a2be79ed4711d58d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359394"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Como: Chamar funções definidas pelo usuário in-line
Embora você possa chamar funções definidas pelo usuário embutidos, as funções que são incluídas em uma consulta cuja execução é adiada não são executadas até que a consulta. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Quando você chama a mesma função fora de uma consulta, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria uma consulta simples de expressão de chamada de método. A seguir está a sintaxe do SQL (parâmetro `@p0` é associado à constante passada dentro):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria o seguinte:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemplo  
 A seguir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consulta, você pode ver um embutido chamada para o método de função definida pelo usuário gerado `ReverseCustName`. A função não é executada imediatamente porque a execução da consulta é adiada. O SQL compilado para esta consulta converte a uma chamada para a função definida pelo usuário na base de dados (consulte o código SQL seguir a consulta).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Funções definidas pelo usuário](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
