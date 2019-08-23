---
title: Consultas LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 534da029664af0babc3dff6226ff095b7222c34d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915842"
---
# <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL
Você define consultas de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usando a mesma sintaxe que você em [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. A única diferença é que os objetos referenciados nas consultas são mapeados para os elementos em uma base de dados. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento. Mais especificamente, seu aplicativo usa a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API para solicitar a execução da consulta. Em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] seguida, o provedor transforma a consulta em texto SQL e delega a execução para o provedor ADO. O provedor ADO retorna os resultados da consulta `DataReader`como um. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provedor converte os resultados do ADO em uma <xref:System.Linq.IQueryable> coleção de objetos de usuário.  
  
> [!NOTE]
> A maioria dos métodos e operadores em .NET Framework tipos internos têm traduções diretas para o SQL. Aqueles que [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] não pode converter gerenciar exceções de tempo de execução. Para obter mais informações, consulte [mapeamento de tipo SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 A tabela a seguir mostra as semelhanças e diferenças entre [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consulte itens.  
  
|Item|Consulta LINQ|consulta de[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]|  
|----------|----------------|----------------------------------------------------------------------|  
|Tipo de retorno da variável local que contém a consulta (para consultas que as sequências de retorno)|`IEnumerable`genérico|`IQueryable`genérico|  
|Especificando a fonte de dados|Usa a `From` cláusula (Visual Basic) `from` ouC#()|Same|  
|Filtragem|Usa a `Where`cláusula / `where`|Same|  
|Agrupamento|Usa a `Group…By`cláusula / `groupby`|Same|  
|Selecione (se projetar)|Usa a `Select`cláusula / `select`|Same|  
|Execução adiada versus imediata|Consulte [introdução às consultas LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Same|  
|Implementar join|Usa a `Join`cláusula / `join`|Pode usar a `Join` / <xref:System.Data.Linq.Mapping.AssociationAttribute> cláusula, mas usa com mais eficiência o atributo. `join` Para obter mais informações, consulte [consultando entre relações](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Editando contra a execução local||Para obter mais informações, [consulte remoto versus Execução](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md)local.|  
|Passar contra consulte armazenado em cachê|Não aplicável em um cenário de memória local||  
  
## <a name="see-also"></a>Consulte também

- [Introdução a consultas LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Operações de consulta LINQ básicas](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relacionamentos de tipo em operações de consulta LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
