---
title: Tipos de valor – Referência de C#
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 390b2226cc2f345d2f42659bd092e36a4bd0c4fc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632918"
---
# <a name="value-types-c-reference"></a>Tipos de valor (Referência de C#)

Há dois tipos de valor:

- [Estruturas](struct.md)

- [Enumerações](enum.md)

## <a name="main-features-of-value-types"></a>Principais recursos dos tipos de valor

Uma variável de um tipo de valor contém um valor do tipo. Por exemplo, uma variável do tipo `int` pode conter o valor `42`. Isso é diferente de uma variável de um tipo de referência, que contém uma referência a uma instância do tipo, também conhecida como um objeto. Quando você atribui um novo valor a uma variável de um tipo de valor, esse valor é copiado. Quando você atribui um novo valor a uma variável de um tipo de referência, a referência é copiada, não o objeto.

Todos os tipos de valor são derivados implicitamente da <xref:System.ValueType?displayProperty=nameWithType>.

Ao contrário do que acontece com tipos de referência, você não pode derivar um novo tipo de um tipo de valor. No entanto, assim como com tipos de referência, os structs podem implementar interfaces.

Variáveis de tipo de valor não podem ser `null` por padrão. No entanto, as variáveis dos [tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md) correspondentes podem ser `null`.

Cada tipo de valor tem um construtor sem parâmetro implícito que inicializa o valor padrão desse tipo. Para saber mais sobre valores padrão de tipos de valor, consulte [Tabela de valores padrão](default-values-table.md).

## <a name="simple-types"></a>Tipos simples

Os *tipos simples* são um conjunto de tipos de struct predefinidos fornecidos por C# e incluem os seguintes tipos:

- [Tipos integrais](integral-types-table.md): tipos numéricos inteiros e o tipo [char](char.md)
- [Tipos de ponto flutuante](floating-point-types-table.md)
- [bool](bool.md)

Os tipos simples são identificados por meio de palavras-chave, mas essas palavras-chave são simplesmente aliases para tipos de struct predefinidos no namespace <xref:System>. Por exemplo, [int](int.md) é um alias de <xref:System.Int32?displayProperty=nameWithType>. Para obter uma lista completa de aliases, consulte [Tabela de tipos internos](built-in-types-table.md).

Os tipos simples diferem de outros tipos de struct, pois permitem determinadas operações adicionais:

- Os tipos simples podem ser inicializados com o uso de literais. Por exemplo, `'A'` é um literal do tipo `char` e `2001` é um literal do tipo `int`.

- Você pode declarar constantes dos tipos simples com a palavra-chave [const](const.md). Não é possível ter constantes de outros tipos de struct.

- As expressões constantes, cujos operandos são todos constantes de tipo simples, são avaliadas em tempo de compilação.

Para saber mais, confira a seção [Tipos simples](~/_csharplang/spec/types.md#simple-types) na [Especificação da linguagem C#](../language-specification/index.md).

## <a name="initializing-value-types"></a>Inicializando tipos de valor

As variáveis locais no C# devem ser inicializadas antes de serem usadas. Por exemplo, você pode declarar uma variável local sem inicialização, como no exemplo a seguir:

```csharp
int myInt;
```

Você não pode usá-la antes de inicializá-la. Você pode inicializar a variável usando a instrução a seguir:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Essa instrução é equivalente à instrução a seguir:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

É claro que a declaração e a inicialização podem ser feitas na mesma instrução, como nos exemplos a seguir:

```csharp
int myInt = new int();
```

– ou –

```csharp
int myInt = 0;
```

Usando o operador [new](new.md), chama o construtor sem parâmetro do tipo específico e atribui o valor padrão à variável. No exemplo anterior, o construtor sem parâmetro atribuiu o valor `0` para `myInt`. Para obter mais informações sobre valores atribuídos ao chamar construtores padrão, consulte [Tabela de valores padrão](default-values-table.md).

Com tipos definidos pelo usuário, use [new](new.md) para invocar o construtor sem parâmetro. Por exemplo, a instrução a seguir invoca o construtor sem parâmetro do struct `Point`:

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

Após esta chamada, o struct é considerado para ser definitivamente atribuído, ou seja, todos os seus membros são inicializados com seus valores padrão.

Para saber mais sobre o operador `new`, confira [new](new.md).

Para saber mais sobre a formatação da saída de tipos numéricos, consulte [Tabela de formatação de resultados numéricos](formatting-numeric-results-table.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Tipos](types.md)
- [Tabelas de referência de tipos](reference-tables-for-types.md)
- [Tipos de referência](reference-types.md)
- [Tipos que permitem valor nulo](../../programming-guide/nullable-types/index.md)
