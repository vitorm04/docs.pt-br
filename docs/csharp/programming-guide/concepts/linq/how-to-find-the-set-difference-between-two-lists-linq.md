---
title: Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)
description: Saiba como usar o LINQ em C# para comparar duas listas de cadeias de caracteres e produzir as linhas que estão em uma lista, mas não no outro.
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 24509488d91f9861ee9bf84277238bea7031e5f6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105088"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="8f9e2-103">Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8f9e2-103">How to find the set difference between two lists (LINQ) (C#)</span></span>
<span data-ttu-id="8f9e2-104">Este exemplo mostra como usar o LINQ para comparar duas listas de cadeias de caracteres e retornar as linhas que estão no names1.txt, mas não no names2.txt.</span><span class="sxs-lookup"><span data-stu-id="8f9e2-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="8f9e2-105">Para criar os arquivos de dados</span><span class="sxs-lookup"><span data-stu-id="8f9e2-105">To create the data files</span></span>  
  
1. <span data-ttu-id="8f9e2-106">Copie names1.txt e names2.txt para a pasta da solução, conforme mostrado em [como combinar e comparar as coleções de cadeias de caracteres (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="8f9e2-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f9e2-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8f9e2-107">Example</span></span>  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 <span data-ttu-id="8f9e2-108">Alguns tipos de operações de consulta em C#, tais como <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A> e <xref:System.Linq.Enumerable.Concat%2A>, só podem ser expressas em sintaxe baseada em método.</span><span class="sxs-lookup"><span data-stu-id="8f9e2-108">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f9e2-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8f9e2-109">Compiling the Code</span></span>  
 <span data-ttu-id="8f9e2-110">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="8f9e2-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9e2-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f9e2-111">See also</span></span>

- [<span data-ttu-id="8f9e2-112">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="8f9e2-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
