---
title: Operadores aritméticos
description: Saiba mais sobre os operadores aritméticos que estão disponíveis F# na linguagem de programação.
ms.date: 04/04/2018
ms.openlocfilehash: b783a0134541f11f06dde83af97676699b797da1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630786"
---
# <a name="arithmetic-operators"></a>Operadores aritméticos

Este tópico descreve os F# operadores aritméticos que estão disponíveis no idioma.

## <a name="summary-of-binary-arithmetic-operators"></a>Resumo de operadores aritméticos binários

A tabela a seguir resume os operadores aritméticos binários que estão disponíveis para tipos de ponto flutuante e inbox integral.

|Operador binário|Observações|
|---------------|-----|
|`+`(adição, mais)|Desmarcada. Possível condição de estouro quando os números são adicionados juntos e a soma excede o valor absoluto máximo com suporte do tipo.|
|`-`(subtração, menos)|Desmarcada. Possível condição de estouro quando tipos não assinados são subtraídos, ou quando valores de ponto flutuante são muito pequenos para serem representados pelo tipo.|
|`*`(multiplicação, vezes)|Desmarcada. Possível condição de estouro quando os números são multiplicados e o produto excede o valor absoluto máximo com suporte do tipo.|
|`/`(divisão, dividida por)|A divisão por zero causa <xref:System.DivideByZeroException> um para tipos integrais. Para tipos de ponto flutuante, divisão por zero fornece os valores `+Infinity` especiais de ponto flutuante ou. `-Infinity` Também há uma possível condição de estouro quando um número de ponto flutuante é muito pequeno para ser representado pelo tipo.|
|`%`(resto, REM)|Retorna o restante de uma operação de divisão. O sinal do resultado é o mesmo que o sinal do primeiro operando.|
|`**`(exponenciação, à potência de)|Possível condição de estouro quando o resultado excede o valor absoluto máximo para o tipo.<br /><br />O operador de exponenciação só funciona com tipos de ponto flutuante.|

## <a name="summary-of-unary-arithmetic-operators"></a>Resumo de operadores aritméticos unários

A tabela a seguir resume os operadores aritméticos unários que estão disponíveis para tipos de ponto flutuante e integral.

|Operador unário|Observações|
|--------------|-----|
|`+`negativo|Pode ser aplicado a qualquer expressão aritmética. Não altera o sinal do valor.|
|`-`(negação, negativo)|Pode ser aplicado a qualquer expressão aritmética. Altera o sinal do valor.|

O comportamento em estouro ou negativo para tipos integrais é encapsulado. Isso causa um resultado incorreto. O estouro de número inteiro é um problema potencialmente sério que pode contribuir com problemas de segurança quando o software não é gravado para se considerar. Se essa for uma preocupação para seu aplicativo, considere o uso dos operadores marcados `Microsoft.FSharp.Core.Operators.Checked`em.

## <a name="summary-of-binary-comparison-operators"></a>Resumo de operadores de comparação binária

A tabela a seguir mostra os operadores de comparação binária que estão disponíveis para tipos de ponto flutuante e integral. Esses operadores retornam valores do `bool`tipo.

Os números de ponto flutuante nunca devem ser diretamente comparados para igualdade, pois a representação de ponto flutuante de IEEE não oferece suporte a uma operação de igualdade exata. Dois números que você pode verificar facilmente são iguais ao inspecionar que o código pode realmente ter representações de bits diferentes.

|Operador|Observações|
|--------|-----|
|`=`(igualdade, igual a)|Este não é um operador de atribuição. Ele é usado somente para comparação. Esse é um operador genérico.|
|`>`(maior que)|Esse é um operador genérico.|
|`<`(menor que)|Esse é um operador genérico.|
|`>=`(maior que ou igual a)|Esse é um operador genérico.|
|`<=`(menor que ou igual a)|Esse é um operador genérico.|
|`<>`(diferente de)|Esse é um operador genérico.|

## <a name="overloaded-and-generic-operators"></a>Operadores sobrecarregados e genéricos

Todos os operadores abordados neste tópico são definidos no namespace **Microsoft. FSharp. Core. Operators** . Alguns dos operadores são definidos usando parâmetros de tipo resolvidos estaticamente. Isso significa que há definições individuais para cada tipo específico que funciona com esse operador. Todos os operadores unários e aritméticos binários e de bit-inteiro estão nessa categoria. Os operadores de comparação são genéricos e, portanto, funcionam com qualquer tipo, não apenas tipos aritméticos primitivos. Os F# tipos de união discriminada e de registro têm suas próprias implementações personalizadas que são geradas pelo compilador. Os tipos de classe usam <xref:System.Object.Equals%2A>o método.

Os operadores genéricos são personalizáveis. Para personalizar as funções de comparação, <xref:System.Object.Equals%2A> substitua para fornecer sua própria comparação de igualdade Personalizada e, <xref:System.IComparable>em seguida, implemente. A <xref:System.IComparable?displayProperty=nameWithType> interface tem um método único, o <xref:System.IComparable.CompareTo%2A> método.

## <a name="operators-and-type-inference"></a>Inferência de tipos e operadores

O uso de um operador em uma expressão restringe a inferência de tipos nesse operador. Além disso, o uso de operadores impede a generalização automática, porque o uso de operadores implica um tipo aritmético. Na ausência de qualquer outra informação, o F# compilador infere `int` como o tipo de expressões aritméticas. Você pode substituir esse comportamento especificando outro tipo. Assim, os tipos de argumento e o `function1` tipo de retorno do no código a seguir são `int`inferidos como sendo `function2` , mas os tipos de `float`são inferidos como.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Consulte também

- [Referência de Símbolos e Operadores](index.md)
- [Sobrecarga de Operador](../operator-overloading.md)
- [Operadores Bit a Bit](bitwise-operators.md)
- [Operadores Boolianos](boolean-operators.md)
