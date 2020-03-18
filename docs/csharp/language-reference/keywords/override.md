---
title: Modificador override – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713242"
---
# <a name="override-c-reference"></a>override (Referência de C#)

O modificador `override` é necessário para estender ou modificar a implementação abstrata ou virtual de um método, propriedade, indexador ou evento herdado.

## <a name="example"></a>Exemplo

Neste exemplo, `Square` a classe deve fornecer uma `GetArea` `GetArea` implementação substituída porque `Shape` é herdada da classe abstrata:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Um método `override` fornece uma nova implementação de um membro herdado de uma classe base. O método que é substituído por uma declaração `override` é conhecido como o método base substituído. O método base substituído deve ter a mesma assinatura que o método `override`. Para obter informações sobre herança, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md).

Você não pode substituir um método não virtual ou estático. O método base substituído deve ser `virtual`, `abstract` ou `override`.

Uma declaração `override` não pode alterar a acessibilidade do método `virtual`. O método `override` e o método `virtual` devem ter o mesmo [modificador de nível de acesso](access-modifiers.md).

Não é possível usar os modificadores `new`, `static` ou `virtual` para modificar um método `override`.

Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome que a propriedade herdada e a propriedade substituída deve ser `virtual`, `abstract` ou `override`.

Para obter mais informações `override` sobre como usar a palavra-chave, consulte [Versioning com o Override e Novas Palavras-Chave](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Saber quando usar Override e Novas Palavras-Chave](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Exemplo

Este exemplo define uma classe base chamada `Employee` e uma classe derivada chamada `SalesEmployee`. A classe `SalesEmployee` inclui um campo extra, `salesbonus`, e substitui o método `CalculatePay` para levar isso em consideração.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Herança](../../programming-guide/classes-and-structs/inheritance.md)
- [Palavras-chave do C#](index.md)
- [Modificadores](index.md)
- [Abstrata](abstract.md)
- [Virtual](virtual.md)
- [novo (modificador)](new-modifier.md)
- [Polimorfismo](../../programming-guide/classes-and-structs/polymorphism.md)
