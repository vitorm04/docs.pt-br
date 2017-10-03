---
title: "Diretiva using (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1129efd8a1c4058a9648eab61f98cdcef7e9f2f7
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

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
  
 Os namespaces vêm em duas categorias: definidos pelo usuário e definidos pelo sistema. Os namespaces definidos pelo usuário são namespaces definidos em seu código. Para obter uma lista dos namespaces definidos pelo sistema, consulte [Biblioteca de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195).  
  
 Para obter exemplos de referência a métodos em outros assemblies, consulte [Criando e usando DLLs do C#](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="example-1"></a>Exemplo 1  
  
 O exemplo a seguir mostra como definir e usar um alias de `using` para um namespace:  
  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 Uma diretiva alias de using não pode ter um tipo genérico aberto no lado direito. Por exemplo, você não pode criar um alias de using para uma List\<T>, mas pode criar um para uma List\<int>.  
  
## <a name="example-2"></a>Exemplo 2  
  
 O exemplo a seguir mostra como definir uma diretiva `using` e um alias `using` para uma classe:  
  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Usando namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras-chave de namespace](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [Namespaces](../../../csharp/programming-guide/namespaces/index.md)   
 [Instrução using](../../../csharp/language-reference/keywords/using-statement.md)

