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
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942993"
---
# <a name="doloop-statement-visual-basic"></a>Instrução Do...Loop (Visual Basic)
Repete um bloco de instruções enquanto uma `Boolean` condição é `True` ou até que a condição se `True`torne.  
  
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
|`While`|Necessário a menos que `Until` seja usado. Repita o loop até `condition` que `False`esteja.|  
|`Until`|Necessário a menos que `While` seja usado. Repita o loop até `condition` que `True`esteja.|  
|`condition`|Opcional. Expressão `Boolean`. Se `condition` `False`for `Nothing`, Visual Basic tratará como.|  
|`statements`|Opcional. Uma ou mais instruções repetidas enquanto, ou até, `condition` são. `True`|  
|`Continue Do`|Opcional. Transfere o controle para a próxima iteração do `Do` loop.|  
|`Exit Do`|Opcional. Transfere o controle do `Do` loop.|  
|`Loop`|Necessário. Encerra a definição do `Do` loop.|  
  
## <a name="remarks"></a>Comentários  
 Use uma `Do...Loop` estrutura quando você quiser repetir um conjunto de instruções um número indefinido de vezes, até que uma condição seja satisfeita. Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) é geralmente uma opção melhor.  
  
 Você pode usar o `While` ou `Until` o para `condition`especificar, mas não ambos.  
  
 Você pode testar `condition` apenas uma vez, no início ou no fim do loop. Se você testar `condition` no início do loop ( `Do` na instrução), o loop pode não ser executado mesmo uma vez. Se você testar no final do loop (na `Loop` instrução), o loop sempre será executado pelo menos uma vez.  
  
 A condição geralmente resulta de uma comparação de dois valores, mas pode ser qualquer expressão avaliada como um valor de [tipo de dados](../../../visual-basic/language-reference/data-types/boolean-data-type.md) booliano`True` ( `False`ou). Isso inclui valores de outros tipos de dados, como tipos numéricos, que foram convertidos `Boolean`em.  
  
 Você pode aninhar `Do` loops colocando um loop dentro de outro. Você também pode aninhar diferentes tipos de estruturas de controle entre si. Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> A `Do...Loop` estrutura oferece mais flexibilidade do que o [while... Instrução End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) porque ela permite que você decida se deseja encerrar o loop quando `condition` parar de `True` ser ou quando ele se `True`tornar o primeiro. Ele também permite que você teste `condition` no início ou no fim do loop.  
  
## <a name="exit-do"></a>Sair do  
 A instrução [Exit do](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer uma maneira alternativa de sair de `Do…Loop`um. `Exit Do`transfere o controle imediatamente para a instrução que `Loop` segue a instrução.  
  
 `Exit Do`geralmente é usado depois que alguma condição é avaliada, por exemplo `If...Then...Else` , em uma estrutura. Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento. Um uso de `Exit Do` é testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número grande ou mesmo infinito de vezes. Você pode usar `Exit Do` para escapar o loop.  
  
 Você pode incluir qualquer número de `Exit Do` instruções em qualquer lugar `Do…Loop`em um.  
  
 Quando usado em loops `Do` aninhados `Exit Do` , o transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam a ser executadas até que `index` a variável seja maior que 10. A `Until` cláusula está no final do loop.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `While` uma cláusula em vez `Until` de uma cláusula `condition` e é testada no início do loop em vez de no final.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `condition` interrompe o loop quando a `index` variável é maior que 100. No `If` entanto, a instrução no loop faz com `Exit Do` que a instrução pare o loop quando a variável de índice for maior que 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A> método abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres. Na condição, o <xref:System.IO.StreamReader.Peek%2A> método de `StreamReader` determina se há caracteres adicionais. `Do...Loop`  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
