---
title: Modificador sealed (referência do C#)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: cf6b85e2a04870b454b3bfea4d534680d22da8d1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188580"
---
# <a name="sealed-c-reference"></a>sealed (Referência de C#)

Quando aplicado a uma classe, o modificador `sealed` impede que outras classes herdem dela. No exemplo a seguir, a classe `B` herda da classe `A`, mas nenhuma classe pode herdar da classe `B`.

```csharp
class A {}
sealed class B : A {}
```

Você também pode usar o modificador `sealed` em um método ou propriedade que substitui um método ou propriedade virtual em uma classe base. Com isso, você pode permitir que classes sejam derivadas de sua classe e impedir que substituam métodos ou propriedades virtuais.

## <a name="example"></a>Exemplo

No exemplo a seguir, `Z` herda de `Y`, mas `Z` não pode substituir a função virtual `F` declarada em `X` e lacrada em `Y`.

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Quando define novos métodos ou propriedades em uma classe, você pode impedir que classes derivadas as substituam ao não declará-las como [virtuais](virtual.md).

É um erro usar o modificador [abstract](abstract.md) com uma classe selada, porque uma classe abstrata deve ser herdada por uma classe que fornece uma implementação dos métodos ou propriedades abstratas.

Quando aplicado a um método ou propriedade, o modificador `sealed` sempre deve ser usado com [override](override.md).

Como structs são lacrados implicitamente, eles não podem ser herdados.

Para obter mais informações, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md).

Para obter mais exemplos, consulte [Classes e membros de classes abstratas e lacradas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

No exemplo anterior, você pode tentar herdar da classe lacrada usando a instrução a seguir:

`class MyDerivedC: SealedClass {}   // Error`

O resultado é uma mensagem de erro:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a>Comentários

Para determinar se deve lacrar uma classe, método ou propriedade, geralmente você deve considerar os dois pontos a seguir:

- Os possíveis benefícios que as classes derivadas podem obter por meio da capacidade de personalizar a sua classe.

- O potencial de as classes derivadas modificarem suas classes de forma que elas deixem de funcionar corretamente ou como esperado.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Classes static e membros de classes static](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Classes e membros de classes abstract e sealed](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modificadores](modifiers.md)
- [override](override.md)
- [virtual](virtual.md)