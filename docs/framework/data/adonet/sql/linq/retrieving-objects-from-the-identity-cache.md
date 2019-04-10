---
title: Recuperando objetos de cache de identidade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211225"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Recuperando objetos de cache de identidade
Este tópico descreve os tipos LINQ to SQL consulta que retornam um objeto de cache de identidade que é gerenciado por <xref:System.Data.Linq.DataContext>.  
  
 Em LINQ to SQL, uma das maneiras em que <xref:System.Data.Linq.DataContext> gerencia objetos é autorizando identidades de objeto em um cache de identidade como consultas é executado. Em alguns casos, LINQ to SQL tentará recuperar um objeto de cache de identidade antes de executar uma consulta na base de dados.  
  
 Em geral, porque uma consulta LINQ to SQL para retornar um objeto de cache de identidade, a consulta deve ser baseado a chave primária de um objeto e deve retornar um único objeto. Em particular, a consulta deve estar em um dos formulários gerais mostrados abaixo.  
  
> [!NOTE]
>  Consultas pré-compilação compiladas não irão retornar objetos de cache de identidade. Para obter mais informações sobre consultas pré-compilação compiladas, consulte <xref:System.Data.Linq.CompiledQuery> e [como: Store e reutilizar consultas](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Uma consulta deve estar em um das seguintes formas gerais para recuperar um objeto de cache de identidade:  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 Nesses formulários gerais, `Function1`, `Function2`, e `predicate` são definidos como segue.  
  
 `Function1` pode ser qualquer um dos seguintes:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` pode ser qualquer um dos seguintes:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` deve ser uma expressão na qual a propriedade de chave primária do objeto é definida como um valor constante. Se um objeto tem uma chave primária definida por mais de uma propriedade, cada propriedade de chave primária deve ser definida como um valor constante. Os seguintes são exemplos de formulário `predicate` devem tomar:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Exemplo  
 O código a seguir fornece exemplos dos tipos de consultas LINQ to SQL que recuperam um objeto de cache de identidade.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- [Consulte conceitos](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Identidade do objeto](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Identidade do objeto](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
