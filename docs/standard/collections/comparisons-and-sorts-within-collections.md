---
title: "Comparações e classificações dentro de coleções"
description: "Comparações e classificações dentro de coleções"
keywords: .NET, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c7b7c005-628d-427a-91ad-af0c3958c00e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 6826c0c2e86d0a1add1f88b001c13143ee098634
ms.lasthandoff: 03/02/2017

---

# <a name="comparisons-and-sorts-within-collections"></a>Comparações e classificações dentro de coleções

As classes [System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) executam comparações em quase todos os processos envolvidos no gerenciamento de coleções, seja pesquisar pelo elemento a ser removido ou retornar o valor de um par de chave e valor.

As coleções normalmente usam um comparador de igualdade e/ou um comparador de ordenação. Dois constructos são usados para comparações. 

## <a name="checking-for-equality"></a>Verificando a igualdade

Métodos como `Contains`, `IndexOf`, `LastIndexOf` e `Remove` usam um comparador de igualdade para os elementos da coleção. Se a coleção for genérica, os itens serão comparados com relação à igualdade, de acordo com as seguintes diretrizes:

*   Se o tipo T implementar a interface genérica [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1), então o comparador de igualdade será o método `Equals` dessa interface.

*   Se o tipo T não implementar `IEquatable<T>`, `Object.Equals` será usado.

Além disso, algumas sobrecargas de construtores para coleções de dicionários aceitam uma implementação [IEqualityComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEqualityComparer-1), que é usada para comparar chaves com relação à igualdade.

## <a name="determining-sort-order"></a>Determinando a ordem de classificação

Métodos como `BinarySearch` e `Sort` usam um comparador de ordenação para os elementos da coleção. As comparações podem ser entre elementos da coleção ou entre um elemento e um valor especificado. Para comparar objetos, há o conceito de um comparador padrão e um comparador explícito. 

O comparador padrão se baseia em pelo menos um dos objetos que estão sendo comparados para implementar a interface `IComparable`. É uma boa prática implementar `IComparable` em todas as classes usadas como valores em uma coleção de listas ou como chaves em uma coleção de dicionários. Para uma coleção genérica, a comparação de igualdade é determinada de acordo com o seguinte:

*   Se o tipo T implementar a interface genérica [System.IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1), o comparador padrão será o método `CompareTo(T)` dessa interface.

*   Se o tipo T implementar a interface não genérica [System.IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable), o comparador padrão será o método `CompareTo` (objeto) dessa interface.

*   Se o tipo T não implementar nenhuma das interfaces, não haverá um comparador padrão e um comparador ou um delegado de comparação deverá ser fornecido explicitamente.

Para fornecer comparações explícitas, alguns métodos aceitam uma implementação `IComparer` como parâmetro. Por exemplo, o método `List<T>.Sort` aceita uma implementação [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1). 

## <a name="equality-and-sort-example"></a>Exemplo de igualdade e classificação

O código a seguir demonstra uma implementação de [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1) e [IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1) em um objeto de negócios simples. Além disso, quando o objeto é armazenado em uma lista e classificado, você verá que chamar o método `Sort()` resulta no uso do comparador padrão para o tipo “Part”, e o método `Sort(Comparison<T>)` é implementado usando um método anônimo.

C#

```csharp
using System;
using System.Collections.Generic;
// Simple business object. A PartId is used to identify the type of part 
// but the part name can change. 
public class Part : IEquatable<Part> , IComparable<Part>
{
    public string PartName { get; set; }

    public int PartId { get; set; }

    public override string ToString()
    {
        return "ID: " + PartId + "   Name: " + PartName;
    }
    public override bool Equals(object obj)
    {
        if (obj == null) return false;
        Part objAsPart = obj as Part;
        if (objAsPart == null) return false;
        else return Equals(objAsPart);
    }
    public int SortByNameAscending(string name1, string name2)
    {

        return name1.CompareTo(name2);
    }

    // Default comparer for Part type.
    public int CompareTo(Part comparePart)
    {
          // A null value means that this object is greater.
        if (comparePart == null)
            return 1;

        else
            return this.PartId.CompareTo(comparePart.PartId);
    }
    public override int GetHashCode()
    {
        return PartId;
    }
    public bool Equals(Part other)
    {
        if (other == null) return false;
        return (this.PartId.Equals(other.PartId));
    }
    // Should also override == and != operators.

}
public class Example
{
    public static void Main()
    {
        // Create a list of parts.
        List<Part> parts = new List<Part>();

        // Add parts to the list.
        parts.Add(new Part() { PartName = "regular seat", PartId = 1434 });
        parts.Add(new Part() { PartName= "crank arm", PartId = 1234 });
        parts.Add(new Part() { PartName = "shift lever", PartId = 1634 }); ;
        // Name intentionally left null.
        parts.Add(new Part() {  PartId = 1334 });
        parts.Add(new Part() { PartName = "banana seat", PartId = 1444 });
        parts.Add(new Part() { PartName = "cassette", PartId = 1534 });


        // Write out the parts in the list. This will call the overridden 
        // ToString method in the Part class.
        Console.WriteLine("\nBefore sort:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }


        // Call Sort on the list. This will use the 
        // default comparer, which is the Compare method 
        // implemented on Part.
        parts.Sort();


        Console.WriteLine("\nAfter sort by part number:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        // This shows calling the Sort(Comparison(T) overload using 
        // an anonymous method for the Comparison delegate. 
        // This method treats null as the lesser of two values.
        parts.Sort(delegate(Part x, Part y)
        {
            if (x.PartName == null && y.PartName == null) return 0;
            else if (x.PartName == null) return -1;
            else if (y.PartName == null) return 1;
            else return x.PartName.CompareTo(y.PartName);
        });

        Console.WriteLine("\nAfter sort by name:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        /*

            Before sort:
        ID: 1434   Name: regular seat
        ID: 1234   Name: crank arm
        ID: 1634   Name: shift lever
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette

        After sort by part number:
        ID: 1234   Name: crank arm
        ID: 1334   Name:
        ID: 1434   Name: regular seat
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1634   Name: shift lever

        After sort by name:
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1234   Name: crank arm
        ID: 1434   Name: regular seat
        ID: 1634   Name: shift lever

         */

    }
}
```

## <a name="see-also"></a>Consulte também

[IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer)

[IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1)

[IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1)

[IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable)

[IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1)

