---
title: Polimorfismo – Guia de Programação em C#
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170163"
---
# <a name="polymorphism-c-programming-guide"></a>Polimorfismo (Guia de Programação em C#)

O polimorfismo costuma ser chamado de o terceiro pilar da programação orientada a objetos, depois do encapsulamento e a herança. O polimorfismo é uma palavra grega que significa "de muitas formas" e tem dois aspectos distintos:
  
- Em tempo de execução, os objetos de uma classe derivada podem ser tratados como objetos de uma classe base, em locais como parâmetros de método, coleções e matrizes. Quando esse polimorfismo ocorre, o tipo declarado do objeto não é mais idêntico ao seu tipo de tempo de execução.
- As classes base podem definir e implementar [métodos](../../language-reference/keywords/virtual.md) *virtuais* e as classes derivadas podem [substituí-los](../../language-reference/keywords/override.md), o que significa que elas fornecem sua própria definição e implementação. Em tempo de execução, quando o código do cliente chama o método, o CLR procura o tipo de tempo de execução do objeto e invoca a substituição do método virtual. Em seu código-fonte, você pode chamar um método em uma classe base e fazer com que a versão do método de uma classe derivada seja executada.

Os métodos virtuais permitem que você trabalhe com grupos de objetos relacionados de maneira uniforme. Por exemplo, suponha que você tem um aplicativo de desenho que permite que um usuário crie vários tipos de formas sobre uma superfície de desenho. Você não sabe em tempo de compilação que tipos específicos de formas que o usuário criará. No entanto, o aplicativo precisa manter controle de todos os diferentes tipos de formas que são criados e atualizá-los em resposta às ações do mouse do usuário. Você pode usar o polimorfismo para resolver esse problema em duas etapas básicas:

1. Crie uma hierarquia de classes em que cada classe de forma específica derive de uma classe base comum.
1. Use um método virtual para invocar o método adequado em qualquer classe derivada por meio de uma única chamada para o método da classe base.

Primeiro, crie uma classe base chamada `Shape` e as classes derivadas como `Rectangle`, `Circle` e `Triangle`. Atribua à classe `Shape` um método virtual chamado `Draw` e substitua-o em cada classe derivada para desenhar a forma especial que a classe representa. Crie `List<Shape>` um objeto `Circle`e `Triangle`adicione `Rectangle` um , e a ele.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

Para atualizar a superfície de desenho, use um loop [foreach](../../language-reference/keywords/foreach-in.md) para iterar na lista e chamar o método `Draw` em cada objeto `Shape` na lista. Embora cada objeto da lista tenha um `Shape`tipo declarado de , é o tipo de tempo de execução (a versão substituída do método em cada classe derivada) que será invocada.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

Em C#, cada tipo é polimórfico porque todos os tipos, incluindo tipos definidos pelo usuário, herdam de <xref:System.Object>.  

## <a name="polymorphism-overview"></a>Visão geral do polimorfismo

### <a name="virtual-members"></a>Membros virtuais

Quando uma classe derivada herda de uma classe base, ela ganha todos os métodos, campos, propriedades e eventos da classe base. O designer da classe derivada pode diferentes escolhas para o comportamento dos métodos virtuais:

- A classe derivada pode substituir membros virtuais na classe base, definindo um novo comportamento.
- A classe derivada herda o método de classe base mais próximo sem sobrepor-lo, preservando o comportamento existente, mas permitindo que outras classes derivadas sobreponham o método.
- A classe derivada pode definir a nova implementação não virtual daqueles membros que ocultam as implementações da classe base.

