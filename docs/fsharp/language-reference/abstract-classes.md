---
title: Classes abstratas
description: Saiba mais F# sobre as classes abstratas, que deixam alguns ou todos os membros não implementados e representam a funcionalidade comum de um conjunto diversificado de tipos de objetos.
ms.date: 05/16/2016
ms.openlocfilehash: a6bbfc23b858d5f3833f3f52b6dca46753080f03
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629684"
---
# <a name="abstract-classes"></a>Classes abstratas

*Classes abstratas* são classes que deixam alguns ou todos os membros não implementados, para que as implementações possam ser fornecidas por classes derivadas.

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

Na programação orientada a objeto, uma classe abstrata é usada como uma classe base de uma hierarquia e representa a funcionalidade comum de um conjunto diversificado de tipos de objeto. Como o nome "Abstract" implica, as classes abstratas geralmente não correspondem diretamente às entidades concretas no domínio problemático. No entanto, elas representam o que muitas entidades concretas diferentes têm em comum.

Classes abstratas devem ter `AbstractClass` o atributo. Eles podem ter membros implementados e não implementados. O uso do termo *abstract* quando aplicado a uma classe é o mesmo que em outras linguagens .net; no entanto, o uso do termo *abstract* quando aplicado a métodos (e propriedades) é um pouco diferente F# de seu uso em outras linguagens do .net. No F#, quando um método é marcado com a `abstract` palavra-chave, isso indica que um membro tem uma entrada, conhecida como um *slot de expedição virtual*, na tabela interna de funções virtuais para esse tipo. Em outras palavras, o método é virtual, embora a `virtual` palavra-chave não seja usada F# no idioma. A palavra `abstract` -chave é usada em métodos virtuais, independentemente de o método ser implementado ou não. A declaração de um slot de expedição virtual é separada da definição de um método para esse slot de expedição. Portanto, o F# equivalente a uma declaração de método virtual e definição em outra linguagem .net é uma combinação de uma declaração de método abstrato e uma definição separada, com a `default` palavra-chave `override` ou a palavra-chave. Para obter mais informações e exemplos, consulte [métodos](./members/methods.md).

Uma classe será considerada abstrata somente se houver métodos abstratos declarados, mas não definidos. Portanto, as classes que têm métodos abstratos não são necessariamente classes abstratas. A menos que uma classe tenha métodos abstratos indefinidos, não use o atributo **AbstractClass** .

Na sintaxe anterior, o *modificador de acessibilidade* pode `public`ser `private` ou `internal`. Para saber mais, veja [Controle de acesso](access-control.md).

Assim como ocorre com outros tipos, as classes abstratas podem ter uma classe base e uma ou mais interfaces base. Cada classe base ou interface aparece em uma linha separada junto com a `inherit` palavra-chave.

A definição de tipo de uma classe abstrata pode conter membros totalmente definidos, mas também pode conter membros abstratos. A sintaxe para membros abstratos é mostrada separadamente na sintaxe anterior. Nessa sintaxe, a *assinatura de tipo* de um membro é uma lista que contém os tipos de parâmetro em ordem e os tipos de retorno, `->` separados por tokens `*` e/ou tokens, conforme apropriado para os na forma curried e os parâmetros de tupla. A sintaxe para assinaturas de tipo de membro abstrato é a mesma usada em arquivos de assinatura e mostrada pelo IntelliSense no editor de Visual Studio Code.

O código a seguir ilustra uma forma de classe abstrata, que tem duas classes derivadas não abstratas, Square e Circle. O exemplo mostra como usar classes, métodos e propriedades abstratos. No exemplo, a forma da classe abstrata representa os elementos comuns do círculo e do quadrado das entidades concretas. Os recursos comuns de todas as formas (em um sistema de coordenadas bidimensional) são abstraidos na classe Shape: a posição na grade, um ângulo de rotação e as propriedades de área e de perímetro. Elas podem ser substituídas, exceto a posição, o comportamento de quais formas individuais não podem ser alteradas.

O método de rotação pode ser substituído, como na classe Circle, que é invariável de rotação devido à sua simetria. Portanto, na classe Circle, o método Rotation é substituído por um método que não faz nada.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Saída:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Consulte também

- [Classes](classes.md)
- [Membros](./members/index.md)
- [Métodos](./members/methods.md)
- [Propriedades](./members/Properties.md)
