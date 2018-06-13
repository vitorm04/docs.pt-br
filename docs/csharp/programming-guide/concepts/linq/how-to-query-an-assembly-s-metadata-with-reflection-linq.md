---
title: Como consultar metadados de um assembly com reflexão (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: c4cdce49-b1c8-4420-b12a-9ff7e6671368
ms.openlocfilehash: ada4fdb8ea0a552b9b6a27d7f0dfd9da447e612e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319492"
---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-c"></a>Como consultar metadados de um assembly com reflexão (LINQ) (C#)
O exemplo a seguir mostra como o LINQ pode ser usado com a reflexão para recuperar metadados específicos sobre os métodos que correspondem a um critério de pesquisa especificado. Nesse caso, a consulta localizará os nomes de todos os métodos no assembly que retornam tipos enumeráveis como matrizes.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
using System.Reflection;  
using System.IO;  
namespace LINQReflection  
{  
    class ReflectionHowTO  
    {  
        static void Main(string[] args)  
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
  
            Console.WriteLine("Press any key to exit");  
            Console.ReadKey();  
        }  
    }    
}  
```  
  
 O exemplo usa o método <xref:System.Reflection.Assembly.GetTypes%2A> para retornar uma matriz de tipos no assembly especificado. O filtro [where](../../../../csharp/language-reference/keywords/where-clause.md) é aplicado para que apenas tipos públicos sejam retornados. Para cada tipo de público, uma subconsulta é gerada usando a matriz <xref:System.Reflection.MethodInfo> que é retornada da chamada <xref:System.Type.GetMethods%2A>. Esses resultados são filtrados para retornar apenas os métodos cujo tipo de retorno é uma matriz ou um tipo que implementa <xref:System.Collections.Generic.IEnumerable%601>. Por fim, esses resultados são agrupados usando o nome do tipo como uma chave.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um projeto que tenha como alvo o .NET Framework versão 3.5 ou posterior, com uma referência ao System.Core.dll e diretivas `using` para os namespaces System.Linq e System.IO.  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
