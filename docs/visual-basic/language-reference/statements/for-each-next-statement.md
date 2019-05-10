---
title: Instrução For Each...Next (Visual Basic)
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
ms.openlocfilehash: ecde6ca8d3a95e356c5b1389ba95c4ad72b68d45
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623899"
---
# <a name="for-eachnext-statement-visual-basic"></a>Instrução For Each...Next (Visual Basic)
Repete um grupo de instruções para cada elemento em uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`element`|Necessário no `For Each` instrução. Opcional no `Next` instrução. variável. Usado para iterar por meio dos elementos da coleção.|  
|`datatype`|Necessário se `element` já não está declarado. Tipo de dados de `element`.|  
|`group`|Necessário. Uma variável com um tipo que é um tipo de coleção ou um objeto. Refere-se à coleção na qual o `statements` devem ser repetidas.|  
|`statements`|Opcional. Uma ou mais instruções entre `For Each` e `Next` que são executados em cada item em `group`.|  
|`Continue For`|Opcional. Transfere o controle para o início do `For Each` loop.|  
|`Exit For`|Opcional. Transfere o controle do `For Each` loop.|  
|`Next`|Necessário. Finaliza a definição do `For Each` loop.|  
  
## <a name="simple-example"></a>Exemplo simples  
 Use um `For Each`... `Next` loop quando quiser repetir um conjunto de instruções para cada elemento de uma coleção ou matriz.  
  
