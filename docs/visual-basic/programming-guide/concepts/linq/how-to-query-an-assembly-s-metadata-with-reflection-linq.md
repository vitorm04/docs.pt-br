---
title: 'Como: consultar um Assembly&#39;metadados com reflexão (LINQ) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: f465cccef2009bb9d8da1dc57c14eb09dc008f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643218"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>Como: consultar um Assembly&#39;metadados com reflexão (LINQ) (Visual Basic)
O exemplo a seguir mostra como o LINQ pode ser usado com a reflexão para recuperar metadados específicos sobre os métodos que correspondem a um critério de pesquisa especificado. Nesse caso, a consulta localizará os nomes de todos os métodos no assembly que retornam tipos enumeráveis como matrizes.  
  
## <a name="example"></a>Exemplo  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
Module Module1  
  
    Sub Main()  
        Dim asmbly As Assembly =   
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()   
                            Where type.IsPublic   
                            From method In type.GetMethods()   
                            Where method.ReturnType.IsArray = True   
                            Let name = method.ToString()   
                            Let typeName = type.ToString()   
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 O exemplo usa o método <xref:System.Reflection.Assembly.GetTypes%2A> para retornar uma matriz de tipos no assembly especificado. O [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md) filtro é aplicado para que somente os tipos públicos são retornados. Para cada tipo de público, uma subconsulta é gerada usando a matriz <xref:System.Reflection.MethodInfo> que é retornada da chamada <xref:System.Type.GetMethods%2A>. Esses resultados são filtrados para retornar apenas os métodos cujo tipo de retorno é uma matriz ou um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>. Por fim, esses resultados são agrupados usando o nome do tipo como uma chave.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Crie um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior com uma referência a System.Core.dll e uma instrução `Imports` para o namespace System.Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
