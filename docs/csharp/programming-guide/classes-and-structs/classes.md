---
title: "Classes (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eedb087f177b1bff6f4d4177cd56ac4cca016490
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="classes-c-programming-guide"></a>Classes (Guia de Programação em C#)
Uma *classe* é um constructo que permite que você crie seus próprios tipos personalizados através do agrupamento de variáveis de outros tipos, métodos e eventos. Uma classe é como um plano gráfico. Ela define os dados e o comportamento de um tipo. Se a classe não for declarada como estática, o código cliente poderá usá-la criando *objetos* ou *instâncias* que são atribuídas a uma variável. A variável permanece na memória até que todas as referências a ela saiam do escopo. Nesse momento, o CLR marca a variável como qualificada para a coleta de lixo. Se a classe for declarada como [estática](../../../csharp/language-reference/keywords/static.md), haverá apenas uma cópia na memória e o código cliente só poderá acessá-la por meio da própria classe e não por uma *variável de instância*. Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Diferentemente de structs, as classes dão suporte à *herança*, uma característica fundamental da programação orientada a objeto. Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Declarando Classes  
 As classes são declaradas usando a palavra-chave [class](../../../csharp/language-reference/keywords/class.md), conforme mostrado no exemplo a seguir:  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 A palavra-chave `class` é precedida pelo nível de acesso. Como [público](../../../csharp/language-reference/keywords/public.md) é usado nesse caso, qualquer pessoa pode criar objetos dessa classe. O nome da classe segue a palavra-chave `class`. O restante da definição é o corpo da classe, em que o comportamento e os dados são definidos. Campos, propriedades, métodos e eventos em uma classe são coletivamente denominados de *membros de classe*.  
  
## <a name="creating-objects"></a>Criando Objetos  
 Embora eles sejam usados algumas vezes de maneira intercambiável, uma classe e um objeto são coisas diferentes. Uma classe define um tipo de objeto, mas não é um objeto em si. Um objeto é uma entidade concreta com base em uma classe e, às vezes, é conhecido como uma instância de uma classe.  
  
 Os objetos podem ser criados usando a palavra-chave [new](../../../csharp/language-reference/keywords/new.md), seguida pelo nome da classe na qual ele se baseará, dessa maneira:  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Quando uma instância de uma classe é criada, uma referência ao objeto é passada de volta para o programador. No exemplo anterior, `object1` é uma referência a um objeto que é baseado em `Customer`. Esta referência refere-se ao novo objeto, mas não contém os dados de objeto. Na verdade, você pode criar uma referência de objeto sem criar um objeto:  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Não recomendamos a criação de referências de objeto como essa, que não faz referência a um objeto, porque tentar acessar um objeto por meio de uma referência desse tipo falhará em tempo de execução. Entretanto, essa referência pode ser feita para se referir a um objeto, criando um novo objeto ou atribuindo-a a um objeto existente, como abaixo:  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Esse código cria duas referências de objeto que fazem referência ao mesmo objeto. Portanto, qualquer alteração no objeto feita por meio de `object3` será refletida no usos subsequentes de `object4`. Como os objetos que são baseados em classes são referenciados por referência, as classes são conhecidas como tipos de referência.  
  
## <a name="class-inheritance"></a>Herança da Classe  
 A herança é realizada usando uma *derivação*, o que significa que uma classe é declarada usando uma *classe base*, da qual ela herda o comportamento e os dados. Uma classe base é especificada ao acrescentar dois-pontos e o nome de classe base depois do nome de classe derivada, dessa maneira:  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Quando uma classe declara uma classe base, ela herda todos os membros da classe base, exceto os construtores.  
  
 Ao contrário do C++, uma classe no C# só pode herdar diretamente de uma classe base. No entanto, como uma classe base pode herdar de outra classe, uma classe pode herdar indiretamente várias classes base. Além disso, uma classe pode implementar diretamente mais de uma interface. Para obter mais informações, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
 Uma classe pode ser declarada [abstract](../../../csharp/language-reference/keywords/abstract.md). Uma classe abstrata contém métodos abstratos que têm uma definição de assinatura, mas não têm implementação. As classes abstratas não podem ser instanciadas. Elas só podem ser usadas por meio de classes derivadas que implementam os métodos abstratos. Por outro lado, uma classe [lacrada](../../../csharp/language-reference/keywords/sealed.md) não permite que outras classes sejam derivadas dela. Para obter mais informações, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 As definições de classe podem ser divididas entre arquivos de origem diferentes. Para obter mais informações, consulte [Classes e métodos parciais](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Descrição  
 No exemplo a seguir, é definida uma classe pública que contém um único campo, um método e um método chamado construtor. Para saber mais, veja [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md). Então, a classe é instanciada com a palavra-chave `new`.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Programação Orientada a Objeto](../concepts/object-oriented-programming.md)   
 [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [Membros](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [Objetos](../../../csharp/programming-guide/classes-and-structs/objects.md)

