---
title: "Executar junções externas esquerdas"
description: "Como executar junções externas esquerdas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 0c28c85bf933a411403aefcb91801d28fe1c268e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="perform-left-outer-joins"></a>Executar junções externas esquerdas
Uma junção externa esquerda é uma junção em que cada elemento da primeira coleção é retornado, mesmo que ele tenha elementos correlacionados na segunda coleção. É possível usar o LINQ para executar uma junção externa esquerda chamando o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo para executar uma junção externa esquerda.  
  
 A primeira etapa da produção de uma junção externa esquerda de duas coleções é executar uma junção interna usando uma junção de grupo. (Consulte [Executar junções internas](perform-inner-joins.md) para obter uma explicação desse processo.) Neste exemplo, a lista de objetos `Person` é associada internamente à lista de objetos `Pet` com base em um objeto `Person` correspondente a `Pet.Owner`.  
  
 A segunda etapa é incluir cada elemento da primeira coleção (esquerda) no conjunto de resultados, mesmo que esse elemento não tenha nenhuma correspondência na coleção direita. Isso é feito chamando <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> em cada sequência de elementos correspondentes da junção de grupo. Neste exemplo, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> é chamado em cada sequência de objetos `Pet` correspondentes. O método retorna uma coleção que contém um valor padrão único se a sequência de objetos `Pet` correspondentes estiver vazia para qualquer objeto `Person`, garantindo assim que cada objeto `Person` seja representado no conjunto de resultados.  
  
> [!NOTE]
>  O valor padrão para um tipo de referência é `null`; portanto, o exemplo procura uma referência nula antes de acessar cada elemento de cada coleção `Pet`.  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Executar junções internas](perform-inner-joins.md)  
 [Executar junções agrupadas](perform-grouped-joins.md)  
 [Tipos anônimos](../programming-guide/classes-and-structs/anonymous-types.md)  
 
