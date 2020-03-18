---
title: interface – Referência de C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 473f5f8e226f0a144746ac943afcffdccd4777c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625846"
---
# <a name="no-loc-textinterface-c-reference"></a>:::no-loc text="interface":::(C# Referência)

Uma interface define um contrato. Qualquer [`class`](class.md) [`struct`](../builtin-types/struct.md) ou que implemente esse contrato deve fornecer uma implementação dos membros definidos na interface. Começando com C# 8.0, uma interface pode definir uma implementação padrão para membros. Ele também [`static`](static.md) pode definir membros a fim de fornecer uma única implementação para funcionalidade comum.

No exemplo a seguir, a classe `ImplementationClass` deve implementar um método chamado `SampleMethod` que não tem parâmetros e retorna `void`.

Para obter mais informações e exemplos, consulte [Interfaces](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Uma interface pode ser um membro de um namespace ou de uma classe. Uma declaração de interface pode conter declarações (assinaturas sem qualquer implementação) dos seguintes membros:

- [Métodos](../../programming-guide/classes-and-structs/methods.md)
- [Propriedades](../../programming-guide/classes-and-structs/using-properties.md)
- [Indexadores](../../programming-guide/indexers/using-indexers.md)
- [Eventos](event.md)

Essas declarações de membros anteriores normalmente não contêm um corpo. Começando com C# 8.0, um membro da interface pode declarar um corpo. Isso é chamado de *implementação padrão*. Membros com órgãos permitem que a interface forneça uma implementação "padrão" para classes e estruturas que não forneçam uma implementação predominante. Além disso, começando com C# 8.0, uma interface pode incluir:

- [Constantes](const.md)
- [Operadores](../operators/operator-overloading.md)
- [Construtor estático](../../programming-guide/classes-and-structs/constructors.md#static-constructors).
- [Tipos aninhados](../../programming-guide/classes-and-structs/nested-types.md)
- [Campos estáticos, métodos, propriedades, indexadores e eventos](static.md)
- Declarações de membros usando a sintaxe de implementação de interface explícita.
- Modificadores de acesso explícito (o acesso padrão é [`public`](access-modifiers.md)).

As interfaces podem não conter o estado de ocorrência. Embora os campos estáticos sejam agora permitidos, os campos de instância não são permitidos em interfaces. [As propriedades automáticas de instância](../../programming-guide/classes-and-structs/auto-implemented-properties.md) não são suportadas em interfaces, pois declarariam implicitamente um campo oculto. Esta regra tem um efeito sutil sobre as declarações de propriedade. Em uma declaração de interface, o código a seguir não `class` `struct`declara uma propriedade auto-implementada como faz em um ou . Em vez disso, declara uma propriedade que não tem uma implementação padrão, mas deve ser implementada em qualquer tipo que implemente a interface:

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

Uma interface pode herdar de uma ou mais interfaces base. Quando uma interface [substitui um método](override.md) implementado em uma interface base, ele deve usar a sintaxe de [implementação de interface explícita.](../../programming-guide/interfaces/explicit-interface-implementation.md)

Quando uma lista de tipos base contém uma classe base e interfaces, a classe base deve vir em primeiro na lista.

Uma classe que implementa uma interface pode implementar membros dessa interface explicitamente. Um membro implementado explicitamente não pode ser acessado por meio de uma instância da classe, mas apenas por meio de uma instância da interface. Além disso, os membros de interface padrão só podem ser acessados através de uma instância da interface.

Para obter mais informações sobre a implementação explícita da interface, consulte [Implementação de interface explícita](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra a implementação da interface. Neste exemplo, a interface contém a declaração de propriedade e a classe contém a implementação. Qualquer instância de uma classe que implementa `IPoint` tem propriedades de inteiro `x` e `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [Interfaces](~/_csharplang/spec/interfaces.md) da especificação do [idioma C#](~/_csharplang/spec/introduction.md) e a especificação do recurso para [membros de interface Padrão - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tipos de referência](reference-types.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
- [Usando propriedades](../../programming-guide/classes-and-structs/using-properties.md)
- [Usando indexadores](../../programming-guide/indexers/using-indexers.md)
- [Interfaces](../../programming-guide/interfaces/index.md)
