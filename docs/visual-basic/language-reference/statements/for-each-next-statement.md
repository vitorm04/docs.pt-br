---
title: Instrução For Each...Next
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: 572f1efc0148bd8df4f13fa5651e74249caa45a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351203"
---
# <a name="for-eachnext-statement-visual-basic"></a>Instrução For Each...Next (Visual Basic)

Repete um grupo de instruções para cada elemento em uma coleção.

## <a name="syntax"></a>Sintaxe

```vb
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|`element`|Necessário na instrução `For Each`. Opcional na instrução `Next`. Ela. Usado para iterar pelos elementos da coleção.|
|`datatype`|Opcional se [`Option Infer`](option-infer-statement.md) estiver on (o padrão) ou `element` já estiver declarado; obrigatório se `Option Infer` estiver desativado e `element` já não estiver declarado. O tipo de dados de `element`.|
|`group`|Necessária. Uma variável com um tipo que é um tipo de coleção ou objeto. Refere-se à coleção sobre a qual os `statements` devem ser repetidos.|
|`statements`|Opcional. Uma ou mais instruções entre `For Each` e `Next` que são executadas em cada item em `group`.|
|`Continue For`|Opcional. Transfere o controle para o início do loop de `For Each`.|
|`Exit For`|Opcional. Transfere o controle do loop de `For Each`.|
|`Next`|Necessária. Encerra a definição do loop de `For Each`.|

## <a name="simple-example"></a>Exemplo simples

Use um loop `For Each`...`Next` quando você quiser repetir um conjunto de instruções para cada elemento de uma coleção ou matriz.

> [!TIP]
> Um [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) funciona bem quando você pode associar cada iteração de um loop a uma variável de controle e determinar os valores iniciais e finais da variável. No entanto, quando você está lidando com uma coleção, o conceito de valores iniciais e finais não é significativo e você não sabe necessariamente quantos elementos a coleção tem. Nesse tipo de caso, um loop `For Each`...`Next` é geralmente uma opção melhor.

No exemplo a seguir, a `For Each`...`Next` a instrução faz a iteração por todos os elementos de uma coleção de lista.

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

Para obter mais exemplos, consulte [coleções](../../../standard/collections/index.md) e [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).

## <a name="nested-loops"></a>Loops aninhados

Você pode aninhar loops de `For Each` colocando um loop dentro de outro.

O exemplo a seguir demonstra `For Each`aninhados...`Next` Estruturas.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

Quando você Aninha loops, cada loop deve ter uma variável de `element` exclusiva.

Você também pode aninhar diferentes tipos de estruturas de controle entre si. Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Sair para e continuar para

A instrução [Exit for](../../../visual-basic/language-reference/statements/exit-statement.md) faz com que a execução saia do `For`...`Next` loop e transfere o controle para a instrução que segue a instrução `Next`.

A instrução `Continue For` transfere o controle imediatamente para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).

O exemplo a seguir mostra como usar as instruções `Continue For` e `Exit For`.

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

Você pode colocar qualquer número de instruções `Exit For` em um loop `For Each`. Quando usado em loops de `For Each` aninhados, `Exit For` faz com que a execução saia do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.

`Exit For` geralmente é usado após uma avaliação de alguma condição, por exemplo, em uma estrutura `If`...`Then`...`Else`. Talvez você queira usar `Exit For` para as seguintes condições:

- Continuar a iterar é desnecessário ou impossível. Isso pode ser causado por um valor errado ou uma solicitação de encerramento.

- Uma exceção é capturada em um `Try`...`Catch`...`Finally`. Você pode usar `Exit For` no final do bloco de `Finally`.

- Há um loop infinito, que é um loop que poderia executar um número grande ou uniforme de vezes infinito. Se você detectar essa condição, poderá usar `Exit For` para escapar do loop. Para obter mais informações, consulte [do... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="iterators"></a>{1&gt;Iteradores&lt;1}

Você usa um *iterador* para executar uma iteração personalizada em uma coleção. Um iterador pode ser uma função ou um acessador `Get`. Ele usa uma instrução `Yield` para retornar cada elemento da coleção um de cada vez.

Você chama um iterador usando uma instrução `For Each...Next`. Cada iteração do loop `For Each` chama o iterador. Quando uma instrução `Yield` é atingida no iterador, a expressão na instrução `Yield` é retornada e o local atual no código é retido. A execução será reiniciada desse local na próxima vez que o iterador for chamado.

O exemplo a seguir usa uma função de iterador. A função Iterator tem uma instrução `Yield` que está dentro de um [para... Próximo](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. No método `ListEvenNumbers`, cada iteração do corpo da instrução `For Each` cria uma chamada para a função Iterator, que prossegue para a próxima instrução `Yield`.

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

Para obter mais informações, consulte [iteradores](../../programming-guide/concepts/iterators.md), [instrução yield](../../../visual-basic/language-reference/statements/yield-statement.md)e [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).

## <a name="technical-implementation"></a>Implementação técnica

Quando um `For Each`...`Next` a instrução é executada, Visual Basic avalia a coleção somente uma vez, antes de o loop ser iniciado. Se a instrução bloquear alterações `element` ou `group`, essas alterações não afetarão a iteração do loop.

Quando todos os elementos na coleção tiverem sido atribuídos sucessivamente a `element`, o loop `For Each` será interrompido e o controle passará para a instrução após a instrução `Next`.

Se [Option Infer](option-infer-statement.md) estiver on (sua configuração padrão), o compilador Visual Basic poderá inferir o tipo de dados de `element`. Se ele estiver desativado e `element` não tiver sido declarado fora do loop, você deverá declará-lo na instrução `For Each`. Para declarar o tipo de dados de `element` explicitamente, use uma cláusula `As`. A menos que o tipo de dados do elemento seja definido fora da construção `For Each`...`Next`, seu escopo será o corpo do loop. Observe que você não pode declarar `element` tanto fora quanto dentro do loop.

Opcionalmente, você pode especificar `element` na instrução `Next`. Isso melhora a legibilidade do seu programa, especialmente se você tiver aninhado loops de `For Each`. Você deve especificar a mesma variável que aparece na instrução de `For Each` correspondente.

Talvez você queira evitar alterar o valor de `element` dentro de um loop. Fazer isso pode dificultar a leitura e a depuração do código. Alterar o valor de `group` não afeta a coleção ou seus elementos, que foram determinados quando o loop foi inserido pela primeira vez.

Quando você estiver aninhando loops, se uma instrução `Next` de um nível de aninhamento externo for encontrada antes da `Next` de um nível interno, o compilador sinalizará um erro. No entanto, o compilador pode detectar esse erro sobreposto somente se você especificar `element` em cada instrução `Next`.

Se o seu código depende de percorrer uma coleção em uma ordem específica, um loop `For Each`...`Next` não é a melhor opção, a menos que você saiba as características do objeto enumerador que a coleção expõe. A ordem de passagem não é determinada por Visual Basic, mas pelo método <xref:System.Collections.IEnumerator.MoveNext%2A> do objeto enumerador. Portanto, talvez você não consiga prever qual elemento da coleção é o primeiro a ser retornado em `element`, ou que é o próximo a ser retornado após um determinado elemento. Você pode obter resultados mais confiáveis usando uma estrutura de loop diferente, como `For`...`Next` ou `Do`...`Loop`.

O tempo de execução deve ser capaz de converter os elementos em `group` para `element`. A instrução [`Option Strict`] controla se as conversões de alargamento e de estreitamento são permitidas (`Option Strict` está desativado, seu valor padrão) ou se apenas conversões ampliadas são permitidas (`Option Strict` está ativado). Para obter mais informações, consulte [conversões redutoras](#narrowing-conversions).

O tipo de dados de `group` deve ser um tipo de referência que se refere a uma coleção ou uma matriz enumerável. Normalmente, isso significa que `group` se refere a um objeto que implementa a interface <xref:System.Collections.IEnumerable> do namespace `System.Collections` ou a interface <xref:System.Collections.Generic.IEnumerable%601> do namespace `System.Collections.Generic`. `System.Collections.IEnumerable` define o método <xref:System.Collections.IEnumerable.GetEnumerator%2A>, que retorna um objeto enumerador para a coleção. O objeto Enumerator implementa a interface `System.Collections.IEnumerator` do namespace `System.Collections` e expõe a propriedade <xref:System.Collections.IEnumerator.Current%2A> e os métodos <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.MoveNext%2A>. Visual Basic os usa para atravessar a coleção.

### <a name="narrowing-conversions"></a>Conversões de redução

Quando `Option Strict` é definido como `On`, as conversões redutoras normalmente causam erros do compilador. Em uma instrução `For Each`, no entanto, as conversões dos elementos em `group` para `element` são avaliadas e executadas em tempo de execução, e erros de compilador causados por conversões redutoras são suprimidos.

No exemplo a seguir, a atribuição de `m` como o valor inicial para `n` não é compilada quando `Option Strict` está ativada porque a conversão de um `Long` para um `Integer` é uma conversão de restrição. No entanto, na instrução `For Each`, nenhum erro do compilador é relatado, mesmo que a atribuição a `number` exija a mesma conversão de `Long` para `Integer`. Na instrução `For Each` que contém um número grande, um erro em tempo de execução ocorre quando <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> é aplicado ao número grande.

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>Chamadas de IEnumerator

Quando a execução de um loop de `For Each`...`Next` é iniciada, Visual Basic verifica se `group` se refere a um objeto de coleção válido. Caso contrário, ele gera uma exceção. Caso contrário, ele chama o método <xref:System.Collections.IEnumerator.MoveNext%2A> e a propriedade <xref:System.Collections.IEnumerator.Current%2A> do objeto enumerador para retornar o primeiro elemento. Se `MoveNext` indica que não há nenhum elemento seguinte, ou seja, se a coleção estiver vazia, o loop `For Each` será interrompido e o controle passará para a instrução após a instrução `Next`. Caso contrário, Visual Basic define `element` para o primeiro elemento e executa o bloco de instruções.

Cada vez que Visual Basic encontra a instrução `Next`, ele retorna à instrução `For Each`. Novamente, ele chama `MoveNext` e `Current` para retornar o próximo elemento e, novamente, ele executa o bloco ou interrompe o loop dependendo do resultado. Esse processo continua até que `MoveNext` indica que não há nenhum elemento seguinte ou uma instrução `Exit For` é encontrada.

**Modificando a coleção.** O objeto enumerador retornado por <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalmente não permite que você altere a coleção adicionando, excluindo, substituindo ou reordenando quaisquer elementos. Se você alterar a coleção depois de iniciar um loop `For Each`...`Next`, o objeto enumerador se tornará inválido e a próxima tentativa de acessar um elemento causará uma exceção <xref:System.InvalidOperationException>.

No entanto, esse bloqueio de modificação não é determinado pelo Visual Basic, mas sim pela implementação da interface <xref:System.Collections.IEnumerable>. É possível implementar `IEnumerable` de uma maneira que permita modificações durante a iteração. Se estiver pensando em fazer essa modificação dinâmica, certifique-se de entender as características da implementação de `IEnumerable` na coleção que você está usando.

**Modificando elementos de coleção.** A propriedade <xref:System.Collections.IEnumerator.Current%2A> do objeto enumerador é [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)e retorna uma cópia local de cada elemento da coleção. Isso significa que você não pode modificar os elementos em um loop `For Each`...`Next`. Qualquer modificação que você faça afeta apenas a cópia local de `Current` e não é refletida de volta para a coleção subjacente. No entanto, se um elemento for um tipo de referência, você poderá modificar os membros da instância para a qual ele aponta. O exemplo a seguir modifica o membro `BackColor` de cada elemento `thisControl`. No entanto, você não pode modificar `thisControl` si mesmo.

```vb
Sub LightBlueBackground(thisForm As System.Windows.Forms.Form)
    For Each thisControl In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

