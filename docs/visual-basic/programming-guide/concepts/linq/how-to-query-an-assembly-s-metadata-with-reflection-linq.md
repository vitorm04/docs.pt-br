---
title: "Como: consultar metadados de um Assembly com reflexão (LINQ) (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c1bc26d7b23135dd45ad58ea0bd2510b7157448
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>Como: consultar metadados de um Assembly com reflexão (LINQ) (Visual Basic)
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
  
 O exemplo usa o <xref:System.Reflection.Assembly.GetTypes%2A>método para retornar uma matriz de tipos no assembly especificado.</xref:System.Reflection.Assembly.GetTypes%2A> O [cláusula Where](../../../../visual-basic/language-reference/queries/where-clause.md) filtro é aplicado para que somente os tipos públicos são retornados. Para cada tipo de público, uma subconsulta é gerada usando o <xref:System.Reflection.MethodInfo>matriz que é retornado de <xref:System.Type.GetMethods%2A>chamar.</xref:System.Type.GetMethods%2A> </xref:System.Reflection.MethodInfo> Esses resultados são filtrados para retornar somente os métodos cujo tipo de retorno é uma matriz ou então um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601> Finalmente, esses resultados são agrupados usando o nome do tipo como uma chave.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tem como alvo o .NET Framework versão 3.5 ou superior com uma referência a System.Core.dll e uma `Imports` declaração para o namespace System. Linq.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
