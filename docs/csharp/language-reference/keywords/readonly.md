---
title: Palavra-chave readonly – Referência de C#
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 6c48806e54f11bce930d03a53b010c337e6658f8
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960848"
---
# <a name="readonly-c-reference"></a>readonly (Referência de C#)

A palavra-chave `readonly` é um modificador que pode ser usado em quatro contextos:

- Em uma [declaração de campo](#readonly-field-example), `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor na mesma classe. Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor. 
  
  Um campo de `readonly` não pode ser atribuído depois que o construtor é encerrado. Essa regra tem implicações diferentes para tipos de valor e tipos de referência:
  
  - Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável. 
  - Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto. Esse objeto não é imutável. O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência. No entanto, o modificador não impede que os dados da instância do campo sejam modificados por meio do campo somente leitura.

  > [!WARNING]
  > Um tipo visível externamente que contém um campo somente leitura visível externamente, que é um tipo de referência mutável, pode ser uma vulnerabilidade de segurança e pode disparar o aviso [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Não declare tipos de referência mutáveis somente leitura".

- Em uma [definição `readonly struct`](#readonly-struct-example), `readonly` indica que o `struct` é imutável.
- Em uma [definição de membro`readonly`](#readonly-member-examples), `readonly` indica que um membro de um `struct` não modifica o estado interno da estrutura.
- Em um [retorno de método`ref readonly`](#ref-readonly-return-example), o modificador `readonly` indica que o método retorna uma referência e as gravações não são permitidas para essa referência.

Os contextos de `readonly sturct` e `ref readonly` foram adicionados C# em 7,2. `readonly` membros de struct foram adicionados C# em 8,0

## <a name="readonly-field-example"></a>Exemplo de campo readonly

Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, embora ele tenha sido atribuído a um valor no construtor da classe:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:

- Quando a variável é inicializada na declaração, por exemplo:

  ```csharp
  public readonly int y = 5;
  ```

- Em um construtor de instância da classe que contém a declaração de campo de instância.
- No construtor estático da classe que contém a declaração do campo estático.

Esses contextos de Construtor também são os únicos contextos em que é válido passar um campo de `readonly` como um parâmetro [out](out-parameter-modifier.md) ou [ref](ref.md) .

> [!NOTE]
> A palavra-chave `readonly` é diferente da palavra-chave [const](const.md). O campo `const` pode ser inicializado apenas na declaração do campo. Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor. Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado. Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:

```csharp
p2.y = 66;        // Error
```

Você obterá a mensagem de erro do compilador:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>Exemplo de struct readonly

O modificador `readonly` em uma definição `struct` declara que o struct é **imutável**. Cada campo da instância de `struct` precisa ser marcado como `readonly`, conforme é mostrado no exemplo a seguir:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

O exemplo anterior usa as [propriedades automáticas de readonly](../../properties.md#read-only) para declarar seu armazenamento. Isso instrui o compilador a criar campos de suporte `readonly` para essas propriedades. Você também pode declarar campos `readonly` diretamente:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Adicionar um campo não marcado como `readonly` gera o erro do compilador `CS8340`: "Os campos da instância de structs readonly devem ser readonly."

## <a name="readonly-member-examples"></a>Exemplos de membros ReadOnly

Em outras ocasiões, você pode criar uma estrutura que dá suporte a mutação. Nesses casos, vários dos membros da instância provavelmente não modificarão o estado interno da estrutura. Você pode declarar os membros da instância com o modificador de `readonly`. O compilador impõe sua intenção. Se esse membro modifica o estado diretamente ou acessa um membro que também não é declarado com o modificador de `readonly`, o resultado é um erro de tempo de compilação. O modificador de `readonly` é válido em Membros `struct`, não `class` ou `interface` declarações de membro.

Você tem duas vantagens aplicando o modificador de `readonly` aos métodos `struct` aplicáveis. O mais importante é que o compilador impõe sua intenção. O código que modifica o estado não é válido em um método `readonly`. O compilador também pode fazer uso do modificador de `readonly` para habilitar otimizações de desempenho. Quando grandes `struct` tipos são passados por `in` referência, o compilador deve gerar uma cópia defensiva se o estado da estrutura puder ser modificado. Se apenas `readonly` Membros forem acessados, o compilador poderá não criar a cópia defensiva.

O modificador de `readonly` é válido na maioria dos membros de um `struct`, incluindo métodos que substituem os métodos declarados em <xref:System.Object?displayProperty=nameWithType>. Há algumas restrições:

- Você não pode declarar `readonly` membros estáticos.
- Você não pode declarar construtores de `readonly`.

Você pode adicionar o modificador de `readonly` a uma propriedade ou declaração de indexador:

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

Você também pode adicionar o modificador de `readonly` a `get` individuais ou `set` acessadores de uma propriedade ou um indexador:

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

Você não pode adicionar o modificador `readonly` a uma propriedade e um ou mais dos acessadores da mesma propriedade. Essa mesma restrição se aplica a indexadores.

O compilador aplica implicitamente o modificador de `readonly` a propriedades implementadas automaticamente em que o código implementado pelo compilador não modifica o estado. É equivalente às seguintes declarações:

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

Você pode adicionar o modificador de `readonly` nesses locais, mas ele não terá nenhum efeito significativo. Você não pode adicionar o modificador `readonly` a um setter de propriedade autoimplementado ou a uma propriedade autoimplementada de leitura/gravação.

## <a name="ref-readonly-return-example"></a>Exemplo de retorno de readonly de ref

O modificador de `readonly` em um `ref return` indica que a referência retornada não pode ser modificada. O exemplo a seguir retorna uma referência para a origem. Ele usa o modificador `readonly` para indicar que os chamadores não podem modificar a origem:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
O tipo retornado não precisa ser um `readonly struct`. Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Você também pode ver as propostas de especificação de idioma:

- [struct de ref e ReadOnly ReadOnly](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [Membros de struct ReadOnly](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores](modifiers.md)
- [const](const.md)
- [Campos](../../programming-guide/classes-and-structs/fields.md)
