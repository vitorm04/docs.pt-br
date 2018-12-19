---
title: Construtores estáticos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: fabcbb084a74334a7a1bcddb9a04cc6705caeb29
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234923"
---
# <a name="static-constructors-c-programming-guide"></a>Construtores estáticos (Guia de Programação em C#)
Um construtor estático é usado para inicializar quaisquer dados [estáticos](../../../csharp/language-reference/keywords/static.md) ou para executar uma ação específica que precisa ser executada apenas uma vez. Ele é chamado automaticamente antes que a primeira instância seja criada ou que quaisquer membros estáticos sejam referenciados.  
  
 [!code-csharp[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
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
  
 [!code-csharp[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
- [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)
