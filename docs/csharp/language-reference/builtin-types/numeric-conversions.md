---
title: Conversões numéricas incorporadas - referência C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: b7d53e508e4d585c746a3cc61824cdace7707deb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121459"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Conversões numéricas incorporadas (referência C#)

C# fornece um conjunto de tipos numéricos [integrais](integral-numeric-types.md) e [de ponto flutuante.](floating-point-numeric-types.md) Existe uma conversão entre dois tipos numéricos, implícitos ou explícitos. Você deve usar uma [expressão de elenco](../operators/type-testing-and-cast.md#cast-expression) para realizar uma conversão explícita.

## <a name="implicit-numeric-conversions"></a>Conversões numéricas implícitas

A tabela a seguir mostra as conversões implícitas predefinidas entre os tipos numéricos incorporados:

|De|Para|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` ou `decimal`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[Curto](integral-numeric-types.md)|`int`, `long`, `float`, `double` ou `decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` ou `decimal`|
|[INT](integral-numeric-types.md)|`long`, `float`, `double` ou `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double` ou `decimal`|
|[Longas](integral-numeric-types.md)|`float`, `double` ou `decimal`|
|[Ulong](integral-numeric-types.md)|`float`, `double` ou `decimal`|
|[FLOAT](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> As conversões `int`implícitas `long`de `ulong` `float` , `uint` `long` , ou de e para ou para ou `ulong` para `double` pode causar uma perda de precisão, mas nunca uma perda de uma ordem de magnitude. As outras conversões numéricas implícitas nunca perdem qualquer informação.

Note também que

- Qualquer [tipo numérico integral](integral-numeric-types.md) é implicitamente conversível para qualquer tipo [numérico de ponto flutuante](floating-point-numeric-types.md).

- Não há conversões implícitas `sbyte` para os e tipos. `byte` Não há nenhuma conversão implícita dos tipos `double` e `decimal`.

- Não há nenhuma conversão implícita entre os tipos `decimal` e `float` ou os tipos `double`.

- Um valor de uma `int` expressão constante de tipo (por exemplo, um valor representado por `sbyte` `byte`um `short` `ushort`inteiro `uint`literal) pode ser implicitamente convertido para, , , , ou `ulong`, se estiver dentro do intervalo do tipo de destino:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Como o exemplo anterior mostra, se o valor constante não estiver dentro do intervalo do tipo de destino, ocorrerá um erro de compilador [CS0031.](../../misc/cs0031.md)

## <a name="explicit-numeric-conversions"></a>Conversões numéricas explícitas

A tabela a seguir mostra as conversões explícitas predefinidas entre os tipos numéricos incorporados para os quais não há [conversão implícita](#implicit-numeric-conversions):

|De|Para|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint` ou `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[Curto](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint` ou `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte` ou `short`|
|[INT](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint` ou `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` ou `int`|
|[Longas](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `ulong`|
|[Ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` ou `long`|
|[FLOAT](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` ou `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , ou`decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `float`, , , , ou`double`|

> [!NOTE]
> Uma conversão numérica explícita pode resultar em perda de dados <xref:System.OverflowException>ou lançar uma exceção, tipicamente uma .

Note também que

- Quando você converte um valor de um tipo integral em outro tipo integral, o resultado depende do [contexto de verificação](../keywords/checked-and-unchecked.md) do estouro. Em um contexto verificado, a conversão terá êxito se o valor de origem estiver dentro do intervalo do tipo de destino. Caso contrário, um <xref:System.OverflowException> será gerado. Em um contexto não verificado, a conversão sempre terá êxito e procederá da seguinte maneira:

  - Se o tipo de origem for maior do que o tipo de destino, então o valor de origem será truncado descartando seus bits "extra" mais significativos. O resultado é então tratado como um valor do tipo de destino.

  - Se o tipo de origem for menor do que o tipo de destino, então o valor de origem será estendido ou zero estendido para que seja do mesmo tamanho do tipo de destino. A extensão por sinal será usada se o tipo de origem tiver sinal; a extensão por zero será usada se o tipo de origem não tiver sinal. O resultado é então tratado como um valor do tipo de destino.

  - Se o tipo de origem tiver o mesmo tamanho que o tipo de destino, então o valor de origem será tratado como um valor do tipo de destino.

- Ao converter um valor `decimal` para um tipo integral, esse valor será arredondado para zero, para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, uma <xref:System.OverflowException> será lançada.

- Ao converter um valor `double` ou `float` em um tipo integral, esse valor será arredondado em direção a zero para o valor integral mais próximo. Se o valor integral resultante estiver fora do intervalo do tipo de destino, o resultado dependerá do [contexto de verificação](../keywords/checked-and-unchecked.md) de estouro. Em um contexto verificado, uma <xref:System.OverflowException> será lançada, ao passo que em um contexto não verificado, o resultado será um valor não especificado do tipo de destino.

- Ao converter `double` para `float`, o valor `double` será arredondado para o valor `float` mais próximo. Se `double` o valor for muito pequeno ou muito `float` grande para se encaixar no tipo, o resultado é zero ou infinito.

- Ao converter `float` ou `double` para `decimal`, o valor de origem será convertido para uma representação `decimal` e arredondado para o número mais próximo após a 28ª casa decimal, se necessário. De acordo com o valor do valor de origem, um dos resultados a seguir podem ocorrer:

  - Se o valor de origem for muito pequeno para ser representado como um `decimal`, o resultado será zero.

  - Se o valor de origem for um NaN (não for um número), infinito ou muito grande para ser representado como um `decimal`, uma <xref:System.OverflowException> será lançada.

- Quando você `decimal` `float` converte para ou `double`, o valor `float` `double` de origem é arredondado para o mais próximo ou valor, respectivamente.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Conversões numéricas implícitas](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Conversões numéricas explícitas](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Conversão de fundição e tipo](../../programming-guide/types/casting-and-type-conversions.md)
