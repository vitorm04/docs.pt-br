---
title: Operadores aritméticos (F#)
description: 'Saiba mais sobre os operadores aritméticos que estão disponíveis na linguagem de programação F #.'
ms.date: 04/04/2018
ms.openlocfilehash: 008aa84b8736bb3a734ce8bb9713d34c17f1b76e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361953"
---
# <a name="arithmetic-operators"></a>Operadores aritméticos

Este tópico descreve os operadores aritméticos que estão disponíveis na linguagem F #.

## <a name="summary-of-binary-arithmetic-operators"></a>Resumo de operadores aritméticos binários

A tabela a seguir resume os operadores aritméticos binários que estão disponíveis para os tipos de ponto flutuante e integrais não demarcados.

|Operador binário|Observações|
|---------------|-----|
|`+` (adição, além de)|Não verificado. Possível condição de estouro quando os números são adicionados juntos e a soma excede o valor absoluto máximo com suporte pelo tipo.|
|`-` (subtração, sinal de subtração)|Não verificado. Quando tipos não assinados são subtraídos, ou quando valores de ponto flutuante são pequenos demais para ser representado pelo tipo de condição estouro negativo de possíveis.|
|`*` (multiplicação, vezes)|Não verificado. Possível condição de estouro quando os números são multiplicados e o produto excede o valor absoluto máximo com suporte pelo tipo.|
|`/` (divisão, dividido por)|Divisão por zero faz com que um <xref:System.DivideByZeroException> para tipos integrais. Para tipos de ponto flutuantes, divisão por zero lhe dá os valores de ponto flutuantes especiais `+Infinity` ou `-Infinity`. Também há uma condição de estouro negativo possível quando um número de ponto flutuante é muito pequeno para ser representado pelo tipo.|
|`%` (restante, rem)|Retorna o resto de uma operação de divisão. O sinal do resultado é o mesmo que o sinal do primeiro operando.|
|`**` (exponenciação, a potência de)|Possível condição de estouro quando o resultado excede o valor absoluto máximo para o tipo.<br /><br />O operador de exponenciação funciona apenas com tipos de ponto flutuante.|

## <a name="summary-of-unary-arithmetic-operators"></a>Resumo de operadores aritméticos unários

A tabela a seguir resume os operadores aritméticos unários que estão disponíveis para tipos integrais e de ponto flutuantes.

|Operador unário|Observações|
|--------------|-----|
|`+` (positivo)|Pode ser aplicado a qualquer expressão aritmética. Não altera o sinal do valor.|
|`-` (negação, negativa)|Pode ser aplicado a qualquer expressão aritmética. Altera o sinal do valor.|
É o comportamento em estouro ou estouro negativo para tipos integrais ao redor. Isso faz com que um resultado incorreto. Estouro de inteiro é um problema potencialmente grave que pode contribuir para problemas de segurança quando software não é gravado para levar em conta para ele. Se esta for uma preocupação para seu aplicativo, considere o uso de operadores verificados no `Microsoft.FSharp.Core.Operators.Checked`.

## <a name="summary-of-binary-comparison-operators"></a>Resumo de operadores de comparação binária

A tabela a seguir mostra os operadores de comparação binária que estão disponíveis para os tipos de ponto flutuante e integrais. Esses operadores retornam valores do tipo `bool`.

Números de ponto flutuante nunca devem ser comparados diretamente para igualdade, como a representação de ponto flutuante IEEE não oferece suporte a uma operação de igualdade exata. Dois números que você pode facilmente verificar para ser igual ao inspecionar o código, na verdade, podem ter representações de bits diferentes.

|Operador|Observações|
|--------|-----|
|`=` (igualdade, igual a)|Isso não é um operador de atribuição. Ele é usado somente para comparação. Este é um operador genérico.|
|`>` (maior que)|Este é um operador genérico.|
|`<` (menor que)|Este é um operador genérico.|
|`>=` (maior que ou igual a)|Este é um operador genérico.|
|`<=` (menor que ou igual a)|Este é um operador genérico.|
|`<>` (não igual)|Este é um operador genérico.|

## <a name="overloaded-and-generic-operators"></a>Operadores sobrecarregados e genéricos

Todos os operadores discutidos neste tópico são definidos na **Microsoft.FSharp.Core.Operators** namespace. Alguns dos operadores são definidos usando parâmetros de tipo estaticamente resolvidos. Isso significa que há definições individuais para cada tipo específico que funciona com o operador. Todos os operadores aritméticos e bit a bit binários e unários estão nesta categoria. Os operadores de comparação são genéricos e, portanto, trabalhe com qualquer tipo, não apenas primitivos tipos aritméticos. Tipos de registro e de união discriminada têm suas próprias implementações personalizadas que são geradas pelo compilador do F #. Tipos de classe usam o método <xref:System.Object.Equals%2A>.

Os operadores genéricos são personalizáveis. Para personalizar as funções de comparação, substitua <xref:System.Object.Equals%2A> para fornecer seu próprio comparação de igualdade personalizado e, em seguida, implementar <xref:System.IComparable>. O <xref:System.IComparable?displayProperty=nameWithType> interface tem um único método, o <xref:System.IComparable.CompareTo%2A> método.

## <a name="operators-and-type-inference"></a>Inferência de tipos e operadores

O uso de um operador em uma expressão restringe a inferência de tipos no operador. Além disso, o uso de operadores impede a generalização automática, pois o uso de operadores implica um tipo aritmético. Na ausência de qualquer outra informação, o compilador F # infere `int` como o tipo de expressões aritméticas. Você pode substituir esse comportamento especificando outro tipo. Portanto, os tipos de argumento e o tipo de retorno de `function1` no código a seguir são inferidos para ser `int`, mas os tipos para `function2` são inferidos ser `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Consulte também

- [Referência de Símbolos e Operadores](index.md)
- [Sobrecarga de Operador](../operator-overloading.md)
- [Operadores Bit a Bit](bitwise-operators.md)
- [Operadores Boolianos](boolean-operators.md)
