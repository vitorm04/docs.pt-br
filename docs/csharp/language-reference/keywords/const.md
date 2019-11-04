---
title: Palavra-chave const – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 81660e6a56efe5737600122d4ff7e182654f9a9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422890"
---
# <a name="const-c-reference"></a>const (Referência de C#)

Use a palavra-chave `const` para declarar um campo constante ou um local constante. Campos e locais constantes não são variáveis ​​e não podem ser modificados. As constantes podem ser números, valores boolianos, cadeias de caracteres ou uma referência nula. Não crie uma constante para representar informações que você espera mudar a qualquer momento. Por exemplo, não use um campo constante para armazenar o preço de um serviço, um número de versão de produto ou a marca de uma empresa. Esses valores podem mudar ao longo do tempo e como os compiladores propagam constantes, outro código compilado com as bibliotecas terá que ser recompilado para ver as alterações. Veja também a palavra-chave [readonly](./readonly.md). Por exemplo:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Comentários

O tipo de uma declaração constante especifica o tipo dos membros que a declaração apresenta. O inicializador de um local ou um campo constante deve ser uma expressão constante que pode ser implicitamente convertida para o tipo de destino.

Uma expressão constante é uma expressão que pode ser completamente avaliada em tempo de compilação. Portanto, os únicos valores possíveis para as constantes de tipos de referência são `string` e uma referência nula.

A declaração constante pode declarar constantes múltiplas como:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

O modificador `static` não é permitido em uma declaração constante.

A constante pode fazer parte de uma expressão constante, como a seguir:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> A palavra-chave [readonly](./readonly.md) é diferente da palavra-chave `const`. O campo `const` pode ser inicializado apenas na declaração do campo. Um campo `readonly` pode ser inicializado na declaração ou em um construtor. Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado. Além disso, embora um campo `const` seja uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como nesta linha: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Exemplo

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Exemplo

Este exemplo demonstra como usar constantes como variáveis ​​locais.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [Modificadores](index.md)
- [readonly](./readonly.md)
