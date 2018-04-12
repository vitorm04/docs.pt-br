---
title: Como acessar uma classe de coleção com foreach (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a>Como acessar uma classe de coleção com foreach (Guia de Programação em C#)
O exemplo de código a seguir ilustra como gravar uma classe de coleção não genérica que pode ser usada com [foreach](../../../csharp/language-reference/keywords/foreach-in.md). O exemplo define uma classe do criador de token da cadeia de caracteres.  
  
> [!NOTE]
>  Este exemplo representa a prática recomendada somente quando não é possível usar uma classe de coleção genérica. Para obter um exemplo de como implementar uma classe de coleção genérica fortemente tipada com suporte para <xref:System.Collections.Generic.IEnumerable%601>, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
 No exemplo, o segmento de código a seguir utiliza a classe `Tokens` para interromper a frase: “Esta é uma frase de exemplo.” em tokens, usando ' ' e '-' como separadores. O código, em seguida, exibe esses tokens usando uma instrução `foreach`.  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Internamente, a classe `Tokens` usa uma matriz para armazenar os tokens. Já que as matrizes implementam <xref:System.Collections.IEnumerator> e <xref:System.Collections.IEnumerable>, o exemplo de código poderia ter usado os métodos de enumeração da matriz (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.Current%2A>) em vez de defini-los na classe `Tokens`. As definições de método estão incluídas no exemplo para esclarecer como elas são definidas e o que cada uma delas faz.  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 Em C#, não é necessário que uma classe de coleção implemente <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para que seja compatível com `foreach`. Se a classe tiver os membros <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.Current%2A> necessários, ela funcionará com `foreach`. A vantagem de omitir as interfaces é que isso permite definir um tipo de retorno para `Current` mais específico do que <xref:System.Object>. Isso fornece segurança de tipos.  
  
 Por exemplo, altere as seguintes linhas no exemplo anterior.  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 Como `Current` retorna uma cadeia de caracteres, o compilador pode detectar quando um tipo incompatível for usado em uma instrução `foreach`, conforme mostrado no código a seguir.  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 A desvantagem de omitir <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> é que a classe de coleção já não é interoperável com as instruções `foreach` ou instruções equivalentes de outras linguagens Common Language Runtime.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.Generic>  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Matrizes](../../../csharp/programming-guide/arrays/index.md)  
 [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
