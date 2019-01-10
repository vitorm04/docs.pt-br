---
title: virtual – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: eede3359b195661ff89a387e9b226bc970c27942
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612563"
---
# <a name="virtual-c-reference"></a>virtual (Referência de C#)

A palavra-chave `virtual` é usada para modificar uma declaração de método, propriedade, indexador ou evento e permitir que ela seja substituída em uma classe derivada. Por exemplo, esse método pode ser substituído por qualquer classe que o herde:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

A implementação de um membro virtual pode ser alterada por um [membro de substituição](override.md) em uma classe derivada. Para obter mais informações sobre como usar a palavra-chave `virtual`, consulte [Controle de versão com as palavras-chave override e new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras-chave override e new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Comentários

Quando um método virtual é invocado, o tipo de tempo de execução do objeto é verificado para um membro de substituição. O membro de substituição na classe mais derivada é chamado, que pode ser o membro original, se nenhuma classe derivada tiver substituído o membro.

Por padrão, os métodos não são virtuais. Você não pode substituir um método não virtual.

Não é possível usar o modificador `virtual` com os modificadores `static`, `abstract`, `private` ou `override`. O exemplo a seguir mostra uma propriedade virtual:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Propriedades virtuais se comportam como métodos abstratos, exceto pelas diferenças na sintaxe de declaração e chamada.

- É um erro usar o modificador `virtual` em uma propriedade estática.

- Uma propriedade herdada virtual pode ser substituída em uma classe derivada incluindo uma declaração de propriedade que usa o modificador `override`.

## <a name="example"></a>Exemplo

Neste exemplo, a classe `Shape` contém as duas coordenadas `x`, `y` e o método virtual `Area()`. Classes de forma diferentes como `Circle`, `Cylinder` e `Sphere` herdam a classe `Shape` e a área de superfície é calculada para cada figura. Cada classe derivada tem a própria implementação de substituição do `Area()`.

Observe que as classes herdadas `Circle`, `Sphere` e `Cylinder` usam construtores que inicializam a classe base, conforme mostrado na declaração a seguir.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

O programa a seguir calcula e exibe a área apropriada para cada figura invocando a implementação apropriada do método `Area()`, de acordo com o objeto que está associado ao método.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Modificadores](modifiers.md)
- [Palavras-chave do C#](index.md)
- [Polimorfismo](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [new](new.md)