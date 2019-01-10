---
title: Palavra-chave public – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 15b86920736f1220553b462d103841ac98d88b7c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239297"
---
# <a name="public-c-reference"></a>public (Referência de C#)

A palavra-chave `public` é um modificador de acesso para tipos e membros de tipo. Acesso público é o nível de acesso mais permissivo. Não há nenhuma restrição quanto ao acesso a membros públicos, como neste exemplo:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Consulte [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md) e [Níveis de acessibilidade](accessibility-levels.md) para obter mais informações.

## <a name="example"></a>Exemplo

No exemplo a seguir, duas classes são declaradas, `PointTest` e `MainClass`. Os membros públicos `x` e `y` de `PointTest` são acessados diretamente de `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Se alterar o nível de acesso de `public` para [particular](private.md) ou [protegido](protected.md), você receberá a mensagem de erro:

'PointTest.y' é inacessível devido ao seu nível de proteção.

## <a name="c-language-specification"></a>Especificação da linguagem C#  

Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Palavras-chave do C#](index.md)
- [Modificadores de acesso](access-modifiers.md)
- [Níveis de acessibilidade](accessibility-levels.md)
- [Modificadores](modifiers.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)