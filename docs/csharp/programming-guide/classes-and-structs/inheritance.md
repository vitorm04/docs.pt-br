---
title: "Herança (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract methods [C#]
- abstract classes [C#]
- inheritance [C#]
- derived classes [C#]
- virtual methods [C#]
- C# language, inheritance
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
caps.latest.revision: "38"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc3d448d311fe0a67839757fa43a209d92141214
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="inheritance-c-programming-guide"></a>Herança (Guia de Programação em C#)

A herança, assim como o encapsulamento e o polimorfismo, é uma das três principais características da programação orientada ao objeto. A herança permite que você crie novas classes que reutilizam, estendem e modificam o comportamento definido em outras classes. A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*. Uma classe derivada pode ter apenas uma classe base direta. No entanto, a herança é transitiva. Se ClassC for derivada de ClassB e ClassB for derivada de ClassA, ClassC herdará os membros declarados em ClassA e ClassB.  
  
> [!NOTE]
>  Structs não dão suporte a herança, mas podem implementar interfaces. Para obter mais informações, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
 Conceitualmente, uma classe derivada é uma especialização da classe base. Por exemplo, se tiver uma classe base `Animal`, você pode ter uma classe derivada chamada `Mammal` e outra classe derivada chamada `Reptile`. Um `Mammal` é um `Animal` e um `Reptile` é um `Animal`, mas cada classe derivada representa especializações diferentes da classe base.  
  
 Quando você define uma classe para derivar de outra classe, a classe derivada obtém implicitamente todos os membros da classe base, exceto por seus construtores e finalizadores. A classe derivada pode, assim, reutilizar o código na classe base sem precisar implementá-lo novamente. Na classe derivada, você pode adicionar mais membros. Dessa forma, a classe derivada estende a funcionalidade da classe base.  
  
 A ilustração a seguir mostra uma classe `WorkItem` que representa um item de trabalho em um processo comercial. Como todas as classes, ela deriva de <xref:System.Object?displayProperty=nameWithType> e herda todos os seus métodos. `WorkItem` adiciona cinco membros próprios. Eles incluem um construtor, porque os construtores não são herdados. A classe `ChangeRequest` herda de `WorkItem` e representa um tipo específico de item de trabalho. `ChangeRequest` adiciona mais dois membros aos membros que herda de `WorkItem` e de <xref:System.Object>. Ele deve adicionar seu próprio construtor e também adiciona `originalItemID`. A propriedade `originalItemID` permite que a instância `ChangeRequest` seja associada ao `WorkItem` original a que a solicitação de alteração se aplica.  
  
 ![Herança de classe](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class_Inheritance")  
Herança de classe  
  
 O exemplo a seguir mostra como as relações entre as classes demonstradas na ilustração anterior são expressos em C#. O exemplo também mostra como `WorkItem` substitui o método virtual <xref:System.Object.ToString%2A?displayProperty=nameWithType> e como a classe `ChangeRequest` herda a implementação de `WorkItem` do método.  
  
 [!code-csharp[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## <a name="abstract-and-virtual-methods"></a>Métodos abstratos e virtuais  
 Quando uma classe base declara um método como [virtual](../../../csharp/language-reference/keywords/virtual.md), uma classe derivada pode [substituir](../../../csharp/language-reference/keywords/override.md) o método por sua própria implementação. Se uma classe base declarar um membro como [abstrato](../../../csharp/language-reference/keywords/abstract.md), esse método deve ser substituído em qualquer classe não abstrata que herdar diretamente da classe. Se uma classe derivada for abstrato, ele herdará membros abstratos sem implementá-los. Membros abstratos e virtuais são a base do polimorfismo, que é a segunda característica principal da programação orientada a objetos. Para obter mais informações, consulte [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## <a name="abstract-base-classes"></a>Classes base abstratas  
 Você pode declarar uma classe como [abstrata](../../../csharp/language-reference/keywords/abstract.md) se quiser impedir a instanciação direta usando a palavra-chave [new](../../../csharp/language-reference/keywords/new.md). Se você fizer isso, a classe poderá ser usada somente se uma nova classe for derivada dela. Uma classe abstrata pode conter uma ou mais assinaturas de método que também são declaradas como abstratas. Essas assinaturas especificam os parâmetros e o valor retornado, mas não têm nenhuma implementação (corpo do método). Uma classe abstrata não precisa conter membros abstratos. No entanto, se uma classe contiver um membro abstrato, a própria classe deverá ser declarada como abstrata. Classes derivadas que não são abstratas devem fornecer a implementação para qualquer método abstrato de uma classe base abstrata. Para obter mais informações, consulte [Classes e Membros de Classes Abstratos e Lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="interfaces"></a>Interfaces  
 Uma *interface* é um tipo de referência semelhante a uma classe base abstrata que consiste somente em membros abstratos. Quando uma classe implementa uma interface, ela deve fornecer uma implementação para todos os membros da interface. Uma classe pode implementar várias interfaces, mesmo que ela possa derivar de apenas uma classe base direta.  
  
 Interfaces são usadas para definir recursos específicos para classes que não têm necessariamente uma relação do tipo “é um". Por exemplo, a interface <xref:System.IEquatable%601?displayProperty=nameWithType> pode ser implementada por qualquer classe ou struct que precise habilitar o código do cliente para determinar se dois objetos do tipo são equivalentes (como quer que o tipo defina a equivalência). <xref:System.IEquatable%601> não implica o mesmo tipo de relação "é um" existente entre uma classe base e uma classe derivada (por exemplo, um `Mammal` é um `Animal`). Para obter mais informações, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
## <a name="preventing-further-derivation"></a>Impedindo derivações adicionais  
 Uma classe pode impedir que outras classes herdem dela ou de qualquer um de seus membros, declarando a si mesmo ou o membro como [lacrado](../../../csharp/language-reference/keywords/sealed.md). Para obter mais informações, consulte [Classes e Membros de Classes Abstratos e Lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="derived-class-hiding-of-base-class-members"></a>Ocultação de membros da classe base pela classe derivada  
 Uma classe derivada pode ocultar membros da classe base declarando membros com mesmo nome e assinatura. O modificador [new](../../../csharp/language-reference/keywords/new.md) pode ser usado para indicar explicitamente que o membro não pretende ser uma substituição do membro base. O uso de [new](../../../csharp/language-reference/keywords/new.md) não é obrigatório, mas um aviso do compilador será gerado se [new](../../../csharp/language-reference/keywords/new.md) não for usado. Para obter mais informações, consulte [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)
