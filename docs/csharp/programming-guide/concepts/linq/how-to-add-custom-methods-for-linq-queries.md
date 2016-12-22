---
title: "Como: adicionar m&#233;todos personalizados para consultas LINQ (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: adicionar m&#233;todos personalizados para consultas LINQ (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode estender o conjunto de métodos que você pode usar para consultas LINQ, adicionando métodos de extensão para o <xref:System.Collections.Generic.IEnumerable%601> interface. Por exemplo, além do padrão médio ou máximo de operações, você pode criar um método de agregação personalizado para calcular um valor único de uma seqüência de valores. Você também pode criar um método que funciona como um filtro personalizado ou uma transformação de dados específicos para uma sequência de valores e retorna uma nova sequência. São exemplos de tais métodos <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, e <xref:System.Linq.Enumerable.Reverse%2A>.  
  
 Quando você estende o <xref:System.Collections.Generic.IEnumerable%601> interface, você pode aplicar seus métodos personalizados para qualquer coleção enumerável. Para obter mais informações, consulte [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## Adicionar um método de agregação  
 Um método de agregação computa um valor único de um conjunto de valores. LINQ fornece vários métodos de agregação, incluindo <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, e <xref:System.Linq.Enumerable.Max%2A>. Você pode criar seu próprio método de agregação, adicionando um método de extensão para o <xref:System.Collections.Generic.IEnumerable%601> interface.  
  
 O exemplo de código a seguir mostra como criar um método de extensão chamado `Median` para calcular uma média para uma seqüência de números do tipo `double`.  
  
```c#  
public static class LINQExtension  
{  
    public static double Median(this IEnumerable<double> source)  
    {  
        if (source.Count() == 0)  
        {  
            throw new InvalidOperationException("Cannot compute median for an empty set.");  
        }  
  
        var sortedList = from number in source  
                         orderby number  
                         select number;  
  
        int itemIndex = (int)sortedList.Count() / 2;  
  
        if (sortedList.Count() % 2 == 0)  
        {  
            // Even number of items.  
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;  
        }  
        else  
        {  
            // Odd number of items.  
            return sortedList.ElementAt(itemIndex);  
        }  
    }  
}  
```  
  
 Chamar esse método de extensão para qualquer coleção enumerável da mesma maneira que você chamar outros métodos de agregação do <xref:System.Collections.Generic.IEnumerable%601> interface.  
  
 O exemplo de código a seguir mostra como usar o `Median` método para uma matriz do tipo `double`.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### Um método de agregação para aceitar vários tipos de sobrecarga  
 Você pode sobrecarregar o método de agregação para que ele aceite sequências de vários tipos. A abordagem padrão é criar uma sobrecarga para cada tipo. Outra abordagem é criar uma sobrecarga que se um tipo genérico e convertê\-lo em um tipo específico, usando um representante. Você também pode combinar as duas abordagens.  
  
#### Para criar uma sobrecarga para cada tipo  
 Você pode criar uma sobrecarga específica para cada tipo que você deseja oferecer suporte. O exemplo de código a seguir mostra uma sobrecarga de `Median` método para o `integer` tipo.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Agora você pode chamar o `Median` sobrecargas para ambos `integer` e `double` tipos, conforme mostrado no código a seguir:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### Para criar uma sobrecarga genérica  
 Você também pode criar uma sobrecarga que aceita uma seqüência de objetos genéricos. Essa sobrecarga leva um delegado como parâmetro e usa\-o para converter uma sequência de objetos de um tipo genérico a um tipo específico.  
  
 O código a seguir mostra uma sobrecarga de `Median` método que usa o <xref:System.Func%602> Delegar como um parâmetro. Esse delegado pega um objeto de tipo genérico T e retorna um objeto do tipo `double`.  
  
```c#  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 Agora você pode chamar o `Median` método para uma sequência de objetos de qualquer tipo. Se o tipo não tem sua própria sobrecarga de método, você precisa passar um parâmetro delegado. No c\#, você pode usar uma expressão lambda para essa finalidade. Além disso, no Visual Basic, se você usar o `Aggregate` ou `Group By` cláusula em vez da chamada de método, você pode passar qualquer valor ou expressão que está no escopo dessa cláusula.  
  
 O exemplo de código a seguir mostra como chamar o `Median` método para uma matriz de inteiros e uma matriz de cadeias de caracteres. Para cadeias de caracteres, a mediana para os comprimentos das cadeias de caracteres na matriz é calculada. O exemplo mostra como passar o <xref:System.Func%602> delegar o parâmetro para o `Median` método para cada caso.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## Adicionando um método que retorna uma coleção  
 Você pode estender o <xref:System.Collections.Generic.IEnumerable%601> interface com um método de consulta personalizada que retorna uma seqüência de valores. Nesse caso, o método deve retornar uma coleção do tipo <xref:System.Collections.Generic.IEnumerable%601>. Esses métodos podem ser usados para aplicar transformações de dados ou filtros para uma seqüência de valores.  
  
 O exemplo a seguir mostra como criar um método de extensão chamado `AlternateElements` que retorna todos os outros elementos em uma coleção, começando do primeiro elemento.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Você pode chamar esse método de extensão para qualquer coleção enumerável exatamente como você poderia chamar outros métodos do <xref:System.Collections.Generic.IEnumerable%601> da interface, conforme mostrado no código a seguir:  
  
```c#  
string[] strings = { "a", "b", "c", "d", "e" };  
  
var query = strings.AlternateElements();  
  
foreach (var element in query)  
{  
    Console.WriteLine(element);  
}  
/*  
 This code produces the following output:  
  
 a  
 c  
 e  
*/  
```  
  
## Consulte também  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)