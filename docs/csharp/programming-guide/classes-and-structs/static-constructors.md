---
title: "Construtores estáticos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
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
ms.openlocfilehash: 73df76c61f393bf5fe09af66935acfbac4b5663f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="static-constructors-c-programming-guide"></a>Construtores estáticos (Guia de Programação em C#)
Um construtor estático é usado para inicializar quaisquer dados [estáticos](../../../csharp/language-reference/keywords/static.md) ou para executar uma ação específica que precisa ser executada apenas uma vez. Ele é chamado automaticamente antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 Construtores estáticos têm as seguintes propriedades:  
  
-   Um construtor estático não usa modificadores de acesso nem tem parâmetros.  
  
-   Um construtor estático é chamado automaticamente para inicializar a [classe](../../../csharp/language-reference/keywords/class.md) antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.  
  
-   Um construtor estático não pode ser chamado diretamente.  
  
-   O usuário não tem controle sobre quando o construtor estático é executado no programa.  
  
-   Um uso típico de construtores estáticos é quando a classe está usando um arquivo de log e o construtor é usado para gravar entradas nesse arquivo.  
  
-   Construtores estáticos também são úteis ao criar classes wrapper para código não gerenciado quando o construtor pode chamar o método `LoadLibrary`.  
  
-   Se um construtor estático gera uma exceção, o tempo de execução não o invocará uma segunda vez e o tipo permanecerá não inicializado durante o tempo de vida do domínio do aplicativo no qual o programa está sendo executado.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a classe `Bus` tem um construtor estático. Quando a primeira instância do `Bus` for criada (`bus1`), o construtor estático será invocado para inicializar a classe. O exemplo de saída verifica se o construtor estático é executado somente uma vez, mesmo se duas instâncias de `Bus` forem criadas e se é executado antes que o construtor da instância seja executado.  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Classes estáticas e membros de classes estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)

