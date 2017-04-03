---
title: Classes | Guia de C#
description: "Saiba mais sobre os tipos de classes e como criá-las"
keywords: .NET, .NET Core, C#
author: stevehoag
ms.author: shoag
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4b5614123d38ae00cb471ef85d0eb92c03c68bba
ms.lasthandoff: 03/13/2017

---

# <a name="classes"></a>Classes
Uma *classe* é um constructo que permite que você crie seus próprios tipos personalizados através do agrupamento de variáveis de outros tipos, métodos e eventos. Uma classe é como um plano gráfico. Ela define os dados e o comportamento de um tipo. Se a classe não for declarada como estática, o código cliente poderá usá-la criando *objetos* ou *instâncias* que são atribuídas a uma variável. A variável permanece na memória até que todas as referências a ela saiam do escopo. Nesse momento, o CLR marca a variável como qualificada para a coleta de lixo. Se a classe for declarada como [estática](https://msdn.microsoft.com/library/98f28cdx.aspx), haverá apenas uma cópia na memória e o código cliente só poderá acessá-la por meio da própria classe e não por uma *variável de instância*. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](https://msdn.microsoft.com/library/79b3xss3.aspx).  

## <a name="reference-types"></a>Tipos de referência  
Um tipo que é definido como uma [classe](https://msdn.microsoft.com/library/0b0thckt.aspx) é um *tipo de referência*. No tempo de execução, quando você declara uma variável de um tipo de referência, a variável contém o valor [null](https://msdn.microsoft.com/library/edakx9da.aspx) até que você crie explicitamente uma instância do objeto usando o operador [new](https://msdn.microsoft.com/library/51y09td4.aspx) ou atribua a ela um objeto que foi criado em outro lugar usando [new](https://msdn.microsoft.com/library/51y09td4.aspx), conforme mostrado no exemplo a seguir:  

[!code-csharp[Tipos de Referência](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
Quando o objeto é criado, a memória é alocada no heap gerenciado e a variável contém apenas uma referência ao local do objeto. Os tipos no heap gerenciado requerem sobrecarga quando são alocados e quando são recuperados pela funcionalidade de gerenciamento automático de memória do CLR, que é conhecida como *coleta de lixo*. No entanto, a coleta de lixo também é altamente otimizada e na maioria dos cenários não cria problemas de desempenho. Para obter mais informações sobre a coleta de lixo, consulte [Gerenciamento automático de memória e coleta de lixo](../standard/garbagecollection/gc.md).  
  
Os tipos de referência dão suporte completo à *herança*, uma característica fundamental da programação orientada a objetos. Ao criar uma classe, você pode herdar de qualquer outra interface ou classe que não esteja definida como [lacrada](https://msdn.microsoft.com/library/88c54tsw.aspx) e outras classes podem herdar de sua classe e substituir seus métodos virtuais. Para obter mais informações, consulte [Herança](https://msdn.microsoft.com/library/ms173149.aspx).

## <a name="declaring-classes"></a>Declarando classes  
As classes são declaradas usando a palavra-chave [class](https://msdn.microsoft.com/library/0b0thckt.aspx), conforme mostrado no exemplo a seguir:  
  
[!code-csharp[Declarando Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
A palavra-chave **class** é precedida pelo modificador de acesso. Como [público](https://msdn.microsoft.com/library/yzh058ae.aspx) é usado nesse caso, qualquer pessoa pode criar objetos dessa classe. O nome da classe segue a palavra-chave **class**. O restante da definição é o corpo da classe, em que o comportamento e os dados são definidos. Campos, propriedades, métodos e eventos em uma classe são coletivamente denominados de *membros de classe*.  
  
## <a name="creating-objects"></a>Criando objetos  
Uma classe define um tipo de objeto, mas não é um objeto em si. Um objeto é uma entidade concreta com base em uma classe e, às vezes, é conhecido como uma instância de uma classe.  
  
Os objetos podem ser criados usando a palavra-chave [new](https://msdn.microsoft.com/library/51y09td4.aspx), seguida pelo nome da classe na qual ele se baseará, dessa maneira:  
  
[!code-csharp[Criando Objetos](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
Quando uma instância de uma classe é criada, uma referência ao objeto é passada de volta para o programador. No exemplo anterior, `object1` é uma referência a um objeto que é baseado em `Customer`. Esta referência refere-se ao novo objeto, mas não contém os dados de objeto. Na verdade, você pode criar uma referência de objeto sem criar um objeto:  
  
[!code-csharp[Criando Objetos](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
Não recomendamos a criação de referências de objeto como essa, que não faz referência a um objeto, porque tentar acessar um objeto por meio de uma referência desse tipo gerará falha em tempo de execução. Entretanto, essa referência pode ser feita para se referir a um objeto, criando um novo objeto ou atribuindo-a a um objeto existente, como abaixo:  
  
[!code-csharp[Criando Objetos](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
Esse código cria duas referências de objeto que fazem referência ao mesmo objeto. Portanto, qualquer alteração no objeto feita por meio de `object3` será refletida no usos subsequentes de `object4`. Como os objetos que são baseados em classes são referenciados por referência, as classes são conhecidas como tipos de referência.  
  
## <a name="class-inheritance"></a>Herança de classe  
A herança é realizada usando uma *derivação*, o que significa que uma classe é declarada usando uma *classe base*, da qual ela herda o comportamento e os dados. Uma classe base é especificada ao acrescentar dois-pontos e o nome de classe base depois do nome de classe derivada, dessa maneira:  
  
[!code-csharp[Herança](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
Quando uma classe declara uma classe base, ela herda todos os membros da classe base, exceto os construtores.  
  
Ao contrário do C++, uma classe no C# só pode herdar diretamente de uma classe base. No entanto, como uma classe base pode herdar de outra classe, uma classe pode herdar indiretamente várias classes base. Além disso, uma classe pode implementar diretamente mais de uma interface. Para obter mais informações, consulte [Interfaces](programming-guide/interfaces/index.md).  
  
Uma classe pode ser declarada [abstract](https://msdn.microsoft.com/library/sf985hc5.aspx). Uma classe abstrata contém métodos abstratos que têm uma definição de assinatura, mas não têm implementação. As classes abstratas não podem ser instanciadas. Elas só podem ser usadas por meio de classes derivadas que implementam os métodos abstratos. Por outro lado, uma classe [lacrada](https://msdn.microsoft.com/library/88c54tsw.aspx) não permite que outras classes sejam derivadas dela. Para obter mais informações, consulte [Classes e membros de classes abstratos e lacrados](https://msdn.microsoft.com/library/ms173150.aspx).  
  
As definições de classe podem ser divididas entre arquivos de origem diferentes. Para obter mais informações, consulte [Definições de classe parcial](https://msdn.microsoft.com/library/wa80x488.aspx).  
  
 
## <a name="example"></a>Exemplo
No exemplo a seguir, é definida uma classe pública que contém um único campo, um método e um método chamado construtor. Para saber mais, veja [Construtores](https://msdn.microsoft.com/library/ace5hbzh.aspx). A classe, então, é instanciada com a palavra-chave **new**.

[!code-csharp[Exemplo de classe](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>especificação da linguagem C#  
Para obter mais informações, consulte a [Especificação da linguagem C#](https://msdn.microsoft.com/library/ms228593.aspx). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também  
[Guia de programação em C#](https://msdn.microsoft.com/library/67ef8sbd.aspx)   
[Polimorfismo](https://msdn.microsoft.com/library/ms173152.aspx)   
[Membros de classe e struct](https://msdn.microsoft.com/library/ms173113.aspx)   
[Métodos de classe e struct](https://msdn.microsoft.com/library/ms173114.aspx)   
[Construtores](https://msdn.microsoft.com/library/ace5hbzh.aspx)   
[Destruidores](https://msdn.microsoft.com/library/66x5fx1b.aspx)   
[Objetos](https://msdn.microsoft.com/library/ms173110.aspx)


