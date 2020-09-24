---
title: 'Como: chamar funções embutidas definidas pelo usuário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
ms.openlocfilehash: 24b23c436fd7d4d5f3fdd0c364c0bdaf6feb8d1b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161341"
---
# <a name="how-to-call-user-defined-functions-inline"></a>Como: chamar funções embutidas definidas pelo usuário

Embora você possa chamar funções definidas pelo usuário embutidos, as funções que são incluídas em uma consulta cuja execução é adiada não são executadas até que a consulta. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Quando você chama a mesma função fora de uma consulta, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria uma consulta simples de expressão de chamada de método. A seguir está a sintaxe do SQL (parâmetro `@p0` é associado à constante passada dentro):  
  
```sql  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria o seguinte:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemplo  

 Na consulta a seguir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , você pode ver uma chamada embutida para o método de função definido pelo usuário gerado `ReverseCustName` . A função não é executada imediatamente porque a execução da consulta é adiada. O SQL compilado para esta consulta converte a uma chamada para a função definida pelo usuário na base de dados (consulte o código SQL seguir a consulta).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```sql  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Confira também

- [Funções definidas pelo usuário](user-defined-functions.md)
