---
title: "Classes – Guia de C#"
description: "Saiba mais sobre os tipos de classes e como criá-las"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.translationtype: HT
ms.sourcegitcommit: b041fbec3ff22157d00af2447e76a7ce242007fc
ms.openlocfilehash: 13cbd3a5b53ea9b0f1acb22684b6a28639d00751
ms.contentlocale: pt-br
ms.lasthandoff: 09/14/2017

---

# <a name="classes"></a>Classes
Uma *classe* é um constructo que permite que você crie seus próprios tipos personalizados através do agrupamento de variáveis de outros tipos, métodos e eventos. Uma classe é como um plano gráfico. Ela define os dados e o comportamento de um tipo. Se a classe não for declarada como estática, o código cliente poderá usá-la criando *objetos* ou *instâncias* que são atribuídas a uma variável. A variável permanece na memória até que todas as referências a ela saiam do escopo. Nesse momento, o CLR marca a variável como qualificada para a coleta de lixo. Se a classe for declarada como [estática](language-reference/keywords/static.md), haverá apenas uma cópia na memória e o código cliente só poderá acessá-la por meio da própria classe e não por uma *variável de instância*. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Tipos de referência  
Um tipo que é definido como uma [classe](language-reference/keywords/class.md) é um *tipo de referência*. No tempo de execução, quando você declara uma variável de um tipo de referência, a variável contém o valor [null](language-reference/keywords/null.md) até que você crie explicitamente uma instância do objeto usando o operador [new](language-reference/keywords/new.md) ou atribua a ela um objeto que foi criado em outro lugar usando [new](language-reference/keywords/new.md), conforme mostrado no exemplo a seguir:  

[!code-csharp[Reference Types](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
Quando o objeto é criado, a memória é alocada no heap gerenciado e a variável contém apenas uma referência para o local do objeto. Os tipos no heap gerenciado requerem sobrecarga quando são alocados e quando são recuperados pela funcionalidade de gerenciamento automático de memória do CLR, que é conhecida como *coleta de lixo*. No entanto, a coleta de lixo também é altamente otimizada e na maioria dos cenários não cria problemas de desempenho. Para obter mais informações sobre a coleta de lixo, consulte [Gerenciamento automático de memória e coleta de lixo](../standard/garbage-collection/gc.md).  
  
Os tipos de referência dão suporte completo à *herança*, uma característica fundamental da programação orientada a objetos. Ao criar uma classe, você pode herdar de qualquer outra interface ou classe que não esteja definida como [lacrada](language-reference/keywords/sealed.md) e outras classes podem herdar de sua classe e substituir seus métodos virtuais. Para obter mais informações, consulte [Herança](programming-guide/classes-and-structs/inheritance.md).

## <a name="declaring-classes"></a>Declarando classes  
As classes são declaradas usando a palavra-chave [class](language-reference/keywords/class.md), conforme mostrado no exemplo a seguir:  
  
[!code-csharp[Declaring Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
A palavra-chave **class** é precedida pelo modificador de acesso. Como [público](language-reference/keywords/public.md) é usado nesse caso, qualquer pessoa pode criar objetos dessa classe. O nome da classe segue a palavra-chave **class**. O restante da definição é o corpo da classe, em que o comportamento e os dados são definidos. Campos, propriedades, métodos e eventos em uma classe são coletivamente denominados de *membros de classe*.  
  
## <a name="creating-objects"></a>Criando objetos  
Uma classe define um tipo de objeto, mas não é um objeto em si. Um objeto é uma entidade concreta com base em uma classe e, às vezes, é conhecido como uma instância de uma classe.  
  
Os objetos podem ser criados usando a palavra-chave [new](language-reference/keywords/new.md), seguida pelo nome da classe na qual ele se baseará, dessa maneira:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
Quando uma instância de uma classe é criada, uma referência ao objeto é passada de volta para o programador. No exemplo anterior, `object1` é uma referência a um objeto que é baseado em `Customer`. Esta referência refere-se ao novo objeto, mas não contém os dados de objeto. Na verdade, você pode criar uma referência de objeto sem criar um objeto:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
Não recomendamos a criação de referências de objeto como essa, que não faz referência a um objeto, porque tentar acessar um objeto por meio de uma referência desse tipo gerará falha em tempo de execução. Entretanto, essa referência pode ser feita para se referir a um objeto, criando um novo objeto ou atribuindo-a a um objeto existente, como abaixo:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
Esse código cria duas referências de objeto que fazem referência ao mesmo objeto. Portanto, qualquer alteração no objeto feita por meio de `object3` será refletida no usos subsequentes de `object4`. Como os objetos que são baseados em classes são referenciados por referência, as classes são conhecidas como tipos de referência.  
  
## <a name="class-inheritance"></a>Herança de classe  
A herança é realizada usando uma *derivação*, o que significa que uma classe é declarada usando uma *classe base*, da qual ela herda o comportamento e os dados. Uma classe base é especificada ao acrescentar dois-pontos e o nome de classe base depois do nome de classe derivada, dessa maneira:  
  
[!code-csharp[Inheritance](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
Quando uma classe declara uma classe base, ela herda todos os membros da classe base, exceto os construtores.  
  
Ao contrário do C++, uma classe no C# só pode herdar diretamente de uma classe base. No entanto, como uma classe base pode herdar de outra classe, uma classe pode herdar indiretamente várias classes base. Além disso, uma classe pode implementar diretamente mais de uma interface. Para obter mais informações, consulte [Interfaces](programming-guide/interfaces/index.md).  
  
Uma classe pode ser declarada [abstract](language-reference/keywords/abstract.md). Uma classe abstrata contém métodos abstratos que têm uma definição de assinatura, mas não têm implementação. As classes abstratas não podem ser instanciadas. Elas só podem ser usadas por meio de classes derivadas que implementam os métodos abstratos. Por outro lado, uma classe [lacrada](language-reference/keywords/sealed.md) não permite que outras classes sejam derivadas dela. Para obter mais informações, consulte [Classes e membros de classes abstratos e lacrados](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
As definições de classe podem ser divididas entre arquivos de origem diferentes. Para obter mais informações, consulte [Definições de classe parcial](programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
 
## <a name="example"></a>Exemplo
No exemplo a seguir, é definida uma classe pública que contém um único campo, um método e um método chamado construtor. Para saber mais, veja [Construtores](programming-guide/classes-and-structs/constructors.md). A classe, então, é instanciada com a palavra-chave **new**.

[!code-csharp[Class Example](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>especificação da linguagem C#  
Para obter mais informações, consulte a [Especificação da linguagem C#](language-reference/language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também  
[Guia de programação em C#](programming-guide/index.md)   
[Polimorfismo](programming-guide/classes-and-structs/polymorphism.md)   
[Membros de classe e struct](programming-guide/classes-and-structs/members.md)   
[Métodos de classe e struct](programming-guide/classes-and-structs/methods.md)   
[Construtores](programming-guide/classes-and-structs/constructors.md)   
[Finalizadores](programming-guide/classes-and-structs/destructors.md)   
[Objetos](programming-guide/classes-and-structs/objects.md)


