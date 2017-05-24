---
title: Como consultar caracteres em uma cadeia de caracteres (LINQ) (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 86c763d8f31a7021605d82ecab0664a290934e07
ms.contentlocale: pt-br
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Como consultar caracteres em uma cadeia de caracteres (LINQ) (C#)
Como a classe <xref:System.String> implementa a interface <xref:System.Collections.Generic.IEnumerable%601>, qualquer cadeia de caracteres pode ser consultada como uma sequência de caracteres. No entanto, esse não é um uso comum da LINQ. Para operações de correspondência de padrões complexos, use a classe <xref:System.Text.RegularExpressions.Regex>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir consulta uma cadeia de caracteres para determinar quantos dígitos numéricos ela contém. Observe que a consulta é "reutilizada" depois que é executada pela primeira vez. Isso é possível porque a consulta em si não armazena nenhum resultado real.  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior, com uma referência a System.Core.dll e diretivas `using` para os namespaces System.Linq e System.IO.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ e cadeias de caracteres (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)   
 [Como combinar consultas LINQ com expressões regulares (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
