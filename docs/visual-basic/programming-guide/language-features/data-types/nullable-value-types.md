---
title: Tipos de valor que permitem valor nulo
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249676"
---
# <a name="nullable-value-types-visual-basic"></a>Tipos de valor que permitem valor nulo (Visual Basic)

Às vezes você trabalha com um tipo de valor que não tem um valor definido em certas circunstâncias. Por exemplo, um campo em um banco de dados pode ter que distinguir entre ter um valor atribuído que seja significativo e não ter um valor atribuído. Os tipos de valor podem ser estendidos para levar seus valores normais ou um valor nulo. Tal extensão é chamada de *tipo nulo.*

Cada tipo de valor anulado é <xref:System.Nullable%601> construído a partir da estrutura genérica. Considere um banco de dados que rastreie atividades relacionadas ao trabalho. O exemplo a seguir `Boolean` constrói um tipo anulado e declara uma variável desse tipo. Você pode escrever a declaração de três maneiras:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

A `ridesBusToWork` variável pode conter `True`um valor `False`de , um valor de , ou nenhum valor em tudo. Seu valor inicial de inadimplência não é nenhum valor, o que neste caso pode significar que as informações ainda não foram obtidas para essa pessoa. Em contrapartida, `False` pode significar que as informações foram obtidas e a pessoa não anda de ônibus para o trabalho.

Você pode declarar variáveis e propriedades com tipos de valor anulados, e você pode declarar uma matriz com elementos de um tipo de valor anulado. Você pode declarar procedimentos com tipos de valor anulados como parâmetros, e você pode retornar um tipo de valor anulado de um `Function` procedimento.

Você não pode construir um tipo anulado em um `String`tipo de referência, como uma matriz, a ou uma classe. O tipo subjacente deve ser um tipo de valor. Para obter mais informações, consulte [Tipos de valor e tipos de referência](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Usando uma variável de tipo anulado

Os membros mais importantes de um <xref:System.Nullable%601.HasValue%2A> tipo <xref:System.Nullable%601.Value%2A> de valor anulado são suas propriedades. Para uma variável de um <xref:System.Nullable%601.HasValue%2A> tipo de valor anulado, informa se a variável contém um valor definido. Se <xref:System.Nullable%601.HasValue%2A> `True`for, você pode <xref:System.Nullable%601.Value%2A>ler o valor de . Note que <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> ambos `ReadOnly` e são propriedades.

### <a name="default-values"></a>Valores padrão

Quando você declara uma variável com um <xref:System.Nullable%601.HasValue%2A> tipo de valor `False`anulado, sua propriedade tem um valor padrão de . Isso significa que, por padrão, a variável não tem valor definido, em vez do valor padrão de seu tipo de valor subjacente. No exemplo a seguir, a variável `numberOfChildren` inicialmente não tem `Integer` valor definido, embora o valor padrão do tipo seja 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Um valor nulo é útil para indicar um valor indefinido ou desconhecido. Se `numberOfChildren` tivesse sido `Integer`declarado como , não haveria valor que poderia indicar que as informações não estão disponíveis no momento.

### <a name="storing-values"></a>Armazenamento de valores

Você armazena um valor em uma variável ou propriedade de um tipo de valor anulado da maneira típica. O exemplo a seguir atribui `numberOfChildren` um valor à variável declarada no exemplo anterior.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Se uma variável ou propriedade de um tipo de valor anulado contiver um valor definido, você pode fazê-lo reverter ao seu estado inicial de não ter um valor atribuído. Você faz isso definindo a `Nothing`variável ou propriedade para , como mostra o exemplo a seguir.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Embora você possa `Nothing` atribuir a uma variável de um tipo `Nothing` de valor anulado, você não pode testá-lo usando o sinal de igual. Comparação que usa o `someVar = Nothing`sinal de `Nothing`igual, sempre avalia para . Você pode testar a <xref:System.Nullable%601.HasValue%2A> propriedade `False`da variável para `Is` `IsNot` , ou testar usando o ou operador.

### <a name="retrieving-values"></a>Recuperando valores

Para recuperar o valor de uma variável de um tipo <xref:System.Nullable%601.HasValue%2A> de valor anulado, você deve primeiro testar sua propriedade para confirmar que ela tem um valor. Se você tentar ler <xref:System.Nullable%601.HasValue%2A> o `False`valor quando <xref:System.InvalidOperationException> é , Visual Basic lança uma exceção. O exemplo a seguir mostra a `numberOfChildren` maneira recomendada de ler a variável dos exemplos anteriores.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Comparando tipos anulados

Quando `Boolean` variáveis anuladas são usadas em expressões booleanas, o resultado pode ser `True`, `False`ou `Nothing`. A seguir está a `And` `Or`tabela da verdade para e . Porque `b1` `b2` e agora tem três valores possíveis, há nove combinações para avaliar.

|b1|B2|b1 E b2|b1 ou b2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

Quando o valor de uma variável `Nothing`ou expressão `true` `false`booleana é, não é nem nem . Considere o exemplo a seguir.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Neste exemplo, `b1 And b2` avalia-se para `Nothing`. Como resultado, `Else` a cláusula é `If` executada em cada declaração, e a saída é a seguinte:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`e `OrElse`, que utilizam avaliação de curto-circuito, devem avaliar seus `Nothing`segundo operadores quando o primeiro avaliar para .

## <a name="propagation"></a>Propagação

Se um ou ambos os operands de uma operação aritmética, comparação, turno ou tipo for um tipo de valor anulado, o resultado da operação também é um tipo de valor anulado. Se ambos os operands `Nothing`tiverem valores que não são, a operação é realizada nos valores subjacentes dos operands, como se nenhum deles fosse um tipo de valor anulado. No exemplo a seguir, variáveis `compare1` e `sum1` são digitadas implicitamente. Se você descansar o ponteiro do mouse sobre eles, você verá que o compilador infere tipos de valor anulados para ambos.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Se um ou ambos os operands tiverem um valor de `Nothing`, o resultado será `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Usando tipos anulados com dados

Um banco de dados é um dos lugares mais importantes para usar tipos de valor anulados. Nem todos os objetos de banco de dados suportam atualmente tipos de valor anulados, mas os adaptadores de tabela gerados pelo designer suportam. Consulte [o suporte tableAdapter para tipos anulados](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Confira também

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Tipos de dados](index.md)
- [Tipos de valor e tipos de referência](value-types-and-reference-types.md)
- [Solução de problemas de tipos de dados](troubleshooting-data-types.md)
- [Preencher conjuntos de dados usando TableAdapters](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [Operador If](../../../language-reference/operators/if-operator.md)
- [Inferência de Tipo de Variável Local](../variables/local-type-inference.md)
- [Operador Is](../../../language-reference/operators/is-operator.md)
- [Operador IsNot](../../../language-reference/operators/isnot-operator.md)
- [Tipos de valor anulados (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
