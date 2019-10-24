---
title: Conversões numéricas internas- C# referência
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776029"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Conversões numéricas internas (C# referência)

C#fornece um conjunto de tipos numéricos de [ponto flutuante](floating-point-numeric-types.md) e [integral](integral-numeric-types.md) . Existe uma conversão entre dois tipos numéricos, implícito ou explícito. Você deve usar o [operador cast `()`](../operators/type-testing-and-cast.md#cast-operator-) para invocar uma conversão explícita.

## <a name="implicit-numeric-conversions"></a>Conversões numéricas implícitas

A tabela a seguir mostra as conversões implícitas predefinidas entre os tipos numéricos internos:

|De|Para|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[short](integral-numeric-types.md)|`int`, `long`, `float`, `double` ou `decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[int](integral-numeric-types.md)|`long`, `float`, `double` ou `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double` ou `decimal`|
|[long](integral-numeric-types.md)|`float`, `double` ou `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double` ou `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> As conversões implícitas de `int`, `uint`, `long`ou `ulong` para `float` e de `long` ou `ulong` para `double` podem causar uma perda de precisão, mas nunca uma perda de uma ordem de magnitude. As outras conversões numéricas implícitas nunca perdem nenhuma informação.

Observe também que

- Qualquer [tipo numérico integral](integral-numeric-types.md) é implicitamente conversível em qualquer [tipo numérico de ponto flutuante](floating-point-numeric-types.md).

- Não há conversões implícitas para os tipos `byte` e `sbyte`. Não há nenhuma conversão implícita dos tipos `double` e `decimal`.

- Não há nenhuma conversão implícita entre os tipos `decimal` e `float` ou os tipos `double`.

- Um valor de uma expressão constante do tipo `int` (por exemplo, um valor representado por um literal inteiro) pode ser convertido implicitamente em `sbyte`, `byte`, `short`, `ushort`, `uint`ou `ulong`, se estiver dentro do intervalo do tipo de destino :

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Como mostra o exemplo anterior, se o valor da constante não estiver dentro do intervalo do tipo de destino, ocorrerá um erro de compilador [CS0031](../../misc/cs0031.md) .

## <a name="explicit-numeric-conversions"></a>Conversões numéricas explícitas

A tabela a seguir mostra as conversões explícitas predefinidas entre os tipos numéricos internos para os quais não há [conversão implícita](#implicit-numeric-conversions):

|De|Para|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint` ou `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint` ou `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte` ou `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` ou `int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` ou `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`ou `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float` ou `double`|

> [!NOTE]
> Uma conversão numérica explícita pode resultar em perda de dados ou gerar uma exceção, normalmente uma <xref:System.OverflowException>.

Observe também que

- Quando você converte um valor de um tipo integral em outro tipo integral, o resultado depende do [contexto de verificação](../keywords/checked-and-unchecked.md) do estouro. Em um contexto verificado, a conversão terá êxito se o valor de origem estiver dentro do intervalo do tipo de destino. Caso contrário, um <xref:System.OverflowException> será gerado. Em um contexto não verificado, a conversão sempre terá êxito e procederá da seguinte maneira:

  - Se o tipo de origem for maior do que o tipo de destino, então o valor de origem será truncado descartando seus bits "extra" mais significativos. O resultado é então tratado como um valor do tipo de destino.

  - Se o tipo de origem for menor que o tipo de destino, o valor de origem será estendido ou estendido em zero para que seja do mesmo tamanho que o tipo de destino. A extensão por sinal será usada se o tipo de origem tiver sinal; a extensão por zero será usada se o tipo de origem não tiver sinal. O resultado é então tratado como um valor do tipo de destino.

  - Se o tipo de origem tiver o mesmo tamanho que o tipo de destino, então o valor de origem será tratado como um valor do tipo de destino.

- Ao converter um valor `decimal` para um tipo integral, esse valor será arredondado para zero, para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, uma <xref:System.OverflowException> será lançada.

- Ao converter um valor `double` ou `float` em um tipo integral, esse valor será arredondado em direção a zero para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, o resultado dependerá do [contexto de verificação](../keywords/checked-and-unchecked.md) de estouro. Em um contexto verificado, uma <xref:System.OverflowException> será lançada, ao passo que em um contexto não verificado, o resultado será um valor não especificado do tipo de destino.

- Ao converter `double` para `float`, o valor `double` será arredondado para o valor `float` mais próximo. Se o valor de `double` for muito pequeno ou muito grande para caber no tipo de `float`, o resultado será zero ou infinito.

- Ao converter `float` ou `double` para `decimal`, o valor de origem será convertido para uma representação `decimal` e arredondado para o número mais próximo após a 28ª casa decimal, se necessário. De acordo com o valor do valor de origem, um dos resultados a seguir podem ocorrer:

  - Se o valor de origem for muito pequeno para ser representado como um `decimal`, o resultado será zero.

  - Se o valor de origem for um NaN (não for um número), infinito ou muito grande para ser representado como um `decimal`, uma <xref:System.OverflowException> será lançada.

- Quando você converte `decimal` em `float` ou `double`, o valor de origem é arredondado para o valor mais próximo `float` ou `double`, respectivamente.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Conversões numéricas implícitas](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Conversões numéricas explícitas](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Conversão e conversões de tipo](../../programming-guide/types/casting-and-type-conversions.md)
