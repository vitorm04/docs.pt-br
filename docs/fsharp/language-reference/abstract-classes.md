---
title: Classes abstratas (F#)
description: 'Saiba mais sobre F # classes abstratas, que deixar alguns ou todos os membros não implementados e representam a funcionalidade comum de um conjunto diversificado de tipos de objeto.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0d7ca996de89c44a5cfb9197c1b515741a2303df
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
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
Em programação orientada a objeto, uma classe abstrata é usada como uma classe base de uma hierarquia e representa a funcionalidade comum de um conjunto diversificado de tipos de objeto. Como o "abstrato" nome implica, classes abstratas geralmente não correspondem diretamente em concretas entidades no domínio do problema. No entanto, eles representam o que muitas entidades concretas diferentes têm em comum.

Classes abstratas devem ter o `AbstractClass` atributo. Pode ter implementado e não implementado membros. O uso do termo *abstrata* quando aplicado a uma classe é igual de outras linguagens .NET; no entanto, o uso do termo *abstrata* quando aplicado a métodos (e propriedades) é um pouco diferente em F # do seu Use em outras linguagens .NET. Em F #, quando um método é marcado com o `abstract` palavra-chave, isso indica que um membro tem uma entrada, conhecida como um *slot de expedição virtual*, na tabela interna de funções virtuais para esse tipo. Em outras palavras, o método é virtual, embora o `virtual` palavra-chave não é usada na linguagem F #. A palavra-chave `abstract` é usado em métodos virtuais, independentemente se o método é implementado. A declaração de um slot de expedição virtual é separada da definição de um método para esse slot de expedição. Portanto, o equivalente de uma declaração de método virtual e uma definição em outra linguagem .NET F # é uma combinação de uma declaração de método abstract e uma definição separada, com um o `default` palavra-chave ou o `override` palavra-chave. Para obter mais informações e exemplos, consulte [métodos](members/methods.md).

Uma classe é considerada abstrata somente se houver métodos abstratos que declarada, mas não definidos. Portanto, as classes que têm métodos abstratos não são necessariamente abstratas de classes. A menos que uma classe possui indefinido métodos abstratos, não use o **AbstractClass** atributo.

Na sintaxe anterior, *modificador de acessibilidade* pode ser `public`, `private` ou `internal`. Para saber mais, veja [Controle de acesso](access-control.md).

Assim como acontece com outros tipos, classes abstratas podem ter uma classe base e um ou mais interfaces base. Cada classe base ou interface aparece em uma linha separada junto com o `inherit` palavra-chave.

A definição do tipo de classe abstrata pode conter membros totalmente definidos, mas também pode conter membros abstratos. A sintaxe para membros abstratos é exibida separadamente na sintaxe anterior. Nessa sintaxe, o *assinatura de tipo* de um membro é uma lista que contém os tipos de parâmetro na ordem e os tipos de retorno, separados por `->` tokens e/ou `*` tokens conforme apropriado na forma curried e tupla parâmetros. A sintaxe para assinaturas de tipo de membro abstrato é o mesmo que o usado em arquivos de assinatura e se mostrado pelo IntelliSense no Editor de código do Visual Studio.

O código a seguir ilustra uma classe abstrata forma, que tem duas classes de derivado não-abstrato, quadrado e círculo. O exemplo mostra como usar propriedades, métodos e classes abstratas. No exemplo, a forma de classe abstrata representa os elementos comuns do círculo de entidades concreta e quadrado. Os recursos comuns de todas as formas (em um sistema de coordenadas bidimensional) são abstraídos limite para a classe de forma: a posição na grade, um ângulo de rotação e as propriedades de área e o perímetro. Esses podem ser substituídas, com exceção de posição, o comportamento dos quais não é possível alterar formas individuais.

O método de rotação pode ser substituído, como a classe do círculo, que é a rotação invariável devido a seu simetria. Para a classe do círculo, o método de rotação é substituído por um método que não faz nada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Saída:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Consulte também
[Classes](classes.md)

[Membros](members/index.md)

[Métodos](members/methods.md)

[Propriedades](members/Properties.md)
