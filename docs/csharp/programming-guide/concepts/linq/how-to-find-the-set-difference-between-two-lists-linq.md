---
title: Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 9e2a42a466a71d4e351df89398be197197a54042
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140991"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="43357-102">Como localizar a diferença de conjunto entre duas listas (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="43357-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="43357-103">Este exemplo mostra como usar o LINQ para comparar duas listas de cadeias de caracteres e retornar as linhas que estão no names1.txt, mas não no names2.txt.</span><span class="sxs-lookup"><span data-stu-id="43357-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="43357-104">Para criar os arquivos de dados</span><span class="sxs-lookup"><span data-stu-id="43357-104">To create the data files</span></span>  
  
1. <span data-ttu-id="43357-105">Copie names1. txt e names2. txt para a pasta da solução, conforme mostrado em [como combinar e comparar as coleções de cadeiasC#de caracteres (LINQ) ()](./how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="43357-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43357-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43357-106">Example</span></span>  
  
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
  
 <span data-ttu-id="43357-107">Alguns tipos de operações de consulta em C#, tais como <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A> e <xref:System.Linq.Enumerable.Concat%2A>, só podem ser expressas em sintaxe baseada em método.</span><span class="sxs-lookup"><span data-stu-id="43357-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43357-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="43357-108">Compiling the Code</span></span>  
 <span data-ttu-id="43357-109">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="43357-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43357-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43357-110">See also</span></span>

- [<span data-ttu-id="43357-111">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="43357-111">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
