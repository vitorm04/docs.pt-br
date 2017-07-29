---
title: "Objetos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
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
ms.openlocfilehash: a2a23d02e4ea95e908f97bc7264ee64d6899aee8
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="objects-c-programming-guide"></a>Objetos (Guia de Programação em C#)
Uma definição de classe ou struct é como um esquema que especifica o que o tipo pode fazer. Um objeto é basicamente um bloco de memória que foi alocado e configurado de acordo com o esquema. Um programa pode criar vários objetos da mesma classe. Objetos também são chamados de instâncias e podem ser armazenados em uma variável nomeada ou em uma matriz ou coleção. O código de cliente é o código que usa essas variáveis para chamar os métodos e acessar as propriedades públicas do objeto. Em uma linguagem orientada a objetos, como o C#, um programa típico consiste em vários objetos que interagem dinamicamente.  
  
> [!NOTE]
>  Tipos estáticos se comportam de modo diferente do que está descrito aqui. Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="struct-instances-vs-class-instances"></a>Instâncias de struct versus Instâncias de Classe  
 Como as classes são tipos de referência, uma variável de um objeto de classe contém uma referência ao endereço do objeto no heap gerenciado. Se um segundo objeto do mesmo tipo for atribuído ao primeiro objeto, as duas variáveis farão referência ao objeto nesse endereço. Esse ponto é abordado com mais detalhes posteriormente neste tópico.  
  
 Instâncias de classes são criadas usando o [operador new](../../../csharp/language-reference/keywords/new-operator.md). No exemplo a seguir, `Person` é o tipo e `person1` e `person 2` são instâncias ou objetos desse tipo.  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 Como structs são tipos de valor, uma variável de um objeto de struct mantém uma cópia do objeto inteiro. Instâncias de structs também podem ser criadas usando o operador `new`, mas isso não é obrigatório, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 A memória de `p1` e `p2` é alocada na pilha de thread. Essa memória é recuperada em conjunto com o tipo ou método em que ela é declarada. Esse é um dos motivos pelos quais os structs são copiados na atribuição. Por outro lado, a memória alocada a uma instância de classe é recuperada automaticamente (o lixo é coletado) pelo Common Language Runtime quando todas as referências ao objeto tiveram saído do escopo. Não é possível destruir de forma determinista um objeto de classe, como é possível no C++. Para obter mais informações sobre a coleta de lixo no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
>  A alocação e a desalocação de memória no heap gerenciado é altamente otimizada no Common Language Runtime. Na maioria dos casos, não há uma diferença significativa quanto ao custo do desempenho de alocar uma instância da classe no heap em vez de alocar uma instância de struct na pilha.  
  
## <a name="object-identity-vs-value-equality"></a>Identidade de objeto versus Igualdade de Valor  
 Quando compara dois objetos quanto à igualdade, primeiro você precisa distinguir se quer saber se as duas variáveis representam o mesmo objeto na memória ou se os valores de um ou mais de seus campos são equivalentes. Se estiver pretendendo comparar valores, você precisa considerar se os objetos são instâncias de tipos de valor (structs) ou tipos de referência (classes, delegados, matrizes).  
  
-   Para determinar se duas instâncias de classe se referem ao mesmo local na memória (o que significa que elas têm a mesma *identidade*), use o método <xref:System.Object.Equals%2A> estático. (<xref:System.Object?displayProperty=fullName> é a classe base implícita para todos os tipos de valor e tipos de referência, incluindo classes e structs definidos pelo usuário.)  
  
-   Para determinar se os campos de instância em duas instâncias de struct têm os mesmos valores, use o método <xref:System.ValueType.Equals%2A?displayProperty=fullName>. Como todos os structs herdam implicitamente de <xref:System.ValueType?displayProperty=fullName>, você chama o método diretamente em seu objeto, conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 A implementação de <xref:System.ValueType?displayProperty=fullName> de `Equals` usa reflexão porque ela precisa ser capaz de determinar quais são os campos em qualquer struct. Ao criar seus próprios structs, substitua o método `Equals` para fornecer um algoritmo de igualdade eficiente que é específico ao seu tipo.  
  
-   Para determinar se os valores dos campos em duas instâncias de classe são iguais, você pode usar o método <xref:System.Object.Equals%2A> ou o [Operador ==](../../../csharp/language-reference/operators/equality-comparison-operator.md). No entanto, use-os apenas se a classe os tiver substituído ou sobrecarregado para fornecer uma definição personalizada do que "igualdade" significa para objetos desse tipo. A classe também pode implementar a interface <xref:System.IEquatable%601> ou a interface <xref:System.Collections.Generic.IEqualityComparer%601>. As duas interfaces fornecem métodos que podem ser usados para testar a igualdade de valores. Ao criar suas próprias classes que substituem `Equals`, certifique-se de seguir as diretrizes informadas em [Como definir a igualdade de valor para um tipo](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) e <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
-   [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [class](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [Operador new](../../../csharp/language-reference/keywords/new-operator.md)   
 [Common Type System](../../../standard/base-types/common-type-system.md)

