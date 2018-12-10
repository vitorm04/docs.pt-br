---
title: Palavra-chave private (Referência em C#)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a817f3f60b76b51868c5cacd8e648ec10497f64a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130995"
---
# <a name="private-c-reference"></a>private (Referência de C#)

A palavra-chave `private` é um modificador de acesso de membro.

> Esta página aborda o acesso `private`. A palavra-chave `private` também faz parte do modificador de acesso [`private protected`](./private-protected.md).

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

Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores de acesso](access-modifiers.md)
- [Níveis de acessibilidade](accessibility-levels.md)
- [Modificadores](modifiers.md)
- [public](public.md)
- [protected](protected.md)
- [internal](internal.md)