> [!TIP]
>  Um [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) funciona bem quando você pode associar a uma variável de controle de cada iteração de um loop e determinar os valores inicial e final da variável. No entanto, quando você está lidando com uma coleção, o conceito de valores inicias e finais não é significativo e você não souber necessariamente quantos elementos a coleção tem. Nesse tipo de caso, um `For Each`... `Next` loop geralmente é uma opção melhor.  
  
 No exemplo a seguir, o `For Each`...`Next` instrução itera em todos os elementos de uma coleção de lista.  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 Para obter mais exemplos, consulte [coleções](../../../standard/collections/index.md) e [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="nested-loops"></a>Loops aninhados  
 Você pode aninhar `For Each` loops, colocando um loop dentro de outra.  
  
 O exemplo a seguir demonstra aninhada `For Each`...`Next` estruturas.  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 Quando você aninhar loops, cada loop deve ter um único `element` variável.  
  
 Você também pode aninhar diferentes tipos de estruturas de controle dentro do outro. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Sair para e continua por  
 O [sair para](../../../visual-basic/language-reference/statements/exit-statement.md) instrução faz com que a execução para sair do `For`...`Next` loop e transfere o controle para a instrução que segue o `Next` instrução.  
  
 O `Continue For` transfere o controle imediatamente para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 O exemplo a seguir mostra como usar o `Continue For` e `Exit For` instruções.  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 Você pode colocar qualquer número de `Exit For` as instruções em um `For Each` loop. Quando usado dentro aninhados `For Each` loops, `Exit For` faz com que o controle mais interno de loop e transferências de saída para o próximo nível mais alto de aninhamento da execução.  
  
 `Exit For` é frequentemente usado após uma avaliação de algumas condições, por exemplo, em um `If`... `Then`... `Else` estrutura. Você talvez queira usar `Exit For` para as seguintes condições:  
  
- Continuar para fazer a iteração é desnecessária ou impossível. Isso pode ser causado por um valor errado ou uma solicitação de encerramento.  
  
- Uma exceção é detectada em um `Try`... `Catch`... `Finally`. Você pode usar `Exit For` no final o `Finally` bloco.  
  
- Há um loop infinito, o que é um loop que possa ser executada um número grande ou mesmo infinito de vezes. Se você detectar uma condição desse tipo, você pode usar `Exit For` para escapar do loop. Para obter mais informações, consulte [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="iterators"></a>Iterators  
 Você usa um *iterador* para executar uma iteração personalizada em uma coleção. Um iterador pode ser uma função ou um `Get` acessador. Ele usa um `Yield` instrução para retornar cada elemento da coleção um por vez.  
  
 Você chama um iterador usando uma `For Each...Next` instrução. Cada iteração do loop `For Each` chama o iterador. Quando um `Yield` instrução é alcançada no iterador, a expressão no `Yield` instrução será retornada e o local atual no código é retido. A execução será reiniciada desse local na próxima vez que o iterador for chamado.  
  
 O exemplo a seguir usa uma função de iterador. A função de iterador tem uma `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. No `ListEvenNumbers` cada iteração de um método, o `For Each` corpo da instrução cria uma chamada à função iteradora, que avança para a próxima `Yield` instrução.  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 Para obter mais informações, consulte [iteradores](../../programming-guide/concepts/iterators.md), [instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md), e [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 Quando um `For Each`...`Next` instrução é executada, Visual Basic avalia a coleção somente uma vez, antes que o loop for iniciado. Se seu bloco de instrução altera `element` ou `group`, essas alterações não afetam a iteração do loop.  
  
 Quando todos os elementos na coleção sucessivamente receberam `element`, o `For Each` loop será interrompido e o controle passa para a instrução após a `Next` instrução.  
  
 Se `element` não tenha sido declarada fora desse loop, você deve declará-la no `For Each` instrução. Você pode declarar o tipo de `element` explicitamente, usando um `As` instrução, ou você pode contar com a inferência de tipo para atribuir o tipo. Em ambos os casos, o escopo de `element` é o corpo do loop. No entanto, você não pode declarar `element` fora e dentro do loop.  
  
 Você pode opcionalmente especificar `element` no `Next` instrução. Isso melhora a legibilidade do programa, especialmente se você tiver aninhado `For Each` loops. Você deve especificar a mesma variável como aquele que aparece nas correspondentes `For Each` instrução.  
  
 Você talvez queira evitar a alteração do valor de `element` dentro de um loop. Isso pode tornar mais difícil de ler e depurar seu código. Alterar o valor de `group` não afeta a coleção ou seus elementos, que foram determinados quando o loop foi acessado pela primeira vez.  
  
 Quando você estiver loops aninhados, se um `Next` declaração de um nível de aninhamento externa é encontrada antes do `Next` de um nível interno, o compilador sinaliza um erro. No entanto, o compilador pode detectar isso sobreposição de erro somente se você especificar `element` em cada `Next` instrução.  
  
 Se seu código depende de como percorrer uma coleção em uma ordem específica, um `For Each`... `Next` loop não é a melhor opção, a menos que você saiba as características do objeto enumerador coleção expõe. A ordem de passagem não é determinada pelo Visual Basic, mas pelo <xref:System.Collections.IEnumerator.MoveNext%2A> método do objeto enumerador. Portanto, não ser capaz de prever qual elemento da coleção é o primeiro a ser retornado em `element`, ou que é a próxima a ser retornada após um determinado elemento. Você pode obter resultados mais confiáveis, usando uma estrutura de loop diferentes, como `For`... `Next` ou `Do`... `Loop`.  
  
 O tipo de dados `element` deve ser, de modo que o tipo de dados dos elementos da `group` podem ser convertidos para ele.  
  
 O tipo de dados `group` deve ser um tipo de referência que se refere a uma coleção ou uma matriz que é enumerável. Geralmente isso significa que `group` refere-se a um objeto que implementa o <xref:System.Collections.IEnumerable> interface da `System.Collections` namespace ou o <xref:System.Collections.Generic.IEnumerable%601> interface da `System.Collections.Generic` namespace. `System.Collections.IEnumerable` Define o <xref:System.Collections.IEnumerable.GetEnumerator%2A> método, que retorna um objeto enumerador para a coleção. Implementa o objeto de enumerador a `System.Collections.IEnumerator` interface do `System.Collections` namespace e expõe os <xref:System.Collections.IEnumerator.Current%2A> propriedade e o <xref:System.Collections.IEnumerator.Reset%2A> e <xref:System.Collections.IEnumerator.MoveNext%2A> métodos. Visual Basic utiliza para percorrer a coleção.  
  
### <a name="narrowing-conversions"></a>Conversões de redução  
 Quando `Option Strict` é definido como `On`, normalmente, as conversões de redução causam erros de compilador. Em um `For Each` instrução, no entanto, as conversões de elementos no `group` para `element` são avaliadas e executada em tempo de execução e erros de compilador causados por conversões de redução são suprimidos.  
  
 No exemplo a seguir, a atribuição de `m` como o valor inicial de `n` não é compilado quando `Option Strict` está habilitada porque a conversão de uma `Long` para um `Integer` é uma conversão de estreitamento. No `For Each` instrução, no entanto, nenhum erro do compilador é relatado, mesmo que a atribuição ao `number` requer a mesma conversão de `Long` para `Integer`. No `For Each` um erro de tempo de execução de instrução que contém um número grande, ocorre quando <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> é aplicado a grande número.  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>Chamadas de IEnumerator  
 Quando a execução de um `For Each`... `Next` loop for iniciado, o Visual Basic verifica que `group` refere-se a um objeto de coleção válido. Caso contrário, ele gerará uma exceção. Caso contrário, ele chama o <xref:System.Collections.IEnumerator.MoveNext%2A> método e o <xref:System.Collections.IEnumerator.Current%2A> propriedade do objeto enumerador para retornar o primeiro elemento. Se `MoveNext` indica que não há nenhum elemento a seguir, ou seja, se a coleção estiver vazia, o `For Each` loop será interrompido e o controle passa para a instrução após a `Next` instrução. Caso contrário, o Visual Basic define `element` para o primeiro elemento e executa o bloco de instrução.  
  
 Cada vez que o Visual Basic encontra a `Next` instrução, ele retorna para o `For Each` instrução. Novamente, ele chama `MoveNext` e `Current` para retornar o próximo elemento e novamente ele executa o bloco de ou para o loop, dependendo do resultado. Esse processo continua até `MoveNext` indica que não há nenhum próximo elemento ou um `Exit For` instrução for encontrada.  
  
 **Modificação da coleção.** O objeto de enumerador retornado pelo <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalmente não permite que você alterar a coleção adicionando, excluindo, substituindo ou reordenar todos os elementos. Se você alterar a coleção depois que você inicia um `For Each`... `Next` loop, o objeto de enumerador se torna inválido e faz com que a próxima tentativa de acessar um elemento um <xref:System.InvalidOperationException> exceção.  
  
 No entanto, esse bloqueio de modificação não é determinado pelo Visual Basic, mas em vez disso, pela implementação do <xref:System.Collections.IEnumerable> interface. É possível implementar `IEnumerable` de forma que permite a modificação durante a iteração. Se você estiver considerando fazer essa modificação dinâmica, certifique-se de que você entenda as características do `IEnumerable` implementação na coleção que você está usando.  
  
 **Modificando elementos da coleção.** O <xref:System.Collections.IEnumerator.Current%2A> é de propriedade do objeto enumerador [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), e retorna uma cópia local de cada elemento da coleção. Isso significa que você não pode modificar os próprios elementos em um `For Each`... `Next` loop. Qualquer modificação que você fizer afeta somente a cópia local do `Current` e não será refletida de volta para a coleção subjacente. No entanto, se um elemento for um tipo de referência, você pode modificar os membros da instância à qual ele aponta. O exemplo a seguir modifica o `BackColor` membro de cada `thisControl` elemento. No entanto, não é possível, modificar `thisControl` em si.  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 O exemplo anterior pode modificar os `BackColor` membro de cada `thisControl` elemento, embora ele não é possível modificar `thisControl` em si.  
  
 **Atravessando matrizes.** Porque o <xref:System.Array> classe implementa as <xref:System.Collections.IEnumerable> interface, todas as matrizes expõem o <xref:System.Array.GetEnumerator%2A> método. Isso significa que você pode iterar por meio de uma matriz com um `For Each`... `Next` loop. No entanto, você pode apenas ler os elementos da matriz. Você não pode alterá-los.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lista todas as pastas no diretório c:\. por meio de <xref:System.IO.DirectoryInfo> classe.  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra um procedimento para a classificação de uma coleção. O exemplo classifica instâncias de um `Car` classe são armazenadas em um <xref:System.Collections.Generic.List%601>. A classe `Car` implementa a interface <xref:System.IComparable%601>, que requer que o método <xref:System.IComparable%601.CompareTo%2A> seja implementado.  
  
 Cada chamada para o <xref:System.IComparable%601.CompareTo%2A> método faz uma comparação única que é usada para classificação. Os códigos escritos pelo usuário no método `CompareTo` retornam um valor para cada comparação do objeto atual com outro objeto. O valor retornado será menor que zero se o objeto atual for menor que o outro objeto, maior que zero se o objeto atual for maior que o outro objeto e zero, se eles forem iguais. Isso permite que você defina no código os critérios para maior que, menor que e igual.  
  
 No método `ListCars`, a instrução `cars.Sort()` classifica a lista. Essa chamada para o método <xref:System.Collections.Generic.List%601.Sort%2A> da <xref:System.Collections.Generic.List%601> faz com que o método `CompareTo` seja chamado automaticamente para os objetos `Car` na `List`.  
  
 [!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]  
  
## <a name="see-also"></a>Consulte também

- [Coleções](../../../standard/collections/index.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Inicializadores de objeto: Tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Inicializadores de Coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
