---
title: Instrução Do...Loop
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
ms.openlocfilehash: 9384cbb355189be448fa4b8d274721b4a7ca6a20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351249"
---
# <a name="doloop-statement-visual-basic"></a>Instrução Do...Loop (Visual Basic)
Repete um bloco de instruções enquanto uma condição de `Boolean` é `True` ou até que a condição se torne `True`.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
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
|`Do`|Necessária. Inicia a definição do loop de `Do`.|  
|`While`|Necessário a menos que `Until` seja usado. Repita o loop até que `condition` seja `False`.|  
|`Until`|Necessário a menos que `While` seja usado. Repita o loop até que `condition` seja `True`.|  
|`condition`|Opcional. Expressão `Boolean`. Se `condition` for `Nothing`, Visual Basic o tratará como `False`.|  
|`statements`|Opcional. Uma ou mais instruções repetidas enquanto, ou até `condition`, são `True`.|  
|`Continue Do`|Opcional. Transfere o controle para a próxima iteração do loop de `Do`.|  
|`Exit Do`|Opcional. Transfere o controle do loop de `Do`.|  
|`Loop`|Necessária. Encerra a definição do loop de `Do`.|  
  
## <a name="remarks"></a>Comentários  
 Use uma estrutura `Do...Loop` quando quiser repetir um conjunto de instruções um número indefinido de vezes, até que uma condição seja satisfeita. Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) é geralmente uma opção melhor.  
  
 Você pode usar `While` ou `Until` para especificar `condition`, mas não ambos.  
  
 Você pode testar `condition` apenas uma vez, no início ou no fim do loop. Se você testar `condition` no início do loop (na instrução `Do`), o loop poderá não ser executado mesmo uma vez. Se você testar no final do loop (na instrução `Loop`), o loop sempre será executado pelo menos uma vez.  
  
 A condição geralmente resulta de uma comparação de dois valores, mas pode ser qualquer expressão avaliada como um valor de [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`). Isso inclui valores de outros tipos de dados, como tipos numéricos, que foram convertidos em `Boolean`.  
  
 Você pode aninhar loops de `Do` colocando um loop dentro de outro. Você também pode aninhar diferentes tipos de estruturas de controle entre si. Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> A estrutura de `Do...Loop` oferece mais flexibilidade do que o [while... Instrução End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) porque ela permite que você decida se deseja encerrar o loop quando `condition` parar de ser `True` ou quando ele se tornar `True`pela primeira vez. Ele também permite que você teste `condition` no início ou no fim do loop.  
  
## <a name="exit-do"></a>Sair do  
 A instrução [Exit do](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer uma maneira alternativa de sair de um `Do…Loop`. `Exit Do` transfere o controle imediatamente para a instrução que segue a instrução `Loop`.  
  
 `Exit Do` geralmente é usado depois que alguma condição é avaliada, por exemplo, em uma estrutura de `If...Then...Else`. Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento. Um uso de `Exit Do` é testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número grande ou mesmo infinita de vezes. Você pode usar `Exit Do` para escapar o loop.  
  
 Você pode incluir qualquer número de instruções `Exit Do` em qualquer lugar em um `Do…Loop`.  
  
 Quando usado em loops de `Do` aninhados, `Exit Do` transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam a ser executadas até que a variável de `index` seja maior que 10. A cláusula `Until` está no final do loop.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma cláusula `While` em vez de uma cláusula `Until` e `condition` é testado no início do loop em vez de no final.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `condition` para o loop quando a variável `index` é maior que 100. No entanto, a instrução `If` no loop faz com que a instrução `Exit Do` pare o loop quando a variável de índice é maior que 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O método <xref:System.IO.File.OpenText%2A> abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres. Na condição de `Do...Loop`, o método <xref:System.IO.StreamReader.Peek%2A> da `StreamReader` determina se há caracteres adicionais.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
