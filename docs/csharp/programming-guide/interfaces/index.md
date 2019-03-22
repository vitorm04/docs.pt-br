---
title: 'Interfaces – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
  - 'interfaces [C#]'
  - 'C# language, interfaces'
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
---
# <a name="interfaces-c-programming-guide"></a>Interfaces (Guia de Programação em C#)

Uma interface contém definições para um grupo de funcionalidades relacionadas que uma [classe](../../language-reference/keywords/class.md) ou um [struct](../../language-reference/keywords/struct.md) pode implementar.
  
Usando interfaces, você pode, por exemplo, incluir o comportamento de várias fontes em uma classe. Essa funcionalidade é importante em C# porque a linguagem não dá suporte a várias heranças de classes. Além disso, use uma interface se você deseja simular a herança para structs, pois eles não podem herdar de outro struct ou classe.  
  
Você define uma interface usando a palavra-chave [interface](../../language-reference/keywords/interface.md). como mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideInheritance#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#47)]  

O nome da struct deve ser um [nome do identificador](../inside-a-program/identifier-names.md) válido em C#. Por convenção, os nomes de interface começam com uma letra maiúscula `I`.

Qualquer classe ou struct que implemente a interface <xref:System.IEquatable%601> deve conter uma definição para um método <xref:System.IEquatable%601.Equals%2A> que corresponda à assinatura que a interface especifica. Como resultado, você pode contar com uma classe que implementa `IEquatable<T>` para conter um método `Equals` com o qual uma instância da classe pode determinar se é igual a outra instância da mesma classe.  
  
A definição de `IEquatable<T>` não fornece uma implementação para `Equals`. A interface define somente a assinatura. Dessa forma, uma interface em C# é semelhante a uma classe abstrata, na qual todos os métodos são abstratos. No entanto, uma classe ou struct pode implementar várias interfaces, mas uma classe pode herdar apenas uma única classe, abstrata ou não.
  
Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
As interfaces podem conter métodos, propriedades, eventos, indexadores ou qualquer combinação desses quatro tipos de membro. Para obter links para exemplos, consulte as [seções relacionadas](../interfaces/index.md#BKMK_RelatedSections). Uma interface não pode conter constantes, campos, operadores, construtores de instância, finalizadores ou tipos. Os membros da interface são automaticamente públicos e eles não podem incluir nenhum modificador de acesso. Os membros também não podem ser [estáticos](../../language-reference/keywords/static.md).  
  
Para implementar um membro de interface, o membro correspondente da classe de implementação deve ser público, não estático e ter o mesmo nome e assinatura do membro de interface.  
  
Quando uma classe ou struct implementa uma interface, a classe ou o struct deve fornecer uma implementação para todos os membros que a interface define. A interface não fornece nenhuma funcionalidade que uma classe ou um struct possa herdar da forma que ela pode herdar a funcionalidade da classe base. No entanto, se uma classe base implementa uma interface, qualquer classe que é derivada da classe base herda essa implementação.  
  
O exemplo a seguir mostra uma implementação da interface <xref:System.IEquatable%601>. A classe de implementação, `Car`, deverá fornecer uma implementação do método <xref:System.IEquatable%601.Equals%2A>.  
  
 [!code-csharp[csProgGuideInheritance#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#48)]  
  
As propriedades e os indexadores de uma classe podem definir acessadores extras para uma propriedade ou o indexador que é definido em uma interface. Por exemplo, uma interface pode declarar uma propriedade que tem um acessador [get](../../language-reference/keywords/get.md). A classe que implementa a interface pode declarar a mesma propriedade tanto com um acessador `get` quanto com um [set](../../language-reference/keywords/set.md). No entanto, se a propriedade ou o indexador usa a implementação explícita, os acessadores devem corresponder. Para obter mais informações sobre a implementação explícita, consulte [Implementação de interface explícita](explicit-interface-implementation.md) e [Propriedades da interface](../classes-and-structs/interface-properties.md).  

As interfaces podem herdar de outras interfaces. Uma classe pode incluir uma interface várias vezes por meio das classes base que ela herda ou por meio de interfaces que outras interfaces herdam. No entanto, a classe poderá fornecer uma implementação de uma interface apenas uma vez e somente se a classe declarar a interface como parte da definição de classe (`class ClassName : InterfaceName`). Se a interface é herdada porque é herdada de uma classe base que implementa a interface, a classe base fornece a implementação dos membros da interface. No entanto, a classe derivada pode reimplementar qualquer membro de interface virtual em vez de usar a implementação herdada.  
  
Uma classe base também pode implementar membros de interface usando membros virtuais. Nesse caso, uma classe derivada pode alterar o comportamento da interface substituindo os membros virtuais. Para obter mais informações sobre membros virtuais, consulte [Polimorfismo](../classes-and-structs/polymorphism.md).  
  
## <a name="interfaces-summary"></a>Resumo de interfaces

Uma interface tem as propriedades a seguir:  

- Uma interface é como uma classe base abstrata que contém apenas membros abstratos. Qualquer classe ou struct que implementa a interface deve implementar todos os seus membros.
- Uma interface não pode ser instanciada diretamente. Seus membros são implementados por qualquer classe ou struct que implemente a interface.
- As interfaces podem conter propriedades, indexadores, métodos e eventos.
- As interfaces não têm implementações de métodos.
- Uma classe ou struct pode implementar várias interfaces. Uma classe pode herdar uma classe base e também implementar uma ou mais interfaces.

## <a name="in-this-section"></a>Nesta seção

[Implementação de interface explícita](explicit-interface-implementation.md)  
 Explica como criar um membro da classe que é específico para uma interface.  
  
 [Como: implementar membros de interface de forma explícita](how-to-explicitly-implement-interface-members.md)  
 Fornece um exemplo de como implementar explicitamente membros de interfaces.  
  
 [Como: implementar membros de duas interfaces de forma explícita](how-to-explicitly-implement-members-of-two-interfaces.md)  
 Fornece um exemplo de como implementar explicitamente membros de interfaces com herança.  
  
## <a name="BKMK_RelatedSections"></a> Seções relacionadas

- [Propriedades de interface](../classes-and-structs/interface-properties.md)  
- [Indexadores em interfaces](../indexers/indexers-in-interfaces.md)  
- [Como:  implementar eventos de interface](../events/how-to-implement-interface-events.md)  
- [Classes e Structs](../classes-and-structs/index.md)  
- [Herança](../classes-and-structs/inheritance.md)  
- [Métodos](../classes-and-structs/methods.md)  
- [Polimorfismo](../classes-and-structs/polymorphism.md)  
- [Classes e membros de classes abstract e sealed](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Propriedades](../classes-and-structs/properties.md)  
- [Eventos](../events/index.md)  
- [Indexadores](../indexers/index.md)  
  
## <a name="featured-book-chapter"></a>capítulo do livro em destaque

[Interfaces](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652489%28v%3Dorm.10%29) em [Aprendizado de C# 3.0: domine os princípios básicos de C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v%253dorm.10%29)

## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Herança](../classes-and-structs/inheritance.md)
- [Nomes de identificadores](../inside-a-program/identifier-names.md)
