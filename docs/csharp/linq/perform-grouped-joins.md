---
title: Executar junções agrupadas
description: Como realizar junções agrupadas.
ms.date: 12/1/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: fbdb1a69fa2f3b171935fa3a58cf9a045be0a494
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288171"
---
# <a name="perform-grouped-joins"></a>Executar junções agrupadas

A junção de grupo é útil para a produção de estruturas de dados hierárquicos. Ela combina cada elemento da primeira coleção com um conjunto de elementos correlacionados da segunda coleção.  
  
 Por exemplo, uma classe ou uma tabela de banco de dados relacional chamada `Student` pode conter dois campos: `Id` e `Name`. Uma segunda classe ou tabela de banco de dados relacional chamada `Course` pode conter dois campos: `StudentId` e `CourseTitle`. Uma junção de grupo dessas duas fontes de dados, com base na correspondência de `Student.Id` e `Course.StudentId`, agruparia cada `Student` com uma coleção de objetos `Course` (que pode estar vazia).  
  
> [!NOTE]
>  Cada elemento da primeira coleção aparece no conjunto de resultados de uma junção de grupo, independentemente de se os elementos correlacionados encontram-se na segunda coleção. Caso nenhum elemento correlacionado seja encontrado, a sequência de elementos correlacionados desse elemento ficará vazia. O seletor de resultado, portanto, tem acesso a todos os elementos da primeira coleção. Isso difere do seletor de resultado de uma junção que não é de grupo, que não pode acessar os elementos da primeira coleção que não têm correspondência na segunda coleção.  
  
 O primeiro exemplo deste tópico mostra como realizar uma junção de grupo. O segundo exemplo mostra como usar uma junção de grupo para criar elementos XML.  
  
## <a name="example"></a>Exemplo  
  
### <a name="group-join-example"></a>Exemplo de junção de grupo  
 O exemplo a seguir realiza uma junção de grupo de objetos do tipo `Person` e `Pet` com base em `Person` correspondente à propriedade `Pet.Owner`. Ao contrário de uma junção que não é de grupo, que produziria um par de elementos para cada correspondência, a junção de grupo produz apenas um objeto resultante para cada elemento da primeira coleção, que neste exemplo é um objeto `Person`. Os elementos correspondentes da segunda coleção, que neste exemplo são objetos `Pet`, são agrupados em uma coleção. Por fim, a função de seletor de resultado cria um tipo anônimo para cada correspondência que consiste em `Person.FirstName` e em uma coleção de objetos `Pet`.  
  
 [!code-csharp[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a>Exemplo  
  
### <a name="group-join-to-create-xml-example"></a>Junção de grupo para criar um exemplo de XML  
 As junções de grupo são ideais para a criação de XML usando o LINQ to XML. O exemplo a seguir é semelhante ao exemplo anterior, exceto que em vez de criar tipos anônimos, a função de seletor de resultado cria elementos XML que representam os objetos associados.  
  
 [!code-csharp[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Executar junções internas](perform-inner-joins.md)  
 [Executar junções externas esquerdas](perform-left-outer-joins.md)  
 [Tipos anônimos](../programming-guide/classes-and-structs/anonymous-types.md)  
 
