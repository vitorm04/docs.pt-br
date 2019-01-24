---
title: Instrução For...Next (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 703a30a558067b386c6bb5288012094418d61ca7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746267"
---
# <a name="fornext-statement-visual-basic"></a>Instrução For...Next (Visual Basic)
Repete um grupo de instruções um número de vezes especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>Partes  
  
|Parte|Descrição|  
|----------|-----------------|  
|`counter`|Necessário no `For` instrução. Variável numérica. A variável de controle para o loop. Para obter mais informações, consulte [contra-argumento](#BKMK_Counter) mais adiante neste tópico.|  
|`datatype`|Opcional. Tipo de dados de `counter`. Para obter mais informações, consulte [contra-argumento](#BKMK_Counter) mais adiante neste tópico.|  
|`start`|Necessário. Expressão numérica. O valor inicial de `counter`.|  
|`end`|Necessário. Expressão numérica. O valor final de `counter`.|  
|`step`|Opcional. Expressão numérica. A quantidade pela qual `counter` é incrementado toda vez pelo loop.|  
|`statements`|Opcional. Uma ou mais instruções entre `For` e `Next` que executam o número de vezes especificado.|  
|`Continue For`|Opcional. Transfere o controle para a próxima iteração do loop.|  
|`Exit For`|Opcional. Transfere o controle do `For` loop.|  
|`Next`|Necessário. Finaliza a definição do `For` loop.|  
  
> [!NOTE]
>  O `To` nesta instrução, a palavra-chave é usada para especificar o intervalo para o contador. Você também pode usar essa palavra-chave no [selecione... Instrução de caso](../../../visual-basic/language-reference/statements/select-case-statement.md) e nas declarações de matriz. Para obter mais informações sobre declarações de matriz, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Exemplos simples  
 Você usa um `For`... `Next` estrutura quando quiser repetir um número definido de horas de um conjunto de instruções.  
  
 No exemplo a seguir, o `index` variável começa com um valor de 1 e é incrementada a cada iteração do loop, terminando quando o valor da `index` atinge 5.  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 No exemplo a seguir, o `number` variável começa em 2 e é reduzido por 0,25 em cada iteração do loop, terminando quando o valor da `number` chegar a 0. O `Step` argumento de `-.25` reduz o valor por 0,25 em cada iteração do loop.  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  Um [enquanto... Finalizar instrução While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) funciona bem quando você não sabe com antecedência quantas vezes para executar as instruções no loop. No entanto, quando você pretende executar o loop de um número específico de vezes, um `For`... `Next` loop é uma opção melhor. Quando você entra pela primeira vez no loop, você determinar o número de iterações.  
  
## <a name="nesting-loops"></a>Loops aninhados  
 Você pode aninhar `For` loops, colocando um loop dentro de outra. O exemplo a seguir demonstra aninhada `For`... `Next` estruturas que têm valores diferentes. O loop externo cria uma cadeia de caracteres para cada iteração do loop. Loop interno decrementa uma variável de contador de loop para cada iteração do loop.  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 Ao aninhar loops, cada loop deve ter um único `counter` variável.  
  
 Você também pode aninhar diferentes tipos de estruturas de controle dentro do outro. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Sair para e continua por  
 O `Exit For` instrução imediatamente encerra o `For`...`Next` loop e transfere o controle para a instrução que segue o `Next` instrução.  
  
 O `Continue For` transfere o controle imediatamente para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 O exemplo a seguir ilustra o uso do `Continue For` e `Exit For` instruções.  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 Você pode colocar qualquer número de `Exit For` as instruções em um `For`...`Next` Executar um loop. Quando usado dentro aninhados `For`...`Next` loops, `Exit For` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.  
  
 `Exit For` geralmente é usado depois de avaliar alguma condição (por exemplo, em um `If`... `Then`... `Else` estrutura). Você talvez queira usar `Exit For` para as seguintes condições:  
  
-   Continuar para fazer a iteração é desnecessária ou impossível. Um valor errado ou uma solicitação de encerramento pode criar essa condição.  
  
-   Um `Try`... `Catch`... `Finally` instrução captura uma exceção. Você pode usar `Exit For` no final o `Finally` bloco.  
  
-   Você tem um loop infinito, o que é um loop que possa ser executada um número grande ou mesmo infinito de vezes. Se você detectar uma condição desse tipo, você pode usar `Exit For` para escapar do loop. Para obter mais informações, consulte [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Implementação Técnica  
 Quando um `For`... `Next` loop for iniciado, o Visual Basic avalia `start`, `end`, e `step`. Visual Basic avalia esses valores só nesse momento e, em seguida, atribui `start` para `counter`. Antes da instrução do bloco é executado, Visual Basic compara `counter` para `end`. Se `counter` já for maior do que o `end` valor (ou menor se `step` é negativo), o `For` loop termina e o controle passa para a instrução que segue o `Next` instrução. Caso contrário, o bloco de instrução é executada.  
  
 Cada vez que o Visual Basic encontra a `Next` instrução, ele é incrementado `counter` pela `step` e retorna para o `For` instrução. Novamente, ele compara `counter` para `end`, e novamente ele executa o bloco ou sai do loop, dependendo do resultado. Esse processo continua até `counter` passa `end` ou um `Exit For` instrução for encontrada.  
  
 O loop não para até `counter` passou `end`. Se `counter` é igual a `end`, o loop continua. A comparação que determina se é necessário executar o bloco `counter`  <=  `end` se `step` for positivo e `counter`  >=  `end` se `step` é negativo.  
  
 Se você alterar o valor de `counter` enquanto dentro de um loop, seu código pode ser mais difícil de ler e depurar. Alterar o valor de `start`, `end`, ou `step` não afeta os valores de iteração que foram determinados quando o loop foi acessado pela primeira vez.  
  
 Se você aninhar loops, o compilador sinaliza um erro se encontra o `Next` instrução de um nível de aninhamento externa antes do `Next` instrução de um nível interno. No entanto, o compilador pode detectar isso sobreposição de erro somente se você especificar `counter` em cada `Next` instrução.  
  
### <a name="step-argument"></a>Argumento de etapa  
 O valor de `step` pode ser positivo ou negativo. Esse parâmetro determina o processamento de loop de acordo com a tabela a seguir:  
  
|**Valor da etapa**|**O loop é executado se**|  
|--------------------|--------------------------|  
|Positivo ou zero|`counter` <= `end`|  
|Negativo|`counter` >= `end`|  
  
 O valor padrão de `step` é 1.  
  
###  <a name="BKMK_Counter"></a> Argumento do contador  
 A tabela a seguir indica se `counter` define uma nova variável local que tem como escopo a todo o `For…Next` loop. Essa decisão depende se `datatype` está presente e se `counter` já está definido.  
  
|É `datatype` presente?|É `counter` já definido?|Resultado (se `counter` define uma nova variável local que tem como escopo a todo o `For...Next` loop)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Não|Sim|Não, porque `counter` já está definido. Se o escopo de `counter` não são locais para o procedimento, ocorre um aviso de tempo de compilação.|  
|Não|Não|Sim. O tipo de dados é inferido do `start`, `end`, e `step` expressões. Para obter informações sobre a inferência de tipo, consulte [instrução opção inferir](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Sim|Sim|Sim, mas somente se existente `counter` variável é definida fora do procedimento. Essa variável permanece separada. Se o escopo da existente `counter` variável é local para o procedimento, ocorre um erro de tempo de compilação.|  
|Sim|Não|Sim.|  
  
 O tipo de dados `counter` determina o tipo da iteração, que deve ser um dos seguintes tipos:  
  
-   Um `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, ou `Double`.  
  
-   Uma enumeração que declarar usando um [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   Um `Object`.  
  
-   Um tipo `T` que tem os seguintes operadores, onde `B` é um tipo que pode ser usado em um `Boolean` expressão.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Opcionalmente, você pode especificar o `counter` variável o `Next` instrução. Essa sintaxe melhora a legibilidade do programa, especialmente se você tiver aninhado `For` loops. Você deve especificar a variável que aparece nas correspondentes `For` instrução.  
  
 O `start`, `end`, e `step` expressões podem ser avaliada como qualquer tipo de dados é ampliado para o tipo de `counter`. Se você usar um tipo definido pelo usuário para `counter`, talvez você precise definir o `CType` operador de conversão para converter os tipos dos `start`, `end`, ou `step` para o tipo de `counter`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir remove todos os elementos de uma lista genérica. Em vez de um [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md), o exemplo mostra um `For`... `Next` que itera em ordem decrescente. O exemplo usa essa técnica porque o `removeAt` método faz com que elementos após o elemento removido tenham um valor de índice mais baixo.  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir itera por meio de uma enumeração que é declarada usando um [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, os parâmetros da instrução usam uma classe que tem as sobrecargas de operador para o `+`, `-`, `>=`, e `<=` operadores.  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Collections.Generic.List%601>
- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Coleções](../../programming-guide/concepts/collections.md)
