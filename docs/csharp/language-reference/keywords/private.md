---
description: Palavra-chave private – Referência de C#
title: Palavra-chave private – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139392"
---
# <a name="private-c-reference"></a>private (Referência de C#)

A palavra-chave `private` é um modificador de acesso de membro.

> Esta página aborda o acesso `private`. A `private` palavra-chave também faz parte do [`private protected`](./private-protected.md) modificador de acesso.

Acesso particular é o nível de acesso menos permissivo. Membros particulares são acessíveis somente dentro do corpo da classe ou do struct em que são declarados, como neste exemplo:

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

Tipos aninhados no mesmo corpo também podem acessar os membros particulares.

É um erro em tempo de compilação fazer referência a um membro particular fora da classe ou do struct em que ele é declarado.

Para obter uma comparação de `private` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](accessibility-levels.md) e [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="example"></a>Exemplo

Neste exemplo, a classe `Employee` contém dois membros de dados particulares, `name` e `salary`. Como membros particulares, eles não podem ser acessados, exceto por métodos de membro. Métodos públicos chamados `GetName` e `Salary` foram adicionados para permitir acesso controlado aos membros particulares. O membro `name` é acessado por meio de um método público e o membro `salary` é acessado por meio de uma propriedade somente leitura pública. (Consulte [Propriedades](../../programming-guide/classes-and-structs/properties.md) para obter mais informações.)

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a>Especificação da linguagem C#  

Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Guia de programação C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores de acesso](access-modifiers.md)
- [Níveis de acessibilidade](accessibility-levels.md)
- [Modificadores](index.md)
- [public](public.md)
- [protegidos](protected.md)
- [interno](internal.md)
