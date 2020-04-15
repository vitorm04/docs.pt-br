---
title: Palavra-chave readonly – Referência de C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389052"
---
# <a name="readonly-c-reference"></a>readonly (Referência de C#)

A `readonly` palavra-chave é um modificador que pode ser usado em quatro contextos:

- Em uma [declaração de campo,](#readonly-field-example) `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor da mesma classe. Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.
  
  Um `readonly` campo não pode ser atribuído depois que o construtor sair. Esta regra tem diferentes implicações para tipos de valor e tipos de referência:
  
  - Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.
  - Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto. Esse objeto não é imutável. O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência. No entanto, o modificador não impede que os dados de ocorrência do campo sejam modificados através do campo somente leitura.

  > [!WARNING]
  > Um tipo externamente visível que contém um campo somente leitura externamente visível que seja um tipo de referência mutável pode ser uma vulnerabilidade de segurança e pode acionar o aviso [CA2104](/visualstudio/code-quality/ca2104) : "Não declare somente tipos de referência mutáveis".

- Em `readonly struct` uma definição `readonly` de tipo, indica que o tipo de estrutura é imutável. Para obter mais [ `readonly` ](../builtin-types/struct.md#readonly-struct) informações, consulte a seção de estrutura do artigo [Tipos de Estrutura.](../builtin-types/struct.md)
- Em uma declaração de membro `readonly` de instância dentro de um tipo de estrutura, indica que um membro de instância não modifica o estado da estrutura. Para obter mais [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) informações, consulte a seção de membros de instância do artigo [Tipos de Estrutura.](../builtin-types/struct.md)
- Em um [ `ref readonly` retorno do método,](#ref-readonly-return-example)o modificador indica que o `readonly` método retorna uma referência e as gravações não são permitidas a essa referência.

Os `readonly struct` `ref readonly` contextos foram adicionados em C# 7.2. `readonly`membros de estrutura foram adicionados em C # 8.0

## <a name="readonly-field-example"></a>Exemplo de campo readonly

Neste exemplo, o valor `year` do campo não pode `ChangeYear`ser alterado no método, mesmo que seja atribuído um valor no construtor de classe:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:

- Quando a variável é inicializada na declaração, por exemplo:

  ```csharp
  public readonly int y = 5;
  ```

- Em um construtor de instância da classe que contém a declaração de campo de instância.
- No construtor estático da classe que contém a declaração do campo estático.

Esses contextos construtores também são os únicos contextos em `readonly` que é válido passar um campo como um parâmetro [de saída](out-parameter-modifier.md) ou [ref.](ref.md)

> [!NOTE]
> A palavra-chave `readonly` é diferente da palavra-chave [const](const.md). O campo `const` pode ser inicializado apenas na declaração do campo. Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor. Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado. Além disso, `const` enquanto um campo é `readonly` uma constante de tempo de compilação, o campo pode ser usado para constantes de tempo de execução como no exemplo a seguir:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:

```csharp
p2.y = 66;        // Error
```

você receberá a mensagem de erro do compilador:

**Um campo somente leitura não pode ser atribuído (exceto em um construtor ou em um inicializador de variáveis)**

## <a name="ref-readonly-return-example"></a>Exemplo de retorno de readonly de ref

O `readonly` modificador `ref return` em um indica que a referência retornada não pode ser modificada. O exemplo a seguir retorna uma referência para a origem. Ele usa `readonly` o modificador para indicar que os chamadores não podem modificar a origem:

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

O tipo retornado não precisa ser um `readonly struct`. Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Você também pode ver as propostas de especificação do idioma:

- [readonly ref e readonly struct](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [lerapenas membros estrutura](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Palavras-chave](index.md)
- [Modificadores](index.md)
- [const](const.md)
- [Fields](../../programming-guide/classes-and-structs/fields.md)
