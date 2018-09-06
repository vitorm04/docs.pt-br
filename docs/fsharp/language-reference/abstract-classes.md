---
title: Classes abstratas (F#)
description: 'Saiba mais sobre o F # classes abstratas, que deixar alguns ou todos os membros não implementados e representam a funcionalidade comum de um conjunto diversificado de tipos de objeto.'
ms.date: 05/16/2016
ms.openlocfilehash: 7e1bb9daca7e8a3b442cd7fb02ef99bb6a2085cb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745444"
---
# <a name="abstract-classes"></a>Classes abstratas

*Classes abstratas* são classes que deixam alguns ou todos os membros não implementados, para que as implementações podem ser fornecidas por classes derivadas.

## <a name="syntax"></a>Sintaxe

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Comentários

Na programação orientada a objeto, uma classe abstrata é usada como uma classe base de uma hierarquia e representa a funcionalidade comum de um conjunto diversificado de tipos de objeto. Como o "abstrato" nome implica, classes abstratas geralmente não correspondem diretamente em entidades concretas no domínio do problema. No entanto, elas representam o que muitas entidades concretas diferentes têm em comum.

Classes abstratas devem ter o `AbstractClass` atributo. Eles podem ter implementado e não implementados membros. O uso do termo *abstrata* quando aplicado a uma classe é o mesmo como em outras linguagens .NET; no entanto, o uso do termo *abstrata* quando aplicado a (propriedades e métodos) é um pouco diferente no F # do seu Use em outras linguagens .NET. No F #, quando um método é marcado com o `abstract` palavra-chave, isso indica que um membro tem uma entrada, conhecida como um *slot de expedição virtual*, na tabela de funções virtuais para esse tipo interna. Em outras palavras, o método é virtual, embora o `virtual` palavra-chave não é usada na linguagem F #. A palavra-chave `abstract` é usado em métodos virtuais, independentemente se o método é implementado. A declaração de um slot de expedição virtual é separada da definição de um método para esse slot de expedição. Portanto, o equivalente em F # de uma declaração de método virtual e uma definição em outra linguagem .NET é uma combinação de uma declaração de método abstrato e uma definição separada, com qualquer um de `default` palavra-chave ou o `override` palavra-chave. Para obter mais informações e exemplos, consulte [métodos](members/methods.md).

Uma classe é considerada abstrata somente se houver métodos abstratos que são declarados, mas não definidos. Portanto, as classes que têm os métodos abstratos não são necessariamente abstratas de classes. A menos que uma classe tem indefinido métodos abstratos, não use o **AbstractClass** atributo.

Na sintaxe anterior, *modificador de acessibilidade* pode ser `public`, `private` ou `internal`. Para saber mais, veja [Controle de acesso](access-control.md).

Assim como acontece com outros tipos, classes abstratas podem ter uma classe base e um ou mais interfaces base. Cada classe base ou interface é exibida em uma linha separada, junto com o `inherit` palavra-chave.

A definição de tipo de uma classe abstrata pode conter membros totalmente definidos, mas ele também pode conter membros abstratos. A sintaxe para membros abstratos é exibida separadamente na sintaxe anterior. Nesta sintaxe, o *assinatura de tipo* de um membro é uma lista que contém os tipos de parâmetros na ordem e os tipos de retorno, separados por `->` tokens de e/ou `*` tokens conforme apropriado para via currying e tupled parâmetros. A sintaxe para assinaturas de tipo de membro abstrato é o mesmo que o usado em arquivos de assinatura e se mostrado pelo IntelliSense no Editor de código do Visual Studio.

O código a seguir ilustra uma classe abstrata Shape, que tem duas classes de derivada não abstrata, círculo e um quadrado. O exemplo mostra como usar propriedades, métodos e classes abstratas. No exemplo, a forma de classe abstrata representa os elementos comuns do círculo de entidades concreta e quadrado. Os recursos comuns de todas as formas (em um sistema de coordenadas bidimensional) são abstraídos out em classe Shape: a posição na grade, um ângulo de rotação e as propriedades de área e perímetro. Elas podem ser substituídas, exceto para a posição, o comportamento dos quais formas individuais não é possível alterar.

O método de rotação pode ser substituído, como na classe do círculo, o que é invariável da rotação devido a seu simetria. Portanto, na classe do círculo, o método de rotação é substituído por um método que não faz nada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Saída:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Consulte também

- [Classes](classes.md)
- [Membros](members/index.md)
- [Métodos](members/methods.md)
- [Propriedades](members/Properties.md)
