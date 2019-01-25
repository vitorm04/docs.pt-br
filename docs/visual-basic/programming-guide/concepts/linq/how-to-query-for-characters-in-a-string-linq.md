---
title: 'Como: Consultar caracteres em uma cadeia de caracteres (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
ms.openlocfilehash: 3a4f3bbca313747e0b16170719b9028e5dc9174f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559743"
---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="0ee8a-102">Como: Consultar caracteres em uma cadeia de caracteres (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ee8a-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="0ee8a-103">Já que a classe <xref:System.String> implementa a interface <xref:System.Collections.Generic.IEnumerable%601> genérica, qualquer cadeia de caracteres pode ser consultada como uma sequência de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="0ee8a-104">No entanto, esse não é um uso comum da LINQ.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="0ee8a-105">Para operações de correspondência de padrões complexas, use a classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ee8a-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ee8a-106">Example</span></span>  
 <span data-ttu-id="0ee8a-107">O exemplo a seguir consulta uma cadeia de caracteres para determinar quantos dígitos numéricos ela contém.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="0ee8a-108">Observe que a consulta é "reutilizada" depois que é executada pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="0ee8a-109">Isso é possível porque a consulta em si não armazena nenhum resultado real.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-109">This is possible because the query itself does not store any actual results.</span></span>  
  
```vb  
Class QueryAString  
  
    Shared Sub Main()  
  
        ' A string is an IEnumerable data source.  
        Dim aString As String = "ABCDE99F-J74-12-89A"  
  
        ' Select only those characters that are numbers  
        Dim stringQuery = From ch In aString   
                          Where Char.IsDigit(ch)   
                          Select ch  
        ' Execute the query  
        For Each c As Char In stringQuery  
            Console.Write(c & " ")  
        Next  
  
        ' Call the Count method on the existing query.  
        Dim count As Integer = stringQuery.Count()  
        Console.WriteLine(System.Environment.NewLine & "Count = " & count)  
  
        ' Select all characters before the first '-'  
        Dim stringQuery2 = aString.TakeWhile(Function(c) c <> "-")  
  
        ' Execute the second query  
        For Each ch In stringQuery2  
            Console.Write(ch)  
        Next  
  
        Console.WriteLine(System.Environment.NewLine & "Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 9 9 7 4 1 2 8 9   
' Count = 8  
' ABCDE99F  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ee8a-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0ee8a-110">Compiling the Code</span></span>  
 <span data-ttu-id="0ee8a-111">Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior com uma referência a System.Core.dll e uma instrução `Imports` para o namespace System.Linq.</span><span class="sxs-lookup"><span data-stu-id="0ee8a-111">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee8a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ee8a-112">See also</span></span>
- [<span data-ttu-id="0ee8a-113">LINQ e cadeias de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ee8a-113">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="0ee8a-114">Como: Combinar consultas LINQ com expressões regulares (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ee8a-114">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
