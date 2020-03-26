---
title: Valores padrão dos tipos C# - Referência C#
description: Aprenda os valores padrão dos tipos C# como bool, char, int, float, double and more.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507250"
---
# <a name="default-values-of-c-types-c-reference"></a>Valores padrão dos tipos C# (referência C#)

A seguinte tabela mostra os valores padrão de tipos C#:

|Type|Valor padrão|
|---------|------------------|
|Qualquer tipo de referência|`null`|
|Qualquer [tipo numérico integral interno](integral-numeric-types.md)|0 (zero)|
|Qualquer [tipo numérico de ponto flutuante interno](floating-point-numeric-types.md)|0 (zero)|
|[Bool](bool.md)|`false`|
|[Char](char.md)|`'\0'` (U+0000)|
|[Enum](enum.md)|O valor é produzido pela expressão `(E)0`, em que `E` é o identificador de enumeração.|
|[struct](struct.md)|O valor produzido pela configuração de todos os campos tipo-valor para seus valores padrão e todos os campos tipo-referência para `null`.|
|Qualquer [tipo de valor que permite valor nulo](nullable-value-types.md)|Uma instância para a qual a propriedade <xref:System.Nullable%601.HasValue%2A> é `false` e a propriedade <xref:System.Nullable%601.Value%2A> não está definida. Esse valor padrão também é conhecido como o valor *nulo* de um tipo de valor anulado.|

Use [ `default` ](../operators/default.md#default-operator) o operador para produzir o valor padrão de um tipo, como mostra o exemplo a seguir:

```csharp
int a = default(int);
```

Começando com C# 7.1, [ `default` ](../operators/default.md#default-literal) você pode usar o literal para inicializar uma variável com o valor padrão do seu tipo:

```csharp
int a = default;
```

Para um tipo de valor, o construtor implícito sem parâmetros também produz o valor padrão do tipo, como mostra o seguinte exemplo:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

No tempo de <xref:System.Type?displayProperty=nameWithType> execução, se a instância representar <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> um tipo de valor, você pode usar o método para invocar o construtor sem parâmetros para obter o valor padrão do tipo.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Valores padrão](~/_csharplang/spec/variables.md#default-values)
- [Construtores padrão](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Construtores](../../programming-guide/classes-and-structs/constructors.md)
