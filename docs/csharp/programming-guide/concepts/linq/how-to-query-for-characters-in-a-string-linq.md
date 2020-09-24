---
title: Como consultar caracteres em uma cadeia (LINQ) (C#)
description: Você pode consultar uma cadeia de caracteres como uma sequência de personagens no LINQ. Este exemplo de C# consulta uma cadeia de caracteres para determinar o número de dígitos numéricos que ele contém.
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 73288924d057e720a744b853998a52437b9db481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153931"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a><span data-ttu-id="28187-104">Como consultar caracteres em uma cadeia (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="28187-104">How to query for characters in a string (LINQ) (C#)</span></span>

<span data-ttu-id="28187-105">Já que a classe <xref:System.String> implementa a interface <xref:System.Collections.Generic.IEnumerable%601> genérica, qualquer cadeia de caracteres pode ser consultada como uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28187-105">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="28187-106">No entanto, esse não é um uso comum da LINQ.</span><span class="sxs-lookup"><span data-stu-id="28187-106">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="28187-107">Para operações de correspondência de padrões complexas, use a classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="28187-107">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28187-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28187-108">Example</span></span>  

 <span data-ttu-id="28187-109">O exemplo a seguir consulta uma cadeia de caracteres para determinar quantos dígitos numéricos ela contém.</span><span class="sxs-lookup"><span data-stu-id="28187-109">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="28187-110">Observe que a consulta é "reutilizada" depois que é executada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="28187-110">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="28187-111">Isso é possível porque a consulta em si não armazena nenhum resultado real.</span><span class="sxs-lookup"><span data-stu-id="28187-111">This is possible because the query itself does not store any actual results.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="28187-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="28187-112">Compiling the Code</span></span>  

 <span data-ttu-id="28187-113">Criar um projeto de aplicativo de console em C# com diretivas `using` para os namespaces System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="28187-113">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28187-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="28187-114">See also</span></span>

- [<span data-ttu-id="28187-115">LINQ e cadeias de caracteres (C#)</span><span class="sxs-lookup"><span data-stu-id="28187-115">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="28187-116">Como combinar consultas LINQ com expressões regulares (C#)</span><span class="sxs-lookup"><span data-stu-id="28187-116">How to combine LINQ queries with regular expressions (C#)</span></span>](./how-to-combine-linq-queries-with-regular-expressions.md)
