---
title: Exemplo de encadeamento de consultas (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 74d3dcaca686487d79a90f28faf4d9c00218f6a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
  
 Este exemplo gera a seguinte saída:  
  
```  
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
  
-   [Materialização intermediária (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: encadear consultas juntas (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
