---
title: "Executar junções externas esquerdas"
description: "Como executar junções externas esquerdas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d81f6e9df228dc6eec985253f53b70a95493ed42
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="perform-left-outer-joins"></a>Executar junções externas esquerdas
Uma junção externa esquerda é uma junção em que cada elemento da primeira coleção é retornado, mesmo que ele tenha elementos correlacionados na segunda coleção. É possível usar o LINQ para executar uma junção externa esquerda chamando o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo para executar uma junção externa esquerda.  
  
 A primeira etapa da produção de uma junção externa esquerda de duas coleções é executar uma junção interna usando uma junção de grupo. (Consulte [Executar junções internas](perform-inner-joins.md) para obter uma explicação desse processo.) Neste exemplo, a lista de objetos `Person` é associada internamente à lista de objetos `Pet` com base em um objeto `Person` correspondente a `Pet.Owner`.  
  
 A segunda etapa é incluir cada elemento da primeira coleção (esquerda) no conjunto de resultados, mesmo que esse elemento não tenha nenhuma correspondência na coleção direita. Isso é feito chamando <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> em cada sequência de elementos correspondentes da junção de grupo. Neste exemplo, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> é chamado em cada sequência de objetos `Pet` correspondentes. O método retorna uma coleção que contém um valor padrão único se a sequência de objetos `Pet` correspondentes estiver vazia para qualquer objeto `Person`, garantindo assim que cada objeto `Person` seja representado no conjunto de resultados.  
  
> [!NOTE]
>  O valor padrão para um tipo de referência é `null`; portanto, o exemplo procura uma referência nula antes de acessar cada elemento de cada coleção `Pet`.  
  
 [!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Executar junções internas](perform-inner-joins.md)   
 [Executar junções agrupadas](perform-grouped-joins.md)   
 [Tipos anônimos](../programming-guide/classes-and-structs/anonymous-types.md)   
 

