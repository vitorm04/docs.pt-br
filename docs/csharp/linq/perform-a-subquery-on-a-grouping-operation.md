---
title: "Executar uma subconsulta em uma operação de agrupamento"
description: "Como executar uma subconsulta em uma operação de agrupamento."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c2c95479db10d81e748349e156f2314a6d4fccf
ms.lasthandoff: 03/13/2017

---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Executar uma subconsulta em uma operação de agrupamento

Este tópico mostra duas formas diferentes de criar uma consulta que ordena os dados de origem em grupos e, então, realiza uma subconsulta em cada grupo individualmente. A técnica básica em cada exemplo é agrupar os elementos de origem usando uma *continuação* chamada `newGroup` e, em seguida, gerar uma nova subconsulta de `newGroup`. Essa subconsulta é executada em cada novo grupo criado pela consulta externa. Observe que, nesse exemplo específico, a saída final não é um grupo, mas uma sequência simples de tipos anônimos.  
  
 Para obter mais informações sobre como agrupar, consulte [Cláusula group](../language-reference/keywords/group-clause.md).  
  
 Para obter mais informações sobre continuações, consulte [into](../language-reference/keywords/into.md). O exemplo a seguir usa uma estrutura de dados na memória como a fonte de dados, mas os mesmos princípios se aplicam a qualquer tipo de fonte de dados do LINQ.  
  
## <a name="example"></a>Exemplo 

 > [!NOTE]
 > Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).

 [!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a>Consulte também  
 [Expressões de consulta LINQ](index.md)
