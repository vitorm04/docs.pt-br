---
title: Interfaces – Guia de Programação em C#
ms.date: 02/20/2020
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
ms.openlocfilehash: f4ee269f41e79562c113a7627816f797b083095e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79157072"
---
# <a name="interfaces-c-programming-guide"></a>Interfaces (Guia de Programação em C#)

Uma interface contém definições para um grupo de funcionalidades relacionadas que uma [classe](../../language-reference/keywords/class.md) não abstrata ou uma [estrutura](../../language-reference/builtin-types/struct.md) deve implementar. Uma interface `static` pode definir métodos, que devem ter uma implementação. Uma interface pode fornecer uma implementação padrão para qualquer ou todos os membros de instância declarados. Uma interface não pode declarar dados de instância, como campos, propriedades implementadas automaticamente ou eventos semelhantes a propriedades.

Usando interfaces, você pode, por exemplo, incluir o comportamento de várias fontes em uma classe. Essa funcionalidade é importante em C# porque a linguagem não dá suporte a várias heranças de classes. Além disso, use uma interface se você deseja simular a herança para structs, pois eles não podem herdar de outro struct ou classe.

Você define uma interface usando a palavra-chave da [interface](../../language-reference/keywords/interface.md) como o exemplo a seguir mostra.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

O nome de uma interface deve ser um [nome identificador](../inside-a-program/identifier-names.md)C# válido . Por convenção, os nomes de interface começam com uma letra maiúscula `I`.

Qualquer classe ou struct que implemente a interface <xref:System.IEquatable%601> deve conter uma definição para um método <xref:System.IEquatable%601.Equals%2A> que corresponda à assinatura que a interface especifica. Como resultado, você pode contar com uma classe que implementa `IEquatable<T>` para conter um método `Equals` com o qual uma instância da classe pode determinar se é igual a outra instância da mesma classe.

A definição de `IEquatable<T>` não fornece uma implementação para `Equals`. Uma classe ou estrutura pode implementar várias interfaces, mas uma classe só pode herdar de uma única classe.

Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

As interfaces podem conter métodos de ocorrência, propriedades, eventos, indexadores ou qualquer combinação desses quatro tipos de membros. As interfaces podem conter construtores, campos, constantes ou operadores estáticos. Para obter links para exemplos, consulte as [seções relacionadas](./index.md#BKMK_RelatedSections). Uma interface não pode conter campos de instância, construtores de instâncias ou finalizadores. Os membros da interface são públicos por padrão.

Para implementar um membro de interface, o membro correspondente da classe de implementação deve ser público, não estático e ter o mesmo nome e assinatura do membro de interface.

Quando uma classe ou estrutura implementa uma interface, a classe ou a estrutura deve fornecer uma implementação para todos os membros que a interface declara, mas não fornece uma implementação padrão para. No entanto, se uma classe base implementa uma interface, qualquer classe que é derivada da classe base herda essa implementação.

O exemplo a seguir mostra uma implementação da interface <xref:System.IEquatable%601>. A classe de implementação, `Car`, deverá fornecer uma implementação do método <xref:System.IEquatable%601.Equals%2A>.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

As propriedades e os indexadores de uma classe podem definir acessadores extras para uma propriedade ou o indexador que é definido em uma interface. Por exemplo, uma interface pode declarar uma propriedade que tem um acessador [get](../../language-reference/keywords/get.md). A classe que implementa a interface pode declarar a mesma propriedade tanto com um acessador `get` quanto com um [set](../../language-reference/keywords/set.md). No entanto, se a propriedade ou o indexador usa a implementação explícita, os acessadores devem corresponder. Para obter mais informações sobre a implementação explícita, consulte [Implementação de interface explícita](explicit-interface-implementation.md) e [Propriedades da interface](../classes-and-structs/interface-properties.md).

Interfaces podem herdar de uma ou mais interfaces. A interface derivada herda os membros de suas interfaces base. Uma classe que implemente uma interface derivada deve implementar todos os membros na interface derivada, incluindo todos os membros das interfaces base da interface derivada. Essa classe pode ser implicitamente convertida para a interface derivada ou qualquer uma de suas interfaces base. Uma classe pode incluir uma interface várias vezes por meio das classes base que ela herda ou por meio de interfaces que outras interfaces herdam. No entanto, a classe poderá fornecer uma implementação de uma interface apenas uma vez e somente se a classe declarar a interface como parte da definição de classe (`class ClassName : InterfaceName`). Se a interface é herdada porque é herdada de uma classe base que implementa a interface, a classe base fornece a implementação dos membros da interface. No entanto, a classe derivada pode reimplementar qualquer membro de interface virtual em vez de usar a implementação herdada. Quando as interfaces declaram uma implementação padrão de um método, qualquer classe que implemente essa interface herda essa implementação. As implementações definidas nas interfaces são virtuais e a classe de implementação pode substituir essa implementação.

Uma classe base também pode implementar membros de interface usando membros virtuais. Nesse caso, uma classe derivada pode alterar o comportamento da interface substituindo os membros virtuais. Para obter mais informações sobre membros virtuais, consulte [Polimorfismo](../classes-and-structs/polymorphism.md).

## <a name="interfaces-summary"></a>Resumo de interfaces

Uma interface tem as propriedades a seguir:

- Uma interface é tipicamente como uma classe base abstrata com apenas membros abstratos. Qualquer classe ou struct que implementa a interface deve implementar todos os seus membros. Opcionalmente, uma interface pode definir implementações padrão para alguns ou todos os seus membros.
- Uma interface não pode ser instanciada diretamente. Seus membros são implementados por qualquer classe ou struct que implemente a interface.
- Uma classe ou struct pode implementar várias interfaces. Uma classe pode herdar uma classe base e também implementar uma ou mais interfaces.

## <a name="BKMK_RelatedSections"></a>Seções relacionadas

- [Propriedades de interface](../classes-and-structs/interface-properties.md)  
- [Indexadores em interfaces](../indexers/indexers-in-interfaces.md)  
- [Como implementar eventos de interface](../events/how-to-implement-interface-events.md)
- [Classes e structs](../classes-and-structs/index.md)  
- [Herança](../classes-and-structs/inheritance.md)  
- [Métodos](../classes-and-structs/methods.md)  
- [Polimorfismo](../classes-and-structs/polymorphism.md)  
- [Classes e membros de classes abstratas e lacradas](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Propriedades](../classes-and-structs/properties.md)  
- [Eventos](../events/index.md)  
- [Indexadores](../indexers/index.md)  
  
## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Herança](../classes-and-structs/inheritance.md)
- [Nomes de identificadores](../inside-a-program/identifier-names.md)
