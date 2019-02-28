---
title: Instrução Do...Loop (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: c7c7987508260a0181904feacf3782f66066309f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968199"
---
# <a name="doloop-statement-visual-basic"></a>Instrução Do...Loop (Visual Basic)
Repete um bloco de instruções enquanto uma `Boolean` condição for `True` ou até que a condição se torne `True`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`Do`|Necessário. Inicia a definição do `Do` loop.|  
|`While`|Necessário a menos que `Until` seja usado. Repita o loop até que `condition` é `False`.|  
|`Until`|Necessário a menos que `While` seja usado. Repita o loop até que `condition` é `True`.|  
|`condition`|Opcional. Expressão `Boolean`. Se `condition` está `Nothing`, Visual Basic trata isso `False`.|  
|`statements`|Opcional. Uma ou mais instruções que são repetidas ao mesmo tempo, ou até que, `condition` é `True`.|  
|`Continue Do`|Opcional. Transfere o controle para a próxima iteração do `Do` loop.|  
|`Exit Do`|Opcional. Transfere o controle do `Do` loop.|  
|`Loop`|Necessário. Finaliza a definição do `Do` loop.|  
  
## <a name="remarks"></a>Comentários  
 Use um `Do...Loop` estrutura quando desejar repetir um conjunto de declarações por um número indefinido de vezes, até que uma condição seja atendida. Se você quiser repetir as declarações de um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.  
  
 Você pode usar tanto `While` ou `Until` para especificar `condition`, mas não ambos.  
  
 Você pode testar `condition` apenas uma vez, no início ou final do loop. Se você testar `condition` no início do loop (no `Do` instrução), o loop não pode ser executado até mesmo uma vez. Se você testar no final do loop (no `Loop` instrução), o loop é sempre executado pelo menos uma vez.  
  
 A condição normalmente resulta de uma comparação entre dois valores, mas ele pode ser qualquer expressão que é avaliada como uma [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`). Isso inclui os valores de outros tipos de dados, como tipos numéricos, que foram convertidos para `Boolean`.  
  
 Você pode aninhar `Do` loops, colocando um loop dentro de outra. Você também pode aninhar diferentes tipos de estruturas de controle dentro do outro. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  O `Do...Loop` estrutura lhe dá mais flexibilidade do que o [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) porque ele permite que você decida se deseja encerrar o loop quando `condition` deixa de ser `True` ou quando ela for primeiro `True`. Ele também permite que você teste `condition` no início ou final do loop.  
  
## <a name="exit-do"></a>Sair  
 O [sair fazer](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer uma maneira alternativa para sair um `Do…Loop`. `Exit Do` transfere o controle imediatamente para a instrução que segue o `Loop` instrução.  
  
 `Exit Do` geralmente é usado depois que alguma condição é avaliada, por exemplo, em um `If...Then...Else` estrutura. Você talvez queira encerrar um loop se você detectar uma condição que torna desnecessária ou impossível continuar a iteração, como um valor errado ou uma solicitação de encerramento. Um uso de `Exit Do` é testar uma condição que poderia causar uma *um loop infinito*, que é um loop que possa ser executada um número grande ou mesmo infinito de vezes. Você pode usar `Exit Do` para escapar do loop.  
  
 Você pode incluir qualquer número de `Exit Do` as instruções em um `Do…Loop`.  
  
 Quando usado dentro aninhados `Do` loops, `Exit Do` transfere o controle para fora do loop interno e para o próximo nível mais alto de aninhamento.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam em execução até que o `index` variável é maior que 10. O `Until` cláusula é no final do loop.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `While` cláusula em vez de um `Until` cláusula, e `condition` é testado no início do loop, em vez de no final.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir `condition` interrompe o loop de quando o `index` variável é maior que 100. O `If` instrução no loop, no entanto, faz com que o `Exit Do` instrução para interromper o loop quando a variável de índice é maior que 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A> abre o arquivo de método e retorna um <xref:System.IO.StreamReader> que lê os caracteres. No `Do...Loop` condição, o <xref:System.IO.StreamReader.Peek%2A> método o `StreamReader` determina se há quaisquer caracteres adicionais.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Consulte também
- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
