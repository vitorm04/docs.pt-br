---
title: Exemplo de encadeamento de consultas (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205418"
---
# <a name="chaining-queries-example-c"></a>Exemplo de encadeamento de consultas (C#)
Este exemplo compila no exemplo anterior e mostra o que acontece quando você encadeia duas consultas que usam execução adiada e avaliação lenta.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, um outro método de extensão é apresentado, `AppendString`, que acrescenta uma cadeia de caracteres especificada em cada cadeia de caracteres na coleção de origem, e produz nas novas cadeias de caracteres.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Esse exemplo gera a saída a seguir:  
  
```output  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 Nesse exemplo, você pode ver que cada método de extensão opera um de cada vez para cada item na coleção de origem.  
  
 O que deve ser claro desse exemplo é o mesmo que nós encadeemos juntos consultas que rendem coleções, qualquer coleção intermediária é materializada. Em vez disso, cada item é passado de um método lenta a seguir. Isso resulta em uma pegada muito menor de memória do que uma abordagem que recebe primeiro uma matriz de cadeias de caracteres, então cria uma segunda matriz de cadeias de caracteres que foram convertidos para maiúsculas, e criar finalmente uma terceira matriz de cadeias de caracteres onde cada cadeia de caracteres tem os pontos de exclamação acrescentados a ele.  
  
 O próximo tópico neste tutorial mostra o materialization intermediário:  
  
- [Materialização intermediária (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Confira também

- [Tutorial: encadear consultas juntas (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
