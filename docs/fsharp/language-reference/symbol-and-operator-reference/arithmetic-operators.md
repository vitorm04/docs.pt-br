---
title: Operadores aritméticos (F#)
description: 'Saiba mais sobre os operadores aritméticos que estão disponíveis no F # linguagem de programação.'
author: cartermp
ms.author: phcart
ms.date: 04/04/2018
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 147600751ca8f991a7d5af24d1a63beb15ccab10
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="arithmetic-operators"></a>Operadores aritméticos

Este tópico descreve os operadores aritméticos que estão disponíveis na linguagem F #.

## <a name="summary-of-binary-arithmetic-operators"></a>Resumo de operadores aritméticos binários
A tabela a seguir resume os operadores aritméticos binários que estão disponíveis para tipos integrais e de ponto flutuantes não demarcados.

|Operador binário|Observações|
|---------------|-----|
|`+` (adição, além de)|Não verificado. Possível condição de estouro quando os números são adicionados juntos e a soma excede o valor absoluto máximo suportado pelo tipo.|
|`-` (subtração, sinal de subtração)|Não verificado. Quando são subtraídos tipos não assinados, ou quando valores de ponto flutuante são muito pequenos para ser representado pelo tipo de condição possível estouro.|
|`*` (multiplicação, horas)|Não verificado. Possível condição de estouro quando os números forem multiplicados e o produto excede o valor absoluto máximo suportado pelo tipo.|
|`/` (divisão, dividido pelo)|Divisão por zero faz com que um <xref:System.DivideByZeroException> para tipos integrais. Para tipos de ponto flutuantes, divisão por zero fornece os valores de ponto flutuantes especiais `+Infinity` ou `-Infinity`. Também há uma condição de estouro negativo possível quando um número de ponto flutuante é muito pequeno para ser representado pelo tipo.|
|`%` (restante, rem)|Retorna o resto de uma operação de divisão. O sinal do resultado é o mesmo que a entrada do primeiro operando.|
|`**` (exponenciação, a potência de)|Possível condição de estouro quando o resultado excede o máximo valor absoluto para o tipo.<br /><br />O operador de exponenciação só funciona com tipos de ponto flutuante.|

## <a name="summary-of-unary-arithmetic-operators"></a>Resumo de operadores aritméticos unários
A tabela a seguir resume os operadores aritméticos unários que estão disponíveis para tipos integrais e de ponto flutuantes.


|Operador unário|Observações|
|--------------|-----|
|`+` (positivo)|Podem ser aplicadas a qualquer expressão aritmética. Não alterar o sinal do valor.|
|`-` (negação, negativa)|Podem ser aplicadas a qualquer expressão aritmética. Altera o sinal do valor.|
É o comportamento no estouro ou estouro negativo para tipos integrais ao redor. Isso faz com que um resultado incorreto. Estouro de inteiro é um problema potencialmente grave que pode contribuir para problemas de segurança quando o software não é gravado para a conta para ele. Se isso for uma preocupação para seu aplicativo, considere o uso de operadores de verificação no `Microsoft.FSharp.Core.Operators.Checked`.


## <a name="summary-of-binary-comparison-operators"></a>Resumo de operadores de comparação binária
A tabela a seguir mostra os operadores de comparação binária que estão disponíveis para tipos integrais e de ponto flutuantes. Esses operadores retornam valores do tipo `bool`.

Números de ponto flutuante nunca devem ser comparados diretamente de igualdade, como a representação de ponto flutuante IEEE não oferece suporte a uma operação de igualdade exata. Dois números que você pode facilmente verificar para ser igual ao inspecionar o código, na verdade, podem ter representações de bits diferentes.



|Operador|Observações|
|--------|-----|
|`=` (igualdade, igual a)|Isso não é um operador de atribuição. Ele é usado apenas para comparação. Este é um operador genérico.|
|`>` (maior que)|Este é um operador genérico.|
|`<` (menor que)|Este é um operador genérico.|
|`>=` (maior que ou igual a)|Este é um operador genérico.|
|`<=` (menor que ou igual a)|Este é um operador genérico.|
|`<>` (não igual)|Este é um operador genérico.|

## <a name="overloaded-and-generic-operators"></a>Operadores sobrecarregados e genéricos
Todos os operadores discutidos neste tópico são definidos no **Microsoft.FSharp.Core.Operators** namespace. Alguns dos operadores são definidas usando os parâmetros de tipo resolvidos estaticamente. Isso significa que há definições individuais para cada tipo específico que funcione com esse operador. Todos os operadores aritméticos e bit a bit binários e unário estão nessa categoria. Os operadores de comparação são genéricos e, portanto, trabalhar com qualquer tipo, não apenas aritméticos primitivos. União discriminada e tipos de registro tem suas próprias implementações personalizadas que são geradas pelo compilador F #. Tipos de classe usam o método <xref:System.Object.Equals%2A>.

Os operadores genéricos são personalizáveis. Para personalizar as funções de comparação, substitua <xref:System.Object.Equals%2A> para fornecer seu próprio comparação de igualdade personalizado e, em seguida, implementar <xref:System.IComparable>. O <xref:System.IComparable?displayProperty=nameWithType> interface tem um único método, o <xref:System.IComparable.CompareTo%2A> método.


## <a name="operators-and-type-inference"></a>Inferência de tipos e operadores
O uso de um operador em uma expressão restringe a inferência de tipo nesse operador. Além disso, o uso de operadores impede generalização automática, porque o uso de operadores significa um tipo aritmético. Na ausência de qualquer outra informação, o compilador F # infere `int` como o tipo de expressões aritméticas. Você pode substituir esse comportamento especificando outro tipo. Assim, os tipos de argumento e tipo de retorno de `function1` no código a seguir são inferidos para ser `int`, mas os tipos de `function2` são inferidos para ser `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]
    
## <a name="see-also"></a>Consulte também
[Referência de Símbolos e Operadores](index.md)

[Sobrecarga de Operador](../operator-overloading.md)

[Operadores Bit a Bit](bitwise-operators.md)

[Operadores Boolianos](boolean-operators.md)
