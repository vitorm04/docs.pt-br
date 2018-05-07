---
title: Consultas LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: ef761f696eaefd6daef9a32892e4c5356a178418
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL
Você define consultas de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usando a mesma sintaxe que você em [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. A única diferença é que os objetos referenciados nas consultas são mapeados para os elementos em uma base de dados. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento. Mais especificamente, o aplicativo usa o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API para execução de consulta da solicitação. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provedor transforma a consulta em texto SQL e delega a execução para o provedor ADO. O provedor ADO retorna resultados da consulta como um `DataReader`. O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provedor converte os resultados do ADO para um <xref:System.Linq.IQueryable> coleção de objetos de usuário.  
  
> [!NOTE]
>  A maioria de operadores e métodos em tipos internos de [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] têm traduções diretas para SQL. Aqueles que [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] não pode converter gerenciar exceções de tempo de execução. Para obter mais informações, consulte [mapeamento de tipo CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 A tabela a seguir mostra as semelhanças e diferenças entre [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consulte itens.  
  
|Item|Consulta LINQ|consulta de[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]|  
|----------|----------------|----------------------------------------------------------------------|  
|Tipo de retorno da variável local que contém a consulta (para consultas que as sequências de retorno)|`IEnumerable`genérico|`IQueryable`genérico|  
|Especificando a fonte de dados|Usa o `From` (Visual Basic) ou `from` cláusula (c#)|Same|  
|Filtragem|Usa o `Where` / `where` cláusula|Same|  
|Agrupamento|Usa o `Group…By` / `groupby` cláusula|Same|  
|Selecione (se projetar)|Usa o `Select` / `select` cláusula|Same|  
|Execução adiada versus imediata|Consulte [Introdução às consultas do LINQ (c#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Same|  
|Implementar join|Usa o `Join` / `join` cláusula|Pode usar o `Join` / `join` cláusula, mas com mais eficiência usa o <xref:System.Data.Linq.Mapping.AssociationAttribute> atributo. Para obter mais informações, consulte [consulta entre relações](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Editando contra a execução local||Para obter mais informações, consulte [vs remotos. Execução local](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Passar contra consulte armazenado em cachê|Não aplicável em um cenário de memória local||  
  
## <a name="see-also"></a>Consulte também  
 [Introdução a consultas LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Operações de consulta LINQ básicas](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 [Relacionamentos de tipo em operações de consulta LINQ](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 [Conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
