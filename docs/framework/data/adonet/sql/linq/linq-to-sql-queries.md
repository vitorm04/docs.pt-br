---
title: Consultas LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 478138d26d6cdf656b2487c637a5eb13784126e9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634373"
---
# <a name="linq-to-sql-queries"></a>Consultas LINQ to SQL
Você define [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consultas usando a mesma sintaxe que faria no LINQ. A única diferença é que os objetos referenciados nas consultas são mapeados para os elementos em uma base de dados. Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento. Mais especificamente, seu aplicativo usa a API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para solicitar a execução da consulta. O provedor de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] transforma a consulta em texto SQL e delega a execução para o provedor ADO. O provedor ADO retorna os resultados da consulta como um `DataReader`. O provedor de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte os resultados do ADO em uma coleção <xref:System.Linq.IQueryable> de objetos de usuário.  
  
> [!NOTE]
> A maioria dos métodos e operadores em .NET Framework tipos internos têm traduções diretas para o SQL. Aqueles que o LINQ não pode converter geram exceções de tempo de execução. Para obter mais informações, consulte [mapeamento de tipo SQL-CLR](sql-clr-type-mapping.md).  
  
 A tabela a seguir mostra as semelhanças e diferenças entre os itens de consulta LINQ e [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Item|Consulta LINQ|consulta de[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]|  
|----------|----------------|----------------------------------------------------------------------|  
|Tipo de retorno da variável local que contém a consulta (para consultas que as sequências de retorno)|`IEnumerable`genérico|`IQueryable`genérico|  
|Especificando a fonte de dados|Usa a cláusula `From` (Visual Basic) ou `from`C#()|Same|  
|Filtragem|Usa a cláusula de `where` de /de `Where`|Same|  
|Agrupamento|Usa a cláusula de `groupby` de /de `Group…By`|Same|  
|Selecione (se projetar)|Usa a cláusula de `select` de /de `Select`|Same|  
|Execução adiada versus imediata|Consulte [introdução às consultas LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Same|  
|Implementar join|Usa a cláusula de `join` de /de `Join`|Pode usar a cláusula `Join`/`join`, mas usa mais efetivamente o atributo <xref:System.Data.Linq.Mapping.AssociationAttribute>. Para obter mais informações, consulte [consultando entre relações](querying-across-relationships.md).|  
|Editando contra a execução local||Para obter mais informações, consulte [execução remota versus local](remote-vs-local-execution.md).|  
|Passar contra consulte armazenado em cachê|Não aplicável em um cenário de memória local||  
  
## <a name="see-also"></a>Veja também

- [Introdução a consultas LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Operações de consulta LINQ básicas](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Relacionamentos de tipo em operações de consulta LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Conceitos de consulta](query-concepts.md)
