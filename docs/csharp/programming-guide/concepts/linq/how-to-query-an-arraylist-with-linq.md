---
title: Como consultar uma ArrayList com LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
ms.openlocfilehash: b8edb90d33c92324d4f76c7e6977641fe4499d9d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345700"
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="d71fc-102">Como consultar uma ArrayList com LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="d71fc-102">How to query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="d71fc-103">Ao usar a LINQ para consultar coleções <xref:System.Collections.IEnumerable> não genéricas como <xref:System.Collections.ArrayList>, você deve declarar explicitamente o tipo da variável de intervalo para refletir o tipo específico dos objetos na coleção.</span><span class="sxs-lookup"><span data-stu-id="d71fc-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="d71fc-104">Por exemplo, se você tiver um <xref:System.Collections.ArrayList> de objetos `Student`, sua [cláusula from](../../../language-reference/keywords/from-clause.md) deverá ter uma aparência semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="d71fc-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```csharp
var query = from Student s in arrList  
//...
```  
  
 <span data-ttu-id="d71fc-105">Especificando o tipo da variável de intervalo, você está convertendo cada item na <xref:System.Collections.ArrayList> em um `Student`.</span><span class="sxs-lookup"><span data-stu-id="d71fc-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="d71fc-106">O uso de uma variável de intervalo de tipo explícito em uma expressão de consulta é equivalente a chamar o método <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="d71fc-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="d71fc-107"><xref:System.Linq.Enumerable.Cast%2A> lança uma exceção se a conversão especificada não puder ser realizada.</span><span class="sxs-lookup"><span data-stu-id="d71fc-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="d71fc-108"><xref:System.Linq.Enumerable.Cast%2A> e <xref:System.Linq.Enumerable.OfType%2A> são os dois métodos de operador de consulta padrão que operam em tipos <xref:System.Collections.IEnumerable> não genéricos.</span><span class="sxs-lookup"><span data-stu-id="d71fc-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="d71fc-109">Para obter mais informações, consulte [Relacionamentos de tipo em operações de consulta LINQ](./type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d71fc-109">For more information, see [Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d71fc-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d71fc-110">Example</span></span>  
 <span data-ttu-id="d71fc-111">O exemplo a seguir mostra uma consulta simples sobre um <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="d71fc-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="d71fc-112">Observe que este exemplo usa os inicializadores de objeto quando o código chama o método <xref:System.Collections.ArrayList.Add%2A>, mas isso não é um requisito.</span><span class="sxs-lookup"><span data-stu-id="d71fc-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:   
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="d71fc-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="d71fc-113">See also</span></span>

- [<span data-ttu-id="d71fc-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="d71fc-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
