---
title: Consultas de agregação
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 1c8f6191cfb832a71bd32c60db492eafb8ca22ca
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858686"
---
# <a name="aggregate-queries"></a>Consultas de agregação
O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dá suporte aos operadores de agregação `Average`, `Count`, `Max`, `Min` e `Sum`. Observe as seguintes características dos operadores de agregação no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   As consultas de agregação são executadas imediatamente.  
  
     Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   As consultas de agregação geralmente retornam um número em vez de uma coleção.  
  
     Para obter mais informações, consulte [operações de agregação](https://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4).  
  
-   Você não pode chamar agregações em tipos anônimos.  
  
 Os exemplos nos seguintes tópicos derivam do banco de dados de exemplo Northwind. Para obter mais informações, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Retornar o valor médio de uma sequência numérica](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 Demonstra como usar o operador <xref:System.Linq.Enumerable.Average%2A>.  
  
 [Contar o número de elementos em uma sequência](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 Demonstra como usar o operador <xref:System.Linq.Enumerable.Count%2A>.  
  
 [Localizar o valor máximo em uma sequência numérica](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 Demonstra como usar o operador <xref:System.Linq.Enumerable.Max%2A>.  
  
 [Localizar o valor mínimo em uma sequência numérica](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 Demonstra como usar o operador <xref:System.Linq.Enumerable.Min%2A>.  
  
 [Calcular a soma dos valores em uma sequência numérica](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 Demonstra como usar o operador <xref:System.Linq.Enumerable.Sum%2A>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 Fornece links para consultas do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no Visual Basic e no C#.  
  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 Fornece links para tópicos que explicam os conceitos para criar consultas do [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] no [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Introdução a consultas LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 Explica como as consultas funcionam no [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].
