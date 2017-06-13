---
title: "Como implementar e chamar um método de extensão personalizado (Guia de programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: 15
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: bcebdd1a6462e651619776549754eacfac9f9573
ms.contentlocale: pt-br
ms.lasthandoff: 06/12/2017

---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Como implementar e chamar um método de extensão personalizado (Guia de Programação em C#)
Este tópico mostra como implementar seus próprios métodos de extensão para qualquer tipo na [biblioteca de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=217856) ou qualquer outro tipo .NET que você desejar estender. O código de cliente pode usar seus métodos de extensão, adicionando uma referência à DLL que os contém e adicionando uma diretiva [using](../../../csharp/language-reference/keywords/using-directive.md) que especifica o namespace no qual os métodos de extensão são definidos.  
  
## <a name="to-define-and-call-the-extension-method"></a>Para definir e chamar o método de extensão  
  
1.  Defina uma [classe](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) estática para conter o método de extensão.  
  
     A classe deve estar visível para o código de cliente. Para obter mais informações sobre regras de acessibilidade, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  Implemente o método de extensão como um método estático com, pelo menos, a mesma visibilidade da classe que a contém.  
  
3.  O primeiro parâmetro do método especifica o tipo no qual o método opera. Ele deve ser precedido pelo modificador [this](../../../csharp/language-reference/keywords/this.md).  
  
4.  No código de chamada, adicione uma diretiva `using` para especificar o [namespace](../../../csharp/language-reference/keywords/namespace.md) que contém a classe do método de extensão.  
  
5.  Chame os métodos como se fossem métodos de instância no tipo.  
  
     Observe que o primeiro parâmetro não é especificado pelo código de chamada porque ele representa o tipo no qual o operador está sendo aplicado e o compilador já conhece o tipo do objeto. Você só precisa fornecer argumentos para os parâmetros de 2 até o `n`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir implementa um método de extensão chamado `WordCount` na classe `CustomExtensions.StringExtension`. O método opera o <xref:System.String> classe, que é especificado como o primeiro parâmetro do método. O namespace `CustomExtensions` é importado para o namespace do aplicativo e o método é chamado dentro do método `Main`.  
  
 [!code-cs[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Para executar esse código, copie e cole-o em um console de projeto de aplicativo do Visual C# que foi criado no [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Por padrão, esse projeto é direcionado para a versão 3.5 do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e ele tem uma referência ao System.Core.dll e uma diretriz `using` para System.Linq. Se um ou mais desses requisitos estiverem ausentes no projeto, você poderá adicioná-los manualmente.   
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Os métodos de extensão não apresentam nenhuma vulnerabilidade de segurança específica. Eles nunca podem ser usados para representar os métodos existentes em um tipo, porque todos os conflitos de nome são resolvidos em favor da instância ou do método estático, definidos pelo próprio tipo. Os métodos de extensão não podem acessar nenhum dado particular na classe estendida.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Métodos de Extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [LINQ (Consulta Integrada à Linguagem)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [this](../../../csharp/language-reference/keywords/this.md)   
 [namespace](../../../csharp/language-reference/keywords/namespace.md)