Uma classe derivada poderá substituir um membro de classe base somente se o membro da classe base tiver sido declarado como [virtual](../../language-reference/keywords/virtual.md) ou [abstrato](../../language-reference/keywords/abstract.md). O membro derivado deve usar a palavra-chave [override](../../language-reference/keywords/override.md) para indicar explicitamente que o método destina-se a participar da invocação virtual. O código a seguir mostra um exemplo:

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Os campos não podem ser virtuais; apenas métodos, propriedades, eventos e indexadores podem ser virtuais. Quando uma classe derivada substitui um membro virtual, esse membro é chamado, mesmo quando uma instância dessa classe está sendo acessada como uma instância da classe base. O código a seguir mostra um exemplo:

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Os métodos e propriedades virtuais permitem que classes derivadas estendam uma classe base sem a necessidade de usar a implementação da classe base de um método. Para obter mais informações, consulte [Controle de versão com as palavras-chave override e new](./versioning-with-the-override-and-new-keywords.md). Uma interface fornece uma outra maneira de definir um método ou conjunto de métodos cuja implementação é deixada para classes derivadas. Para obter mais informações, consulte [Interfaces](../interfaces/index.md).

### <a name="hide-base-class-members-with-new-members"></a>Ocultar membros da classe base com novos membros

Se você quiser que sua classe derivada tenha um membro com o mesmo nome de um membro em uma classe base, você pode usar a [nova](../../language-reference/keywords/new-modifier.md) palavra-chave para ocultar o membro da classe base. A palavra-chave `new` é colocada antes do tipo de retorno de um membro de classe que está sendo substituído. O código a seguir mostra um exemplo:

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

Os membros da classe base oculta podem ser acessados a partir do código do cliente, lançando a instância da classe derivada para uma instância da classe base. Por exemplo: 

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>Impedir que classes derivadas sobrepor membros virtuais  

Os membros virtuais permanecem virtuais, independentemente de quantas classes foram declaradas entre o membro virtual e a classe que originalmente o declarou. Se `A` a classe declarar um `B` membro virtual, e a classe derivar `A`de , e `C` a classe deriva `B`ré , classe `C` herda o membro virtual, e pode substituí-lo, independentemente de a classe `B` declarar uma substituição para esse membro. O código a seguir mostra um exemplo:

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

Uma classe derivada pode interromper a herança virtual, declarando uma substituição como [sealed](../../language-reference/keywords/sealed.md). Parar a herança `sealed` requer colocar `override` a palavra-chave antes da palavra-chave na declaração do membro da classe. O código a seguir mostra um exemplo:

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

No exemplo anterior, `DoWork` o método não é mais `C`virtual para qualquer classe derivada de . Ainda é virtual para `C`exemplos de , mesmo que `B` eles `A`sejam lançados para digitar ou digitar . Os métodos selados podem ser substituídos por classes derivadas usando a `new` palavra-chave, como mostra o exemplo a seguir:

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

Neste caso, `DoWork` se for `D` chamado sobre `D`o uso `DoWork` de uma variável de tipo, o novo é chamado. Se uma variável `C` `B`de `A` tipo , ou for `D`usada para `DoWork` acessar uma instância de , uma chamada para `DoWork` seguir `C`as regras de herança virtual, encaminhando essas chamadas para a implementação do on class .

### <a name="access-base-class-virtual-members-from-derived-classes"></a>Acesso a membros virtuais da classe base de classes derivadas

A classe derivada que substituiu um método ou propriedade ainda pode acessar o método ou propriedade na classe base usando a palavra-chave `base`. O código a seguir mostra um exemplo:

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

Para obter mais informações, consulte [base](../../language-reference/keywords/base.md).

> [!NOTE]
> Recomendamos que os membros virtuais usem `base` para chamar a implementação da classe base do membro em sua própria implementação. Deixar o comportamento da classe base ocorrer permite que a classe derivada se concentre na implementação de comportamento específico para a classe derivada. Se a implementação da classe base não é chamado, cabe à classe derivada tornar seu comportamento compatível com o comportamento da classe base.

## <a name="in-this-section"></a>Nesta seção

- [Controle de versão com as palavras-chave override e new](./versioning-with-the-override-and-new-keywords.md)
- [Quando usar as palavras-chave override e new](./knowing-when-to-use-override-and-new-keywords.md)
- [Como substituir o método ToString](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Herança](./inheritance.md)
- [Classes e membros de classes abstratas e lacradas](./abstract-and-sealed-classes-and-class-members.md)
- [Métodos](./methods.md)
- [Eventos](../events/index.md)
- [Propriedades](./properties.md)
- [Indexadores](../indexers/index.md)
- [Tipos](../types/index.md)
