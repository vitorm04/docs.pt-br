---
title: Interfaces (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: 6ef872876e800674a58b440e0e4001b86b0f8244
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337581"
---
# <a name="interfaces-c-programming-guide"></a>Interfaces (Guia de Programação em C#)
Uma interface contém definições para um grupo de funcionalidades relacionadas que uma [classe](../../../csharp/language-reference/keywords/class.md) ou um [struct](../../../csharp/language-reference/keywords/struct.md) pode implementar.  
  
 Usando interfaces, você pode, por exemplo, incluir o comportamento de várias fontes em uma classe. Essa funcionalidade é importante em C# porque a linguagem não dá suporte a várias heranças de classes. Além disso, use uma interface se você deseja simular a herança para structs, pois eles não podem herdar de outro struct ou classe.  
  
 Você define uma interface usando a palavra-chave [interface](../../../csharp/language-reference/keywords/interface.md), como mostra o exemplo a seguir.  
  
 [!code-csharp[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 Qualquer classe ou struct que implemente a interface <xref:System.IEquatable%601> deve conter uma definição para um método <xref:System.IEquatable%601.Equals%2A> que corresponda à assinatura que a interface especifica. Como resultado, você pode contar com uma classe que implementa `IEquatable<T>` para conter um método `Equals` com o qual uma instância da classe pode determinar se é igual a outra instância da mesma classe.  
  
 A definição de `IEquatable<T>` não fornece uma implementação para `Equals`. A interface define somente a assinatura. Dessa forma, uma interface em C# é semelhante a uma classe abstrata, na qual todos os métodos são abstratos. No entanto, uma classe ou struct pode implementar várias interfaces, mas uma classe pode herdar apenas uma única classe, abstrata ou não. Assim, ao usar interfaces, você pode incluir o comportamento de várias fontes em uma classe.  
  
 Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 As interfaces podem conter métodos, propriedades, eventos, indexadores ou qualquer combinação desses quatro tipos de membro. Para obter links para exemplos, consulte as [seções relacionadas](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections). Uma interface não pode conter constantes, campos, operadores, construtores de instância, finalizadores ou tipos. Os membros da interface são automaticamente públicos e eles não podem incluir nenhum modificador de acesso. Os membros também não podem ser [estáticos](../../../csharp/language-reference/keywords/static.md).  
  
 Para implementar um membro de interface, o membro correspondente da classe de implementação deve ser público, não estático e ter o mesmo nome e assinatura do membro de interface.  
  
 Quando uma classe ou struct implementa uma interface, a classe ou o struct deve fornecer uma implementação para todos os membros que a interface define. A interface não fornece nenhuma funcionalidade que uma classe ou um struct possa herdar da forma que ela pode herdar a funcionalidade da classe base. No entanto, se uma classe base implementa uma interface, qualquer classe que é derivada da classe base herda essa implementação.  
  
 O exemplo a seguir mostra uma implementação da interface IEquatable<T\>. A classe de implementação, `Car`, deverá fornecer uma implementação do método <xref:System.IEquatable%601.Equals%2A>.  
  
 [!code-csharp[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 As propriedades e os indexadores de uma classe podem definir acessadores extras para uma propriedade ou o indexador que é definido em uma interface. Por exemplo, uma interface pode declarar uma propriedade que tem um acessador [get](../../../csharp/language-reference/keywords/get.md). A classe que implementa a interface pode declarar a mesma propriedade tanto com um acessador `get` quanto com um [set](../../../csharp/language-reference/keywords/set.md). No entanto, se a propriedade ou o indexador usa a implementação explícita, os acessadores devem corresponder. Para obter mais informações sobre a implementação explícita, consulte [Implementação de interface explícita](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) e [Propriedades da interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).  
  
 As interfaces podem implementar outras interfaces. Uma classe pode incluir uma interface várias vezes por meio das classes base que ela herda ou por meio de interfaces que outras interfaces implementam. No entanto, a classe poderá fornecer uma implementação de uma interface apenas uma vez e somente se a classe declarar a interface como parte da definição de classe (`class ClassName : InterfaceName`). Se a interface é herdada porque é herdada de uma classe base que implementa a interface, a classe base fornece a implementação dos membros da interface. No entanto, a classe derivada pode reimplementar os membros de interface em vez de usar a implementação herdada.  
  
 Uma classe base também pode implementar membros de interface usando membros virtuais. Nesse caso, uma classe derivada pode alterar o comportamento da interface substituindo os membros virtuais. Para obter mais informações sobre membros virtuais, consulte [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Resumo de Interfaces  
 Uma interface tem as propriedades a seguir:  
  
-   Uma interface é como uma classe base abstrata. Qualquer classe ou struct que implementa a interface deve implementar todos os seus membros.  
  
-   Uma interface não pode ser instanciada diretamente. Seus membros são implementados por qualquer classe ou struct que implemente a interface.  
  
-   As interfaces podem conter propriedades, indexadores, métodos e eventos.  
  
-   As interfaces não têm implementações de métodos.  
  
-   Uma classe ou struct pode implementar várias interfaces. Uma classe pode herdar uma classe base e também implementar uma ou mais interfaces.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementação de interface explícita](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 Explica como criar um membro da classe que é específico para uma interface.  
  
 [Como implementar membros de interface explicitamente](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 Fornece um exemplo de como implementar explicitamente membros de interfaces.  
  
 [Como implementar membros de duas interfaces explicitamente](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 Fornece um exemplo de como implementar explicitamente membros de interfaces com herança.  
  
##  <a name="BKMK_RelatedSections"></a> Seções relacionadas  
  
-   [Propriedades de interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [Indexadores em interfaces](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [Eventos](../../../csharp/programming-guide/events/index.md)  
  
-   [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>Capítulo do Livro em Destaque  
 [Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) em [Learning C# 3.0: Master the Fundamentals of C# 3.0 (Aprendendo C# 3.0: dominando os conceitos básicos do C# 3.0)](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
