---
title: "yield (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eb55fd5b1ade48316516cda83633935abbf8dcf9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="yield-c-reference"></a>yield (Referência de C#)
Quando você usa a palavra-chave `yield` em uma instrução, você indica que o método, o operador ou o acessador `get` em que ela é exibida é um iterador. Usar `yield` para definir um iterador elimina a necessidade de uma classe adicional explícita (a classe que mantém o estado de uma enumeração, consulte <xref:System.Collections.Generic.IEnumerator%601> para obter um exemplo) ao implementar o padrão <xref:System.Collections.IEnumerable> e <xref:System.Collections.IEnumerator> para um tipo de coleção personalizado.  
  
 O exemplo a seguir mostra as duas formas de instrução `yield`.  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>Comentários  
 Você usa uma instrução `yield return` para retornar cada elemento individualmente.  
  
 Você consome um método iterador ao usar uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ou consulta LINQ. Cada iteração do loop `foreach` chama o método iterador. Quando uma instrução `yield return` é atingida no método iterador, `expression` é retornado e o local atual no código é retido. A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.  
  
 Você pode usar uma instrução `yield break` para terminar a iteração.  
  
 Para obter mais informações sobre iteradores, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="iterator-methods-and-get-accessors"></a>Métodos de Iterador Acessadores get  
 A declaração de um iterador deve atender aos seguintes requisitos:  
  
-   O tipo de retorno deve ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   A declaração não pode ter nenhum parâmetro [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  
  
 O tipo `yield` de um iterador que retorna <xref:System.Collections.IEnumerable> ou <xref:System.Collections.IEnumerator> é `object`.  Se o iterador retornar <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Collections.Generic.IEnumerator%601>, uma conversão implícita deverá existir do tipo da expressão na instrução `yield return` para o parâmetro de tipo genérico.  
  
 Você não pode incluir uma instrução `yield return` ou `yield break` nos métodos com as seguintes características:  
  
-   Métodos anônimos. Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
-   Métodos que contêm blocos inseguros. Para obter mais informações, consulte [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 Uma instrução `yield return` não pode estar localizada em um bloco try-catch. Uma instrução `yield return` pode estar localizada no bloco try de uma instrução try-finally.  
  
 Uma instrução `yield break` pode estar localizada em um bloco try ou em um bloco catch, mas não em um bloco finally.  
  
 Se o corpo `foreach` (fora do método iterador) acionar uma exceção, um bloco `finally` no método iterador será executado.  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 O código a seguir retorna uma `IEnumerable<string>` de um método iterador e itera através de seus elementos.  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 A chamada a `MyIteratorMethod` não executa o corpo do método. Em vez disso, a chamada retorna `IEnumerable<string>` na variável `elements`.  
  
 Em uma iteração do loop `foreach`, o método <xref:System.Collections.IEnumerator.MoveNext%2A> é chamado para `elements`. Essa chamada executará o corpo de `MyIteratorMethod` até que a próxima instrução `yield return` seja atingida. A expressão retornada pela instrução `yield return` determina não apenas o valor da variável `element` para consumo pelo corpo do loop, mas também a propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A> dos elementos que é `IEnumerable<string>`.  
  
 Em cada iteração subsequente do loop `foreach`, a execução do corpo do iterador continuará de onde parou, parando novamente quando atingir uma instrução `yield return`. O loop `foreach` é concluído quando o fim do método iterador ou uma instrução `yield break` é atingida.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir contém uma instrução `yield return` dentro de um loop `for`. Cada iteração do corpo da instrução `foreach` em `Process` cria uma chamada à função iteradora `Power`. Cada chamada à função iteradora prossegue para a próxima execução da instrução `yield return` que ocorre durante a próxima iteração do loop `for`.  
  
 O tipo de retorno do método iterador é <xref:System.Collections.IEnumerable> que é um tipo de interface de iterador. Quando o método iterador é chamado, ele retorna um objeto enumerável que contém as potências de um número.  
  
 [!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um acessador `get` que é um iterador. No exemplo, cada instrução `yield return` retorna uma instância de uma classe definida pelo usuário.  
  
 [!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)

