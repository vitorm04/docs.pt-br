---
title: Como consultar metadados de um assembly com reflexão (LINQ)
ms.date: 07/20/2015
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
ms.openlocfilehash: 5cc525c6e60efd7cf34f9894b2cbb9389fd0b6ae
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347725"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-visual-basic"></a>How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)
O exemplo a seguir mostra como o LINQ pode ser usado com a reflexão para recuperar metadados específicos sobre os métodos que correspondem a um critério de pesquisa especificado. Nesse caso, a consulta localizará os nomes de todos os métodos no assembly que retornam tipos enumeráveis como matrizes.  
  
## <a name="example"></a>Exemplo  
  
```vb
Imports System.Linq
Imports System.Reflection  

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
        Console.WriteLine("Press any key to exit... ")  
        Console.ReadKey()  
    End Sub  
End Module  
```  
  
O exemplo usa o método <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> para retornar uma matriz de tipos no assembly especificado. The [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md) filter is applied so that only public types are returned. Para cada tipo de público, uma subconsulta é gerada usando a matriz <xref:System.Reflection.MethodInfo> que é retornada da chamada <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>. Esses resultados são filtrados para retornar apenas os métodos cujo tipo de retorno é uma matriz ou um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>. Por fim, esses resultados são agrupados usando o nome do tipo como uma chave.  
  
## <a name="see-also"></a>Consulte também

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
