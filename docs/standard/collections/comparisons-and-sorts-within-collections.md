---
title: "Comparações e classificações dentro de coleções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 826adbecfc6a57b05db482766baae397ce72bc9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="comparisons-and-sorts-within-collections"></a>Comparações e classificações dentro de coleções
As classes <xref:System.Collections> executam comparações em quase todos os processos envolvidos no gerenciamento de coleções, seja procura pelo elemento para remoção ou retorno do valor de um par de chaves e valores.  
  
 As coleções normalmente usam um comparador de igualdade e/ou um comparador de classificação. Dois constructos são usados para comparações.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Verificando a igualdade  
 Métodos, tais como `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A> e `Remove`, usam um comparador de igualdade para os elementos da coleção. Se a coleção for genérica, os itens serão comparados com relação à igualdade, de acordo com as seguintes diretrizes:  
  
-   Se o tipo T implementa a interface genérica <xref:System.IEquatable%601>, então o comparador de igualdade será o método <xref:System.IEquatable%601.Equals%2A> dessa interface.  
  
-   Se o tipo T não implementa <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> será usado.  
  
 Além disso, algumas sobrecargas de construtores para coleções de dicionários aceitam uma implementação <xref:System.Collections.Generic.IEqualityComparer%601>, que é usada para comparar chaves com relação à igualdade. Para ver um exemplo, consulte o construtor <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType>.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Determinando a ordem de classificação  
 Métodos como `BinarySearch` e `Sort` usam um comparador de ordenação para os elementos da coleção. As comparações podem ser entre elementos da coleção ou entre um elemento e um valor especificado. Para comparar objetos, há o conceito de um `default comparer` e um `explicit comparer`.  
  
 O comparador padrão baseia-se em pelo menos um dos objetos que estão sendo comparados para implementar a interface **IComparable**. É uma boa prática implementar **IComparable** em todas as classes usadas como valores em uma coleção de lista ou como chaves em uma coleção de dicionário. Para uma coleção genérica, a comparação de igualdade é determinada de acordo com o seguinte:  
  
-   Se o tipo T implementa a interface genérica <xref:System.IComparable%601?displayProperty=nameWithType>, então o comparador padrão será o método <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> dessa interface.  
  
-   Se o tipo T implementa a interface não genérica <xref:System.IComparable?displayProperty=nameWithType>, então o comparador padrão será o método <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> dessa interface.  
  
-   Se o tipo T não implementar nenhuma das interfaces, não haverá um comparador padrão e um comparador ou um delegado de comparação deverá ser fornecido explicitamente.  
  
 Para fornecer comparações explícitas, alguns métodos aceitam uma implementação de **IComparer** como um parâmetro. Por exemplo, o método <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> aceita uma implementação <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.  
  
 A configuração de cultura atual do sistema pode afetar as comparações e as classificações dentro de uma coleção. Por padrão, as comparações e classificações nas classes **Collections** levam em conta a cultura. Para ignorar a configuração de cultura e assim obter comparação consistente e classificar os resultados, use o <xref:System.Globalization.CultureInfo.InvariantCulture%2A> com sobrecargas de membros que aceitam uma <xref:System.Globalization.CultureInfo>. Para obter mais informações, consulte [Executando operações de cadeia de caracteres que não levam em conta a cultura em coleções](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) e [Executando operações de cadeia de caracteres que não levam em conta a cultura em matrizes](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Exemplo de igualdade e classificação  
 O código a seguir demonstra uma implementação de <xref:System.IEquatable%601> e <xref:System.IComparable%601> em um objeto de negócios simples. Além disso, quando o objeto é armazenado em uma lista e classificado, você verá que chamar o método <xref:System.Collections.Generic.List%601.Sort> resulta no uso do comparador padrão para o tipo `Part` e o método <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> implementado usando um método anônimo.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
