---
title: Resultados da Consulta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 3ac80cfe06f8531dcd2343f676a6f78f8eb0e8f6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854307"
---
# <a name="query-results"></a>Resultados da Consulta
Depois que uma consulta LINQ to Entities é convertida em árvores de comando e executada, os resultados da consulta geralmente são retornados como um dos seguintes:  
  
- Uma coleção de zero ou mais objetos de entidade tipados ou uma projeção de tipos complexos no modelo conceitual.  
  
- Tipos de CLR suportados pelo modelo conceitual.  
  
- Coleções internas.  
  
- Tipos anônimos.  
  
 Quando a consulta executar contra a fonte de dados, os resultados são materializados em tipos de CLR e retornados para o cliente. Qualquer materialização de objeto é executada pelo Entity Framework. Todos os erros que resultarem de uma incapacidade de mapear entre o Entity Framework e o CLR gerarão exceções durante a materialização do objeto.
  
 Se a execução da consulta retornar tipos de modelo conceitual primitivos, os resultados consistirão em tipos CLR autônomos e desconectados da Entity Framework. No entanto, se a consulta retorna uma coleção de objetos de entidade tipados, representado por <xref:System.Data.Objects.ObjectQuery%601>, os tipos são controlados pelo contexto de objeto. Todo o comportamento do objeto (como coleções filho/pai, controle de alterações, polimorfismo e assim por diante) é definido no Entity Framework. Essa funcionalidade pode ser usada em sua capacidade, conforme definido no Entity Framework. Para obter mais informações, consulte [trabalhando com objetos](../working-with-objects.md).
  
 Os tipos de Estrutura retornados de consultas (como tipos anônimos e tipos complexos anuláveis) podem ser de valor de `null` . Uma propriedade de <xref:System.Data.Objects.DataClasses.EntityCollection%601> de uma entidade retornado também pode ser o valor de `null` . Isso pode resultar de projetar a propriedade de coleção de uma entidade que é o valor de `null` , como chamar <xref:System.Linq.Queryable.FirstOrDefault%2A> em <xref:System.Data.Objects.ObjectQuery%601> que não tiver nenhum elemento.  
  
 Em determinadas situações, uma consulta pode parecer para produzir um resultado materializado durante sua execução, mas a consulta será executada no servidor e o objeto de entidade será materializado nunca em CLR. Isso pode causar problemas se você estiver como efeitos colaterais de materialization de objeto.  
  
 O exemplo a seguir contém uma classe personalizada, `MyContact`, com uma propriedade de `LastName` . Quando a propriedade de `LastName` é definida, uma variável de `count` é incrementado. Se você executa as duas consultas a seguir, a primeira consulta incrementará `count` quando a segunda consulta não. Isso ocorre porque na segunda consulta a propriedade de `LastName` é projetada de resultados e a classe de `MyContact` nunca é criada, porque não é necessário executar a consulta no armazenamento.  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
