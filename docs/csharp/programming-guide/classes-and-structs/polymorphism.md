---
title: Polimorfismo (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 8bbf93d14a16b06441ba48b9d4e19cfd249e9146
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="polymorphism-c-programming-guide"></a>Polimorfismo (Guia de Programação em C#)
O polimorfismo costuma ser chamado de o terceiro pilar da programação orientada a objetos, depois do encapsulamento e a herança. O polimorfismo é uma palavra grega que significa "de muitas formas" e tem dois aspectos distintos:  
  
-   Em tempo de execução, os objetos de uma classe derivada podem ser tratados como objetos de uma classe base, em locais como parâmetros de método, coleções e matrizes. Quando isso ocorre, o tipo declarado do objeto não é mais idêntico ao seu tipo de tempo de execução.  
  
-   As classes base podem definir e implementar *métodos* [virtuais](../../../csharp/language-reference/keywords/virtual.md) e as classes derivadas podem [substituí-los](../../../csharp/language-reference/keywords/override.md), o que significa que elas fornecem sua própria definição e implementação. Em tempo de execução, quando o código do cliente chama o método, o CLR procura o tipo de tempo de execução do objeto e invoca a substituição do método virtual. Dessa forma, você pode chamar em seu código-fonte um método de uma classe base e fazer com que a versão de uma classe derivada do método seja executada.  
  
 Os métodos virtuais permitem que você trabalhe com grupos de objetos relacionados de maneira uniforme. Por exemplo, suponha que você tem um aplicativo de desenho que permite que um usuário crie vários tipos de formas sobre uma superfície de desenho. Você não sabe em tempo de compilação que tipos específicos de formas que o usuário criará. No entanto, o aplicativo precisa manter controle de todos os diferentes tipos de formas que são criados e atualizá-los em resposta às ações do mouse do usuário. Você pode usar o polimorfismo para resolver esse problema em duas etapas básicas:  
  
1.  Crie uma hierarquia de classes em que cada classe de forma específica derive de uma classe base comum.  
  
2.  Use um método virtual para invocar o método adequado em qualquer classe derivada por meio de uma única chamada para o método da classe base.  
  
 Primeiro, crie uma classe base chamada `Shape` e as classes derivadas como `Rectangle`, `Circle` e `Triangle`. Atribua à classe `Shape` um método virtual chamado `Draw` e substitua-o em cada classe derivada para desenhar a forma especial que a classe representa. Crie um objeto `List<Shape>` e adicione um círculo, triângulo e retângulo para ele. Para atualizar a superfície de desenho, use um loop [foreach](../../../csharp/language-reference/keywords/foreach-in.md) para iterar na lista e chamar o método `Draw` em cada objeto `Shape` na lista. Mesmo que cada objeto na lista tenha um tipo de declaração de `Shape`, é o tipo de tempo de execução (a versão de substituição do método em cada classe derivada) que será invocado.  
  
 [!code-csharp[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]  
  
 Em C#, cada tipo é polimórfico porque todos os tipos, incluindo tipos definidos pelo usuário, herdam de <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Visão Geral sobre o polimorfismo  
  
### <a name="virtual-members"></a>Membros virtuais  
 Quando uma classe derivada herda de uma classe base, ela ganha todos os métodos, campos, propriedades e eventos da classe base. O designer da classe derivada pode escolher entre  
  
-   substituir os membros virtuais na classe base,  
  
-   herdar o método da classe base mais próxima, sem ignorá-lo   
  
-   definir nova implementação não virtual desses membros que ocultam as implementações da classe base  
  
 Uma classe derivada poderá substituir um membro de classe base somente se o membro da classe base tiver sido declarado como [virtual](../../../csharp/language-reference/keywords/virtual.md) ou [abstrato](../../../csharp/language-reference/keywords/abstract.md). O membro derivado deve usar a palavra-chave [override](../../../csharp/language-reference/keywords/override.md) para indicar explicitamente que o método destina-se a participar da invocação virtual. O código a seguir mostra um exemplo:  
  
 [!code-csharp[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]  
  
 Os campos não podem ser virtuais, apenas os métodos, propriedades, eventos e indexadores podem ser virtuais. Quando uma classe derivada substitui um membro virtual, esse membro é chamado, mesmo quando uma instância dessa classe está sendo acessada como uma instância da classe base. O código a seguir mostra um exemplo:  
  
 [!code-csharp[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]  
  
 Os métodos e propriedades virtuais permitem que classes derivadas estendam uma classe base sem a necessidade de usar a implementação da classe base de um método. Para obter mais informações, consulte [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md). Uma interface fornece uma outra maneira de definir um método ou conjunto de métodos cuja implementação é deixada para classes derivadas. Para obter mais informações, consulte [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Ocultando membros de classe base com novos membros  
 Se você quiser que o seu membro derivado tenha o mesmo nome de um membro de uma classe base, mas não quiser que ele participe da invocação virtual, será possível usar a palavra-chave [new](../../../csharp/language-reference/keywords/new.md). A palavra-chave `new` é colocada antes do tipo de retorno de um membro de classe que está sendo substituído. O código a seguir mostra um exemplo:  
  
 [!code-csharp[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]  
  
 Você ainda pode acessar os membros da classe base ocultos a partir do código do cliente, convertendo a instância da classe derivada a uma instância da classe base. Por exemplo:  
  
 [!code-csharp[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Impedindo que classes derivadas substituam membros virtuais  
 Os membros virtuais permanecem virtuais por tempo indeterminado, independentemente de quantas classes foram declaradas entre o membro virtual e a classe que originalmente o declarou. Se a classe A declara um membro virtual, a classe B deriva de A e a classe C deriva de B, a classe C herda o membro virtual e tem a opção de substituí-lo, independentemente de a classe B ter declarado uma substituição para esse membro. O código a seguir mostra um exemplo:  
  
 [!code-csharp[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]  
  
 Uma classe derivada pode interromper a herança virtual, declarando uma substituição como [sealed](../../../csharp/language-reference/keywords/sealed.md). Isso exige a colocação da palavra-chave `sealed` antes da palavra-chave `override` na declaração de membro de classe. O código a seguir mostra um exemplo:  
  
 [!code-csharp[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]  
  
 No exemplo anterior, o método `DoWork` não será mais virtual para qualquer classe derivada de C. Ele ainda será virtual para instâncias de C, mesmo se elas forem convertidas em métodos tipo B ou tipo A. Métodos lacrados podem ser substituídos por classes derivadas usando a palavra-chave `new`, como mostra o exemplo a seguir:  
  
 [!code-csharp[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]  
  
 Neste caso, se `DoWork` é chamado em D usando uma variável do tipo D, o novo `DoWork` é chamado. Se uma variável do tipo C, B ou A é usada para acessar uma instância de D, uma chamada de `DoWork` seguirá as regras de herança virtual, encaminhando as chamadas para a implementação de `DoWork` na classe C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Acessando membros virtuais da classe base das classes derivadas  
 A classe derivada que substituiu um método ou propriedade ainda pode acessar o método ou propriedade na classe base usando a palavra-chave base. O código a seguir mostra um exemplo:  
  
 [!code-csharp[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]  
  
 Para obter mais informações, consulte [base](../../../csharp/language-reference/keywords/base.md).  
  
> [!NOTE]
>  Recomendamos que os membros virtuais usem `base` para chamar a implementação da classe base do membro em sua própria implementação. Deixar o comportamento da classe base ocorrer permite que a classe derivada se concentre na implementação de comportamento específico para a classe derivada. Se a implementação da classe base não é chamado, cabe à classe derivada tornar seu comportamento compatível com o comportamento da classe base.  
  
## <a name="in-this-section"></a>Nesta seção  
  
-   [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [Quando usar as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [Como substituir o método ToString)](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Classes e membros de classes abstract e sealed](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Eventos](../../../csharp/programming-guide/events/index.md)  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Indexadores](../../../csharp/programming-guide/indexers/index.md)  
 [Tipos](../../../csharp/programming-guide/types/index.md)
