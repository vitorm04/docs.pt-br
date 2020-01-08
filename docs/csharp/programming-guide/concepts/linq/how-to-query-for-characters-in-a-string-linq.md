---
title: Como consultar os caracteres em uma cadeia de caracteres (LINQ)C#()
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345676"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="6f797-102">Como consultar os caracteres em uma cadeia de caracteres (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="6f797-102">How to query for characters in a string (LINQ) (C#)</span></span>
<span data-ttu-id="6f797-103">Já que a classe <xref:System.String> implementa a interface <xref:System.Collections.Generic.IEnumerable%601> genérica, qualquer cadeia de caracteres pode ser consultada como uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6f797-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="6f797-104">No entanto, esse não é um uso comum da LINQ.</span><span class="sxs-lookup"><span data-stu-id="6f797-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="6f797-105">Para operações de correspondência de padrões complexas, use a classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="6f797-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f797-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f797-106">Example</span></span>  
 <span data-ttu-id="6f797-107">O exemplo a seguir consulta uma cadeia de caracteres para determinar quantos dígitos numéricos ela contém.</span><span class="sxs-lookup"><span data-stu-id="6f797-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="6f797-108">Observe que a consulta é "reutilizada" depois que é executada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="6f797-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="6f797-109">Isso é possível porque a consulta em si não armazena nenhum resultado real.</span><span class="sxs-lookup"><span data-stu-id="6f797-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6f797-110">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="6f797-110">Compiling the Code</span></span>  
 <span data-ttu-id="6f797-111">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="6f797-111">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f797-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="6f797-112">See also</span></span>

- [<span data-ttu-id="6f797-113">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="6f797-113">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="6f797-114">Como combinar consultas LINQ com expressões regulares (C#)</span><span class="sxs-lookup"><span data-stu-id="6f797-114">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
