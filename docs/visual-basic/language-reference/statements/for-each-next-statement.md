---
title: "Instru&#231;&#227;o For Each...Next (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ForEach"
  - "vb.ForEachNext"
  - "vb.Each"
  - "ForEachNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "loops infinitos"
  - "Próxima instrução For Each... Avançar"
  - "loops intermináveis"
  - "estruturas de loop, para cada um... Avançar"
  - "loops intermináveis"
  - "palavra-chave Each"
  - "instruções de repetição"
  - "instrução For Each"
  - "coleções de repetição de instrução"
  - "loops infinitos"
  - "instruções For Each...Next"
  - "Palavra-chave [Visual Basic] para cada um... Instruções Avançar"
  - "Sair instrução For Each... Instruções Avançar"
  - "iteração"
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
caps.latest.revision: 56
caps.handback.revision: 56
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o For Each...Next (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Repete um grupo de instruções para cada elemento em uma coleção.  
  
## Sintaxe  
  
```  
For Each element [ As datatype ] In group  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ element ]  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`element`|Necessário na declaração de `For Each` .  Opcional na declaração de `Next` .  Variável.  Usado para percorrer os elementos da coleção.|  
|`datatype`|Necessário se `element` não já está declarado.  Tipo de dados de `element`.|  
|`group`|Obrigatório.  Uma variável com um tipo que é um tipo ou objeto de coleção.  Refere\-se a coleção em que `statements` deve ser repetido.|  
|`statements`|Opcional.  Uma ou mais instruções entre e `For Each``Next` que executam em cada item em `group`.|  
|`Continue For`|Opcional.  Transfere controle ao início do loop de `For Each` .|  
|`Exit For`|Opcional.  Transfere controle fora do loop `For Each`.|  
|`Next`|Obrigatório.  Termina a definição do loop `For Each`.|  
  
## Exemplo simples  
 Use um loop de `For Each`…`Next` quando você desejar repetir um conjunto de instruções para cada elemento de uma coleção ou de uma matriz.  
  
> [!TIP]
>  [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md) funciona bem quando você pode associar cada iteração de um loop através de uma variável de controle e determinar os valores inicial e final dessa variável.  No entanto, quando você está tratando uma coleção, o conceito de valores inicial e final não é significativo, e você não sabe quantos elementos necessariamente tem a coleção.  Neste tipo dos casos, um loop de `For Each`…`Next` geralmente é uma opção melhor.  
  
 No exemplo, a instrução de `For Each`…`Next` itera através de todos os elementos de uma coleção de lista.  
  
 [!code-vb[VbVbalrStatements#121](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_1.vb)]  
  
 Para obter mais exemplos, consulte [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md) e [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Loops aninhados  
 Você pode aninhar loop de `For Each` colocando um loop dentro de outro.  
  
 O exemplo a seguir demonstra estruturas aninhadas de `For Each`…`Next` .  
  
 [!code-vb[VbVbalrStatements#122](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_2.vb)]  
  
 Quando você aninha loop, cada loop deve ter uma variável exclusivo de `element` .  
  
 Você também pode aninhar diferentes tipos de estruturas de controle dentro da outra.  Para obter mais informações, consulte [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## Para e continue para sair  
 A execução das causas de instrução de [Para sair](../../../visual-basic/language-reference/statements/exit-statement.md) para sair do… loop de `For``Next` e o transfere controle à declaração que segue a declaração de `Next` .  
  
 O transfere o controle da declaração de `Continue For` imediatamente para a próxima iteração do loop.  Para obter mais informações, consulte [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 O exemplo a seguir mostra como usar as declarações de `Continue For` e de `Exit For` .  
  
 [!code-vb[VbVbalrStatements#123](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_3.vb)]  
  
 Você pode colocar qualquer número de declarações de `Exit For` em um loop de `For Each` .  Quando usado dentro de loops `For Each` aninhados, `Exit For` faz com que a execução sair do controle interno do loop e da transferências de alto nível de aninhamento.  
  
 `Exit For` geralmente é usado após uma avaliação de alguma condição, por exemplo, em um estrutura de `If`……`Then``Else` .  Você pode usar `Exit For` nas seguintes circunstâncias:  
  
-   Continuar iterando é desnecessária ou impossível.  Isso pode ser causado por um valor errôneo ou por uma solicitação de finalização.  
  
-   Uma exceção é detectada em `Try`……`Catch``Finally`.  Você pode usar `Exit For` no final do bloco de `Finally` .  
  
-   Há um loop interminável, que é um loop que é um grande ou mesmo número infinito de vezes.  Se você detectar tal condição, você pode usar `Exit For` para escapar do loop.  Para obter mais informações, consulte [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## Iteradores  
 Você usa *um iterador* para executar uma iteração personalizado em uma coleção.  Um iterador pode ser uma função ou um acessador de `Get` .  Usa uma instrução de `Yield` para retornar um de cada vez a cada elemento da coleção.  
  
 Você chama um iterador usando uma instrução de `For Each...Next` .  Cada iteração do loop de `For Each` chama o iterador.  Quando uma declaração de `Yield` é alcançada no iterador, a expressão na declaração de `Yield` é retornada, e o local atual no código é mantido.  A execução é reiniciada de aquele local na próxima vez que o iterador é chamado.  
  
 O exemplo a seguir usa uma função de iterador.  A função de iterador tem uma instrução de `Yield` que está dentro de um loop de [For… Next](../../../visual-basic/language-reference/statements/for-next-statement.md) .  No método de `ListEvenNumbers` , cada iteração do corpo de instrução de `For Each` cria uma chamada para a função de iterador, que continua a próxima instrução de `Yield` .  
  
 [!code-vb[VbVbalrStatements#127](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_4.vb)]  
  
 Para obter mais informações, consulte [Iteradores](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md),  [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md), e [Iterador](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
## Implementação técnica  
 Quando uma declaração de `For Each`…`Next` é executado, o Visual Basic avalia a coleção somente uma vez, antes que inicia o loop.  Se seu bloco de declaração altera `element` ou `group`, essas alterações não afetam a iteração do loop.  
  
 Quando todos os elementos na coleção são atribuídos em sucessão a `element`, as paradas de loop de `For Each` e para o controle passa para a declaração que segue a declaração de `Next` .  
  
 Se `element` não foi declarada fora do loop, você deve declará\-lo na declaração de `For Each` .  Você pode declarar o tipo de `element` explicitamente usando uma instrução de `As` , ou você pode confiar na inferência de tipos para atribuir o tipo.  Em ambos os casos, o escopo de `element` é o corpo do loop.  No entanto, você não pode declarar `element` fora e dentro do loop.  
  
 Você pode opcionalmente especificar `element` na declaração de `Next` .  Isso melhora a legibilidade do seu programa, especialmente se você tem loops aninhados de `For Each` .  Você deve especificar o mesmo variável aquele que aparece na declaração correspondente de `For Each` .  
  
 Você pode desejar evitar alterar o valor de `element` dentro de um loop.  Isso pode fazê\-lo mais difícil de ler e depurar seu código.  Altere o valor de `group` não afeta a coleção ou seus elementos, que eram determinados quando o loop foi inserida primeiro.  
  
 Quando você tiver loops aninhados, se uma instrução de `Next` de um nível de aninhamento externo está localizado antes que `Next` de um nível interno, o compilador sinalizar um erro.  No entanto, o compilador pode detectar este erro sobrepostos somente se você especificar `element` em cada declaração de `Next` .  
  
 Se seu código depende de atravessar uma coleção em uma ordem específica, um loop de `For Each`…`Next` não é a melhor opção, a menos que você saiba que as características do objeto que enumerator expõe a coleção.  A ordem de passagem não é determinado pelo Visual Basic, mas pelo método de <xref:System.Collections.IEnumerator.MoveNext%2A> de objeto enumerator.  Como consequência, você não poderá prever que elemento da coleção é o primeiro a ser retornado em `element`, ou qual for a ser retornado após um determinado elemento.  Você pode obter resultados mais confiáveis usando uma estrutura de loop diferente, como `For`…`Next` ou `Do`…`Loop`.  
  
 O tipo de dados de `element` deve ser tal que o tipo de dados dos elementos de `group` pode ser convertido.  
  
 O tipo de dados de `group` deve ser um tipo de referência que faz referência a uma coleção ou matriz que é enumeráveis.  Mais geralmente isso significa que `group` se refere a um objeto que implementa a interface de <xref:System.Collections.IEnumerable> de namespace de `System.Collections` ou a interface de <xref:System.Collections.Generic.IEnumerable%601> de namespace de `System.Collections.Generic` .  `System.Collections.IEnumerable` define o método de <xref:System.Collections.IEnumerable.GetEnumerator%2A> , que retorna um objeto enumerator para a coleção.  O objeto enumerator implementa a interface de `System.Collections.IEnumerator` de namespace de `System.Collections` e expõe a propriedade de <xref:System.Collections.IEnumerator.Current%2A> e métodos de <xref:System.Collections.IEnumerator.Reset%2A> e de <xref:System.Collections.IEnumerator.MoveNext%2A> .  Visual Basic usa esses para atravessar a coleção.  
  
### Conversões Redutoras  
 Quando `Option Strict` é definido como `On`, conversões causam normalmente erros de compilador.  Em uma instrução de `For Each` , no entanto, conversões de elementos em `group` a `element` são avaliadas e executadas em tempo de execução, e os erros de compilador causados conversões são suprimidos.  
  
 No exemplo a seguir, a atribuição de `m` como o valor inicial para `n` não compila quando `Option Strict` está ativado porque a conversão de `Long` a `Integer` é uma conversão redutora.  Na declaração de `For Each` , no entanto, nenhum erro do compilador é relatado, mesmo que a atribuição a `number` requer a mesma conversão de `Long` a `Integer`.  Na declaração de `For Each` que contém um número grande, um erro em tempo de execução ocorre quando <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> é aplicado ao número grande.  
  
 [!code-vb[VbVbalrStatements#89](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_5.vb)]  
  
### Chamadas de IEnumerator  
 Quando a execução de um loop de `For Each`…`Next` Visual Basic, verifique se `group` se refere a um objeto válido de coleção.  Caso contrário, ele gera uma exceção.  Caso contrário, chama o método de <xref:System.Collections.IEnumerator.MoveNext%2A> e a propriedade de <xref:System.Collections.IEnumerator.Current%2A> de objeto enumerator para retornar o primeiro elemento.  Se `MoveNext` indica que não há nenhum elemento seguir, isto é, se a coleção estiver vazia, paradas de loop de `For Each` e ao controle passa para a declaração que segue a declaração de `Next` .  Caso contrário, o Visual Basic define `element` para o primeiro elemento e executa o bloco de declaração.  
  
 Cada vez que o Visual Basic localize a declaração de `Next` , retorna para a declaração de `For Each` .  Novamente `MoveNext` e chama `Current` para retornar o próximo elemento, e novamente executa o bloco ou para o loop dependendo do resultado.  Esse processo continua até que `MoveNext` indica que não há nenhum elemento seguir ou uma declaração de `Exit For` está localizado.  
  
 **Alterando a coleção.** O objeto enumerator retornado por <xref:System.Collections.IEnumerable.GetEnumerator%2A> normalmente não permite que você altere a coleção adicionar, excluir, substituição, ou reorganizando quaisquer elementos.  Se você altera a coleção depois de iniciou um loop de `For Each`…`Next` , o objeto enumerator se torna inválida, e a seguir tentativa para acessar um elemento causa de uma exceção de <xref:System.InvalidOperationException> .  
  
 No entanto, esse bloqueio de alteração não é determinado por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], mas em vez pela implementação da interface de <xref:System.Collections.IEnumerable> .  É possível implementar `IEnumerable` de uma maneira que permite a alteração durante a iteração.  Se você estiver considerando fazendo tal alteração dinâmico, certifique\-se de que você entende as características da implementação de `IEnumerable` na coleção que você está usando.  
  
 **Elementos de alteração de coleção.** A propriedade de <xref:System.Collections.IEnumerator.Current%2A> de objeto enumerator é [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), e retorna uma cópia local de cada elemento da coleção.  Isso significa que você não pode modificar os próprios elementos em um loop de `For Each`…`Next` .  Qualquer alteração você faz a afeta somente a cópia local de `Current` e não é refletido de novo na coleção subjacente.  No entanto, se um elemento é um tipo de referência, você pode alterar os membros da instância para qual ele aponta.  O exemplo a seguir altera o membro de `BackColor` de cada elemento de `thisControl` .  Você não pode, no entanto, alterar `thisControl` próprio.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 O exemplo anterior pode alterar o membro de `BackColor` de cada elemento de `thisControl` , embora não pode alterar `thisControl` próprio.  
  
 **Percorrer matrizes.** Porque a classe de <xref:System.Array> implementa a interface de <xref:System.Collections.IEnumerable> , todas as matrizes expõe o método de <xref:System.Array.GetEnumerator%2A> .  Isso significa que você pode percorrer uma matriz com um loop de `For Each`…`Next` .  No entanto, você pode ler somente os elementos da matriz.  Você não pode alterá\-los.  
  
## Exemplo  
 O exemplo a seguir lista todas as pastas no diretório de C:\\ usando a classe de <xref:System.IO.DirectoryInfo> .  
  
 [!code-vb[VbVbalrStatements#124](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_6.vb)]  
  
## Exemplo  
 O exemplo a seguir ilustra um procedimento para classificar uma coleção.  Instâncias de tipos de exemplo de `Car` classe que são armazenadas em <xref:System.Collections.Generic.List%601>.  A classe de `Car` implementa a interface de <xref:System.IComparable%601> , que requer que o método de <xref:System.IComparable%601.CompareTo%2A> seja implementado.  
  
 Cada chamada ao método de <xref:System.IComparable%601.CompareTo%2A> faça uma única comparação que é usada para ordenação.  o código de escrito no método de `CompareTo` retorna um valor para cada comparação do objeto atual com outro objeto.  O valor retornado é menor que zero se o objeto atual é menor que o outro objeto, maior que zero se o objeto atual é maior que o outro objeto, e zero se forem iguais.  Isso permite que você defina no código os critérios para maior do que, menor que, e iguais.  
  
 No método de `ListCars` , a instrução de `cars.Sort()` classificar a lista.  Esta chamada para o método de <xref:System.Collections.Generic.List%601.Sort%2A> de <xref:System.Collections.Generic.List%601> faz com que o método de `CompareTo` a ser chamado automaticamente para os objetos de `Car` em `List`.  
  
 [!code-vb[VbVbalrStatements#125](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-each-next-statement_7.vb)]  
  
## Consulte também  
 [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Inicializadores de coleção](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)