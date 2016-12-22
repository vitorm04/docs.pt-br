---
title: "Heran&#231;a (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "classes abstratas [C#]"
  - "métodos abstratos [C#]"
  - "Linguagem C#, herança"
  - "classes derivadas [C#]"
  - "herança [C#]"
  - "métodos virtuais [C#]"
ms.assetid: 81d64ee4-50f9-4d6c-a8dc-257c348d2eea
caps.latest.revision: 38
caps.handback.revision: 38
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Heran&#231;a (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A herança, juntamente com o encapsulamento e polimorfismo, é uma das três principais características \(ou  *pilares*\) da programação orientada a objeto.  A herança permite que você criar novas classes para reutilizar, estendem e modificar o comportamento que está definido no outras classes.  A classe cujos membros são herdados é chamada a  *classe base*, e a classe que herda esses membros é chamada a  *classe derivada*.  Uma classe derivada pode ter somente uma classe base direta.  No entanto, a herança é transitiva.  Se ClassC é derivada da ClassB e ClassB é derivada da ClassA, ClassC herda os membros declarados em ClassB e ClassA.  
  
> [!NOTE]
>  Structs não oferecem suporte a herança, mas eles podem implementar interfaces.  Para obter mais informações, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
 Conceitualmente, uma classe derivada é uma especialização da classe base.  Por exemplo, se você tiver uma classe base `Animal`, você pode ter uma classe derivada chamado `Mammal` e outra classe derivada chamado `Reptile`.  A `Mammal` é um `Animal`e um `Reptile` é um `Animal`, mas cada classe derivada representa diferentes especializações da classe base.  
  
 Quando você Definir uma classe para derivar de outra classe, a classe derivada implicitamente obtém todos os membros da classe base, exceto para o construtores e destrutores.  A classe derivada, assim, pode reutilizar o código na classe base sem ter que reimplementar a ele.  Na classe derivada, você pode adicionar mais membros.  Dessa forma, a classe derivada estende a funcionalidade da classe base.  
  
 A ilustração a seguir mostra uma classe `WorkItem` que representa um item de trabalho em algum processo de negócios.  Como todas as classes, ele deriva de <xref:System.Object?displayProperty=fullName> e herda todos os seus métodos.  `WorkItem`adiciona cinco membros de sua própria.  Eles incluem um construtor, porque os construtores não são herdadas.  Classe `ChangeRequest` herda de `WorkItem` e representa um determinado tipo de item de trabalho.  `ChangeRequest`adiciona dois membros de mais para os membros que ele herda de `WorkItem` de <xref:System.Object>.  Ele deve adicionar seu próprio construtor e também adiciona `originalItemID`.  Propriedade `originalItemID` permite que o `ChangeRequest` instância a ser associado ao original `WorkItem` ao qual a solicitação de alteração se aplica.  
  
 ![Herança de classe](../../../csharp/programming-guide/classes-and-structs/media/class_inheritance.png "Class\_Inheritance")  
Herança de classe  
  
 O exemplo a seguir mostra como as relações de classe demonstradas na ilustração anterior são expressas em C\#.  O exemplo também mostra como `WorkItem` substitui o método virtual <xref:System.Object.ToString%2A?displayProperty=fullName>e como o `ChangeRequest` classe herda de `WorkItem` implementação do método.  
  
 [!code-cs[csProgGuideInheritance#49](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/inheritance_1.cs)]  
  
## Métodos abstratos e virtuais  
 Quando uma classe base declara um método como  [virtual](../../../csharp/language-reference/keywords/virtual.md), uma classe derivada pode  [Substituir](../../../csharp/language-reference/keywords/override.md) o método com sua própria implementação.  Se uma classe base declarar um membro como  [abstrata](../../../csharp/language-reference/keywords/abstract.md), que o método deve ser substituído em qualquer classe não\-abstrata que herda diretamente a partir dessa classe.  Se uma classe derivada é abstrato, ela herda membros abstratos sem ter que implementá\-los.  Os membros abstratos e virtuais são a base para o polimorfismo, que é a segunda característica principal da programação orientada a objeto.  Para obter mais informações, consulte [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).  
  
## Classes Base abstratas  
 Você pode declarar uma classe como  [abstrata](../../../csharp/language-reference/keywords/abstract.md) se você quiser impedir a instanciação direta usando o  [nova](../../../csharp/language-reference/keywords/new.md) palavra\-chave.  Se você fizer isso, a classe pode ser usada somente se uma nova classe é derivada.  Uma classe abstrata pode conter uma ou mais assinaturas de método que eles mesmos são declaradas como abstrato.  Essas assinaturas de especificam os parâmetros e retornam o valor, mas não possuem implementação \(corpo de método\).  Não tem uma classe abstrata conter membros abstratos; No entanto, se uma classe contiver um membro abstract, a própria classe deve ser declarada como abstrato.  Classes derivadas que não são abstratas próprios devem fornecer a implementação de quaisquer métodos abstratos de uma classe base abstrata.  Para obter mais informações, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## Interfaces  
 Um  *interface* é um tipo de referência que é um pouco semelhante a uma classe base abstrata que consiste somente os membros abstratos.  Quando uma classe implementa uma interface, ele deve fornecer uma implementação para todos os membros da interface.  Uma classe pode implementar várias interfaces, mesmo que ele pode derivar de apenas uma única classe base direta.  
  
 Interfaces são usadas para definir recursos específicos para as classes que não têm necessariamente uma "é uma" relação.  Por exemplo, o <xref:System.IEquatable%601?displayProperty=fullName> interface pode ser implementada por qualquer classe ou struct que possui para habilitar o código do cliente determinar se dois objetos do tipo são equivalentes \(no entanto, o tipo define equivalência\).  <xref:System.IEquatable%601>não implica o mesmo tipo de "é uma" relação existente entre uma classe base e uma classe derivada \(por exemplo, um `Mammal` é um `Animal`\).  Para obter mais informações, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
## Acesso de classe derivada para membros de classe Base  
 Uma classe derivada tem acesso aos membros internos públicos, protegidos, internos e protegidos de uma classe base.  Mesmo que uma classe derivada herda os membros privados de uma classe base, ele não pode acessar esses membros.  No entanto, todos esses membros particulares ainda estão presentes na classe derivada e pode fazer o mesmo trabalho que eles fariam na própria classe base.  Por exemplo, suponha que um método de classe base protegida acessa um campo particular.  Esse campo deve estar presente na classe derivada para o método de classe base herdado funcione corretamente.  
  
## Impedindo a derivação de mais  
 Uma classe pode impedir que outras classes de herdar dele, ou de qualquer um de seus membros, declarando si mesmo ou o membro como  [lacrado](../../../csharp/language-reference/keywords/sealed.md).  Para obter mais informações, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## Ocultação de classe derivada de membros de classe Base  
 Uma classe derivada pode ocultar os membros da classe base, declarando membros com o mesmo nome e assinatura.  O  [nova](../../../csharp/language-reference/keywords/new.md) modificador pode ser usado para indicar explicitamente que o membro não pretende ser uma substituição do membro base.  O uso de  [nova](../../../csharp/language-reference/keywords/new.md) não é necessária, mas um aviso de compilação será gerado se  [nova](../../../csharp/language-reference/keywords/new.md) não é usado.  Para obter mais informações, consulte [Controle de versão com as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)