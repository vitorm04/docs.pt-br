---
title: Tipos de valor anulável - Visual Basic
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
ms.openlocfilehash: 46564d2c509fe2b53b9662ee441ab8b85fccc693
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642129"
---
# <a name="nullable-value-types-visual-basic"></a>Tipos de valor que permitem valor nulo (Visual Basic)

Às vezes, você trabalha com um tipo de valor que não tem um valor definido em determinadas circunstâncias. Por exemplo, um campo em um banco de dados pode ter que distinguir entre ter um valor atribuído que seja significativo e não ter um valor atribuído. Tipos de valor podem ser estendidos para levar seus valores de normais ou um valor nulo. Uma extensão desse tipo é chamada um *tipo anulável*.

Cada tipo anulável é construído a partir genérica <xref:System.Nullable%601> estrutura. Considere um banco de dados que rastreia atividades relacionadas ao trabalho. O exemplo a seguir constrói um valor anulável `Boolean` e declara uma variável desse tipo. Você pode escrever a declaração de três maneiras:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

A variável `ridesBusToWork` pode conter um valor de `True`, um valor de `False`, ou nenhum valor. Seu valor inicial padrão não é nenhum valor, que nesse caso, pode significar que as informações ainda não foi obtidas para essa pessoa. Em contraste, `False` pode significar que a informação foi obtida e a pessoa não pretendem ir de ônibus para o trabalho.

Você pode declarar variáveis e propriedades com tipos anuláveis, e você pode declarar uma matriz com elementos de um tipo anulável. Você pode declarar procedimentos com tipos anuláveis como parâmetros, e você pode retornar um tipo anulável de um `Function` procedimento.

Não é possível construir um tipo anulável em um tipo de referência como uma matriz, um `String`, ou uma classe. O tipo subjacente deve ser um tipo de valor. Para obter mais informações, consulte [tipos de valor e tipos de referência](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Usando uma variável de tipo anulável

Os membros mais importantes de um tipo anulável são suas <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> propriedades. Para uma variável de um tipo anulável, <xref:System.Nullable%601.HasValue%2A> informa se a variável contém um valor definido. Se <xref:System.Nullable%601.HasValue%2A> está `True`, você pode ler o valor de <xref:System.Nullable%601.Value%2A>. Observe que ambos <xref:System.Nullable%601.HasValue%2A> e <xref:System.Nullable%601.Value%2A> são `ReadOnly` propriedades.

### <a name="default-values"></a>Valores padrão

Quando você declara uma variável com um tipo anulável, sua <xref:System.Nullable%601.HasValue%2A> propriedade tem um valor padrão de `False`. Isso significa que, por padrão, a variável não tem nenhum valor definido, em vez do valor padrão de seu tipo de valor subjacente. No exemplo a seguir, a variável `numberOfChildren` inicialmente não tem valor definido, mesmo que o valor padrão de `Integer` tipo é 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Um valor nulo é útil para indicar um valor desconhecido ou indefinido. Se `numberOfChildren` tivesse sido declarado como `Integer`, não haveria nenhum valor que pode indicar que as informações não estão disponíveis no momento.

### <a name="storing-values"></a>Armazenando valores

Você pode armazenar um valor em uma variável ou propriedade de um tipo que permite valor nulo em uma forma comum de. O exemplo a seguir atribui um valor à variável `numberOfChildren` declarada no exemplo anterior.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Se uma variável ou propriedade de um tipo anulável contiver um valor definido, você poderá revertê-la para seu estado inicial de não ter um valor atribuído. Você pode fazer isso definindo a variável ou propriedade a ser `Nothing`, como mostra o exemplo a seguir.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Embora você possa atribuir `Nothing` a uma variável de um tipo anulável, você não é possível testá-lo para `Nothing` usando o sinal de igual. Comparação que usa o sinal de igual `someVar = Nothing`, sempre é avaliada como `Nothing`. Você pode testar a variável <xref:System.Nullable%601.HasValue%2A> propriedade para `False`, ou de teste usando o `Is` ou `IsNot` operador.

### <a name="retrieving-values"></a>Recuperando valores

Para recuperar o valor de uma variável de um tipo anulável, primeiro você deve testar seu <xref:System.Nullable%601.HasValue%2A> propriedade para confirmar se ele tem um valor. Se você tentar ler o valor quando <xref:System.Nullable%601.HasValue%2A> está `False`, Visual Basic gera um <xref:System.InvalidOperationException> exceção. O exemplo a seguir mostra a maneira recomendada para ler a variável `numberOfChildren` dos exemplos anteriores.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Comparando tipos anuláveis

Quando for anulável `Boolean` as variáveis são usadas em expressões booleanas, o resultado pode ser `True`, `False`, ou `Nothing`. A seguir está a tabela de verdade para `And` e `Or`. Porque `b1` e `b2` agora tem três valores possíveis, existem nove combinações para avaliar.

|b1|b2|B1 e b2|B1 ou b2|
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

Quando o valor de uma variável ou expressão booleana for `Nothing`, ele não é nem `true` nem `false`. Considere o exemplo a seguir.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

Neste exemplo, `b1 And b2` for avaliada como `Nothing`. Como resultado, o `Else` cláusula é executada em cada `If` instrução e a saída é da seguinte maneira:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` e `OrElse`, que usam curto-circuito avaliação, deve avaliar seus operandos segundo quando o primeiro é avaliada como `Nothing`.

## <a name="propagation"></a>Propagação

Se um ou ambos os operandos de uma aritmética, comparação, shift ou operação de tipo for anulável, o resultado da operação também é anulável. Se os dois operandos tiverem valores que não são `Nothing`, a operação é executada nos valores subjacentes dos operandos, como se nenhum deles fosse um tipo anulável. No exemplo a seguir, as variáveis `compare1` e `sum1` são de tipo implícito. Se você posicionar o ponteiro do mouse sobre eles, você verá que o compilador infere os tipos que permitem valor nulos para os dois.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Se um ou ambos os operandos têm um valor de `Nothing`, o resultado será `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Usando tipos anuláveis com dados

Um banco de dados é um dos locais mais importantes para usar tipos anuláveis. Nem todos os objetos de banco de dados atualmente dão suporte a tipos anuláveis, mas os adaptadores de tabelas gerado pelo designer. Ver [suporte do TableAdapter para tipos anuláveis](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Consulte também

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Usando tipos que permitem valor nulo](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Tipos de Dados](index.md)
- [Tipos de Valor e Tipos de Referência](value-types-and-reference-types.md)
- [Solução de problemas de Tipos de Dados](troubleshooting-data-types.md)
- [Preencher conjuntos de dados usando TableAdapters](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [Operador If](../../../language-reference/operators/if-operator.md)
- [Inferência de Tipo de Variável Local](../variables/local-type-inference.md)
- [Operador Is](../../../language-reference/operators/is-operator.md)
- [Operador IsNot](../../../language-reference/operators/isnot-operator.md)