O exemplo anterior pode modificar o membro `BackColor` de cada elemento `thisControl`, embora ele não possa modificar `thisControl` si mesmo.

**Atravessando matrizes.** Como a classe <xref:System.Array> implementa a interface <xref:System.Collections.IEnumerable>, todas as matrizes expõem o método <xref:System.Array.GetEnumerator%2A>. Isso significa que você pode iterar por meio de uma matriz com um loop `For Each`...`Next`. No entanto, você só pode ler os elementos da matriz. Você não pode alterá-los.

## <a name="example"></a>Exemplo

O exemplo a seguir lista todas as pastas em C:\ diretório usando a classe <xref:System.IO.DirectoryInfo>.

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra um procedimento para a classificação de uma coleção. O exemplo classifica as instâncias de uma classe `Car` que são armazenadas em um <xref:System.Collections.Generic.List%601>. A classe `Car` implementa a interface <xref:System.IComparable%601>, que requer que o método <xref:System.IComparable%601.CompareTo%2A> seja implementado.

Cada chamada para o método <xref:System.IComparable%601.CompareTo%2A> faz uma única comparação que é usada para classificação. Os códigos escritos pelo usuário no método `CompareTo` retornam um valor para cada comparação do objeto atual com outro objeto. O valor retornado será menor que zero se o objeto atual for menor que o outro objeto, maior que zero se o objeto atual for maior que o outro objeto e zero, se eles forem iguais. Isso permite que você defina no código os critérios para maior que, menor que e igual.

No método `ListCars`, a instrução `cars.Sort()` classifica a lista. Essa chamada para o método <xref:System.Collections.Generic.List%601.Sort%2A> da <xref:System.Collections.Generic.List%601> faz com que o método `CompareTo` seja chamado automaticamente para os objetos `Car` na `List`.

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>Consulte também

- [Coleções](../../../standard/collections/index.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicializadores de Coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
