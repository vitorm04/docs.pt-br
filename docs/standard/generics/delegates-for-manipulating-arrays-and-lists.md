---
title: "Delegados genéricos para manipulação de matrizes e listas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 905f30d8b7e6d7c10a0e2b32109076e2950a99ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegados genéricos para manipulação de matrizes e listas
Este tópico fornece uma visão geral dos representantes genéricos para conversões, predicados de pesquisa e ações a serem tomadas nos elementos de uma matriz ou coleção.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegados genéricos para manipulação de matrizes e listas  
 O <xref:System.Action%601> delegado genérico representa um método que executa uma ação em um elemento do tipo especificado. Você pode criar um método que executa a ação desejada no elemento, criar uma instância do <xref:System.Action%601> delegado para representar esse método e, em seguida, passa a matriz e o representante para a <xref:System.Array.ForEach%2A?displayProperty=nameWithType> método estático genérico. O método é chamado para cada elemento da matriz.  
  
 O <xref:System.Collections.Generic.List%601> também fornece uma classe genérica um <xref:System.Collections.Generic.List%601.ForEach%2A> método que usa o <xref:System.Action%601> delegate. Esse método não é genérico.  
  
> [!NOTE]
>  Isso é um ponto interessante sobre tipos e métodos genéricos. O <xref:System.Array.ForEach%2A?displayProperty=nameWithType> método deve ser estático (`Shared` no Visual Basic) e genérico porque <xref:System.Array> não é genérico tipo; o único motivo pelo qual você pode especificar um tipo para <xref:System.Array.ForEach%2A?displayProperty=nameWithType> para operar é que o método tenha sua própria lista de parâmetros de tipo. Por outro lado, não genérica <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> método pertence à classe genérica <xref:System.Collections.Generic.List%601>, portanto, ele simplesmente usa o parâmetro de tipo de sua classe. A classe é fortemente tipada, portanto, o método pode ser um método de instância.  
  
 O <xref:System.Predicate%601> delegado genérico representa um método que determina se um determinado elemento atende aos critérios que você definir. Você pode usá-lo com os seguintes métodos genéricos estáticos de <xref:System.Array> para procurar por um elemento ou um conjunto de elementos: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, e <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>também funciona com os métodos de instância não-genérica correspondentes do <xref:System.Collections.Generic.List%601> classe genérica.  
  
 O <xref:System.Comparison%601> delegado genérico permite que você fornecer uma ordem de classificação de matriz ou lista de elementos que não têm uma ordem de classificação nativa, ou para substituir a ordem de classificação nativa. Crie um método que executa a comparação, crie uma instância do <xref:System.Comparison%601> delegado para representar o método e, em seguida, passa a matriz e o representante para a <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> método estático genérico. O <xref:System.Collections.Generic.List%601> classe genérica fornece uma sobrecarga de método de instância correspondente, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 O <xref:System.Converter%602> delegado genérico permite que você defina uma conversão entre dois tipos e para converter uma matriz de um tipo em uma matriz do outro ou para converter uma lista de um tipo em uma lista das outras. Criar um método que converte os elementos de uma lista existente para um novo tipo, crie uma instância para representar o método e usar o <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> método estático genérico para produzir uma matriz do novo tipo de matriz original, ou o <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> genérico método de instância para produzir uma lista do novo tipo da lista original.  
  
### <a name="chaining-delegates"></a>Encadeando delegados  
 Muitos dos métodos que usam esses delegados retornam uma matriz ou lista, que pode ser passada para outro método. Por exemplo, se você quiser selecionar determinados elementos de uma matriz, converter esses elementos em um novo tipo e salvá-los em uma nova matriz, você pode passar a matriz retornada pelo <xref:System.Array.FindAll%2A> método genérico para o <xref:System.Array.ConvertAll%2A> método genérico. Se o novo tipo de elemento não tiver uma ordem de classificação natural, você pode passar a matriz retornada pelo <xref:System.Array.ConvertAll%2A> método genérico para o <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> método genérico.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Genéricos](../../../docs/standard/generics/index.md)  
 [Coleções genéricas no .NET Framework](../../../docs/standard/generics/collections.md)  
 [Interfaces genéricas](../../../docs/standard/generics/interfaces.md)  
 [Covariância e Contravariância](../../../docs/standard/generics/covariance-and-contravariance.md)
