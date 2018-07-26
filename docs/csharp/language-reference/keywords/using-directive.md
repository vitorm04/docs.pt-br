---
title: Diretiva using (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960034"
---
# <a name="using-directive-c-reference"></a>Diretiva using (Referência de C#)
A diretiva `using` tem três usos:  
  
-   Para permitir o uso de tipos em um namespace para que você não precise qualificar o uso de um tipo nesse namespace:  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   Para permitir que você acesse membros estáticos de um tipo sem precisar qualificar o acesso com o nome do tipo. 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    Para obter mais informações, consulte a [diretiva using static](using-static.md).

-   Para criar um alias para um namespace ou um tipo. Isso é chamado de uma *diretiva alias de using*.  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 A palavra-chave `using` também é usada para criar *instruções using*, o que ajuda a garantir que objetos <xref:System.IDisposable>, tais como arquivos e fontes, sejam tratados corretamente. Consulte a [Instrução using](../../../csharp/language-reference/keywords/using-statement.md) para obter mais informações.  
  
## <a name="using-static-type"></a>Tipo using static  
 Você pode acessar os membros estáticos de um tipo sem precisar qualificar o acesso com o nome do tipo:  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a>Comentários  
 O escopo de uma diretiva `using` é limitado ao arquivo em que ele aparece.  
  
 Crie um alias `using` para tornar mais fácil a qualificação de um identificador para um namespace ou tipo. O lado direito de uma diretiva alias de using deve sempre ser um tipo totalmente qualificado, independentemente das diretivas using que vêm antes dele.  
  
 Crie uma diretiva `using` para usar os tipos em um namespace sem precisar especificar o namespace. Uma diretiva `using` não fornece acesso a nenhum namespace aninhado no namespace especificado.  
  
 Os namespaces vêm em duas categorias: definidos pelo usuário e definidos pelo sistema. Os namespaces definidos pelo usuário são namespaces definidos em seu código. Para obter uma lista dos namespaces definidos pelo sistema, confira [Visão geral da biblioteca de classes .NET Framework](../../../standard/class-library-overview.md).  
  
 Para obter exemplos sobre como referenciar métodos em outros assemblies, confira [Criar e usar assemblies usando a linha de comando](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="example-1"></a>Exemplo 1  
  
 O exemplo a seguir mostra como definir e usar um alias de `using` para um namespace:  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Uma diretiva alias de using não pode ter um tipo genérico aberto no lado direito. Por exemplo, você não pode criar um alias de using para uma List\<T>, mas pode criar um para uma List\<int>.  
  
## <a name="example-2"></a>Exemplo 2  
  
 O exemplo a seguir mostra como definir uma diretiva `using` e um alias `using` para uma classe:  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [Namespaces](../../../csharp/programming-guide/namespaces/index.md)  
 [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)
