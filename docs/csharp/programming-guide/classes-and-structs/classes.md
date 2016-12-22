---
title: "Classes (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "classes [C#]"
  - "Linguagem c#, classes"
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
caps.handback.revision: 40
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Classes (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

*Uma classe* é uma compilação que permite a você criar seus próprios tipos personalizados agrupamento juntos variáveis de outros tipos, métodos e eventos.  Uma classe é como um modelo.  Define os dados e comportamento de um tipo.  Se a classe não é declarada como estático, o código do cliente pode usá\-la criando *objetos* ou *instâncias* que são atribuídos a uma variável.  A variável permanece na memória até que todas as referências a ela saiam de escopo.  No momento, o CLR marcá\-lo como qualificado para coleta de lixo.  Se a classe é declarada como [static](../../../csharp/language-reference/keywords/static.md), então apenas uma cópia existe na memória e o código do cliente só pode acessá\-lo através da classe em si, não *uma variável de instância*.  Para obter mais informações, consulte [Classes static e membros de classes static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Diferentemente de estruturas, as classes oferecem suporte *a herança*, uma característica fundamental da programação orientada a objeto.  Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## Declarando classes  
 Classes são declaradas usando a palavra\-chave de [classe](../../../csharp/language-reference/keywords/class.md) , conforme mostrado no exemplo o seguir:  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 A palavra\-chave de `class` é precedido pelo nível de acesso.  Porque [público](../../../csharp/language-reference/keywords/public.md) é usado nesse caso, ou pode criar objetos dessa classe.  O nome da classe segue a palavra\-chave de `class` .  O restante de definição é o corpo da classe, onde o comportamento e os dados são definidos.  Os campos, propriedades, métodos, e eventos de uma classe são coletivamente chamados *membros da classe*.  
  
## Criando objetos  
 Embora eles sejam usados de forma intercambiável às vezes, uma classe e um objeto são coisas diferentes.  Uma classe define um tipo de objeto, mas não é um objeto.  Um objeto é uma entidade concreta com base em uma classe, e as vezes é conhecido como uma instância de uma classe.  
  
 Objetos podem ser criados usando a palavra\-chave de [novo](../../../csharp/language-reference/keywords/new.md) seguida do nome da classe que o objeto será baseado no, assim:  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Quando uma instância de uma classe é criada, uma referência ao objeto é passado de volta para o programador.  No exemplo anterior, `object1` é uma referência a um objeto que é baseado em `Customer`.  Essa referência se refere ao novo objeto mas não contém os próprios dados do objeto.  Na verdade, você pode criar uma referência de objeto sem criar um objeto de qualquer:  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Não recomendamos criar referência de objeto como essa que não se refere a um objeto porque tentando acessar um objeto com tal referência falhará em tempo de execução.  No entanto, tal referência pode ser feita para se referir a um objeto, criando um novo objeto, ou atribuindo\-o a um objeto existente, como este:  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Esse código cria duas referências de objetos aqueles que ambos referem\-se ao mesmo objeto.  Como consequência, todas as alterações para o objeto feito com `object3` serão refletidas em usa subsequentes de `object4`.  Como os objetos que são baseados em classes são referenciados por referência, classes são conhecidas como a referência tipos.  
  
## Herança de classe  
 A herança é realizada usando *uma base*, o que significa que uma classe é declarada usando *uma classe base* que herda de dados e comportamento.  Uma classe base é especificada para acrescentar dois\-pontos e o nome da classe base após o nome de classe derivada, assim:  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Quando uma classe declara uma classe base, herda todos os membros da classe base exceto os construtores.  
  
 Diferentemente de uma classe em C\+\+, C\# somente pode diretamente herdar de uma classe base.  No entanto, como uma classe base própria pode herdar de outra classe, uma classe pode herdar indiretamente várias classes base.  Além disso, uma classe pode implementar diretamente mais de uma interface.  Para obter mais informações, consulte [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md).  
  
 Uma classe pode ser declarada [sumário](../../../csharp/language-reference/keywords/abstract.md).  Uma classe abstrata contém métodos abstratos que não têm uma definição de assinatura mas nenhuma implementação.  As classes abstratas não podem ser instanciadas.  Só podem ser usados por meio de classes derivadas que implementam os métodos abstratos.  Por constrast, uma classe de [sealed](../../../csharp/language-reference/keywords/sealed.md) não permite que outras classes derivem\-se de ela.  Para obter mais informações, consulte [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 As definições de classe podem ser de divisão entre os arquivos de origem diferentes.  Para obter mais informações, consulte [Classes e métodos partial](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## Descrição  
 No exemplo, uma classe pública que contém um único campo, um método, e um método chamado um construtor são definidos.  Para obter mais informações, consulte [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md).  A classe é instanciada em com a palavra\-chave de `new` .  
  
## Exemplo  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Programação orientada a objeto](../Topic/Object-Oriented%20Programming%20\(C%23%20and%20Visual%20Basic\).md)   
 [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [Membros](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [Métodos](../../../fsharp/language-reference/members/methods.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destruidores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [Objetos](../../../csharp/programming-guide/classes-and-structs/objects.md)