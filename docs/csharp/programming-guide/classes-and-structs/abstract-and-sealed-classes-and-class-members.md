---
title: "Classes e membros de classes abstract e sealed (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dac7570c018bd577faac4540e4d800cc11143578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a>Classes e membros de classes abstract e sealed (Guia de Programação em C#)
A palavra-chave [abstract](../../../csharp/language-reference/keywords/abstract.md) permite que você crie classes e membros de [classe](../../../csharp/language-reference/keywords/class.md) que estão incompletos e devem ser implementados em uma classe derivada.  
  
 A palavra-chave [sealed](../../../csharp/language-reference/keywords/sealed.md) permite evitar a herança de uma classe ou de determinados membros de classe que foram marcados anteriormente com [virtual](../../../csharp/language-reference/keywords/virtual.md).  
  
## <a name="abstract-classes-and-class-members"></a>Classes abstratas e membros de classe  
 As classes podem ser declaradas como abstratas, colocando a palavra-chave `abstract` antes da definição de classe. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 Uma classe abstrata não pode ser instanciada. A finalidade de uma classe abstrata é fornecer uma definição comum de uma classe base que pode ser compartilhada por várias classes derivadas. Por exemplo, uma biblioteca de classes pode definir uma classe abstrata que serve como um parâmetro para muitas de suas funções e exige que os programadores que usam essa biblioteca forneçam sua própria implementação da classe, criando uma classe derivada.  
  
 As classes abstratas também podem definir métodos abstratos. Isso é realizado através da adição da palavra-chave `abstract` antes do tipo de retorno do método. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 Os métodos abstratos não têm implementação, portanto, a definição do método é seguida por um ponto e vírgula, em vez de um bloco de método normal. As classes derivadas da classe abstrata devem implementar todos os métodos abstratos. Quando uma classe abstrata herda um método virtual de uma classe base, a classe abstrata pode substituir o método virtual por um método abstrato. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 Se um método `virtual` for declarado `abstract`, ele ainda será virtual para qualquer classe que herdar da classe abstrata. Uma classe que herda um método abstrato não pode acessar a implementação original do método. No exemplo anterior, `DoWork` na classe F não pode chamar `DoWork` na classe D. Dessa forma, uma classe abstrata pode forçar classes derivadas a fornecerem novas implementações de método para métodos virtuais.  
  
## <a name="sealed-classes-and-class-members"></a>Classes e membros de classes sealed  
 As classes podem ser declaradas como [sealed](../../../csharp/language-reference/keywords/sealed.md), colocando a palavra-chave `sealed` antes da definição de classe. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 Uma classe sealed não pode ser usada como uma classe base. Por esse motivo, também não pode ser uma classe abstrata. As classes sealed impedem a derivação. Como elas nunca podem ser usadas como uma classe base, algumas otimizações em tempo de execução podem tornar a chamada a membros de classe sealed ligeiramente mais rápida.  
  
 Um método, um indexador, uma propriedade ou um evento em uma classe derivada que está substituindo um membro virtual da classe base, pode declarar esse membro como sealed. Isso anula o aspecto virtual do membro para qualquer outra classe derivada. Isso é realizado através da colocação da palavra-chave `sealed` antes da palavra-chave [override](../../../csharp/language-reference/keywords/override.md) na declaração de membro de classe. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [Como definir propriedades abstract](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
