---
title: Como consultar metadados de um assembly com reflexão (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: 092cb386af0c3f2e2241c2c2ac8e50eab74cc43b
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241533"
---
# <a name="how-to-query-an-assemblys-metadata-with-reflection-linq-c"></a>Como consultar metadados de um assembly com reflexão (LINQ) (C#)

As APIs de reflexão do .NET podem ser usadas para examinar os metadados em um assembly .NET e criar coleções de tipos, membros de tipo, parâmetros e assim por diante que estão nesse assembly. Como essas coleções dão suporte à interface <xref:System.Collections.Generic.IEnumerable%601> genéricas, elas podem ser consultadas usando LINQ.  
  
O exemplo a seguir mostra como o LINQ pode ser usado com a reflexão para recuperar metadados específicos sobre os métodos que correspondem a um critério de pesquisa especificado. Nesse caso, a consulta localizará os nomes de todos os métodos no assembly que retornam tipos enumeráveis como matrizes.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
using System;
using System.Linq;
using System.Reflection;  

class ReflectionHowTO  
{  
    static void Main()  
    {  
        Assembly assembly = Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089");  
        var pubTypesQuery = from type in assembly.GetTypes()  
                    where type.IsPublic  
                        from method in type.GetMethods()  
                        where method.ReturnType.IsArray == true
                            || ( method.ReturnType.GetInterface(  
                                typeof(System.Collections.Generic.IEnumerable<>).FullName ) != null  
                            && method.ReturnType.FullName != "System.String" )  
                        group method.ToString() by type.ToString();  

        foreach (var groupOfMethods in pubTypesQuery)  
        {  
            Console.WriteLine("Type: {0}", groupOfMethods.Key);  
            foreach (var method in groupOfMethods)  
            {  
                Console.WriteLine("  {0}", method);  
            }  
        }  

        Console.WriteLine("Press any key to exit... ");  
        Console.ReadKey();  
    }  
}
```  

O exemplo usa o método <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> para retornar uma matriz de tipos no assembly especificado. O filtro [where](../../../language-reference/keywords/where-clause.md) é aplicado para que apenas tipos públicos sejam retornados. Para cada tipo de público, uma subconsulta é gerada usando a matriz <xref:System.Reflection.MethodInfo> que é retornada da chamada <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>. Esses resultados são filtrados para retornar apenas os métodos cujo tipo de retorno é uma matriz ou um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>. Por fim, esses resultados são agrupados usando o nome do tipo como uma chave.  
  
## <a name="see-also"></a>Consulte também

- [LINQ to Objects (C#)](./linq-to-objects.md)
