---
title: Instrução While...End While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582264"
---
# <a name="whileend-while-statement-visual-basic"></a>Instrução While...End While (Visual Basic)
Executa uma série de instruções desde que uma determinada condição seja `True`.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`condition`|Necessário. Expressão `Boolean`. Se `condition` for `Nothing`, Visual Basic o tratará como `False`.|  
|`statements`|Opcional. Uma ou mais instruções a seguir `While`, que são executadas sempre que `condition` é `True`.|  
|`Continue While`|Opcional. Transfere o controle para a próxima iteração do bloco de `While`.|  
|`Exit While`|Opcional. Transfere o controle do bloco de `While`.|  
|`End While`|Necessário. Finaliza a definição do bloco `While`.|  
  
## <a name="remarks"></a>Comentários  
 Use uma estrutura de `While...End While` quando quiser repetir um conjunto de instruções um número indefinido de vezes, desde que uma condição permaneça `True`. Se você quiser mais flexibilidade com o local em que você testa a condição ou o resultado para o qual você o testa, talvez prefira o [... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md). Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) é geralmente uma opção melhor.  
  
> [!NOTE]
> A palavra-chave `While` também é usada no... [ Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), a [cláusula Skip while](../../../visual-basic/language-reference/queries/skip-while-clause.md) e a [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Se `condition` for `True`, todos os `statements` executados até que a instrução `End While` seja encontrada. Em seguida, o controle retorna à instrução `While` e `condition` é verificado novamente. Se `condition` ainda estiver `True`, o processo será repetido. Se for `False`, o controle passará para a instrução que segue a instrução `End While`.  
  
 A instrução `While` sempre verifica a condição antes de iniciar o loop. O loop continua enquanto a condição permanece `True`. Se `condition` for `False` quando você inserir o loop pela primeira vez, ele não será executado de uma maneira.  
  
 O `condition` geralmente resulta de uma comparação de dois valores, mas pode ser qualquer expressão avaliada como um valor de [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`). Essa expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.  
  
 Você pode aninhar loops de `While` colocando um loop dentro de outro. Você também pode aninhar diferentes tipos de estruturas de controle entre si. Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Sair enquanto  
 A instrução [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer outra maneira de sair de um loop de `While`. `Exit While` transfere imediatamente o controle para a instrução que segue a instrução `End While`.  
  
 Normalmente, você usa `Exit While` depois que alguma condição é avaliada (por exemplo, em uma estrutura de `If...Then...Else`). Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento. Você pode usar `Exit While` ao testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número muito grande ou mesmo infinito de vezes. Em seguida, você pode usar `Exit While` para escapar o loop.  
  
 Você pode inserir qualquer número de instruções `Exit While` em qualquer lugar no loop `While`.  
  
 Quando usado em loops de `While` aninhados, `Exit While` transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.  
  
 A instrução `Continue While` transfere imediatamente o controle para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam a ser executadas até que a variável de `index` seja maior que 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso das instruções `Continue While` e `Exit While`.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O método <xref:System.IO.File.OpenText%2A> abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres. Na condição de `While`, o método <xref:System.IO.StreamReader.Peek%2A> da `StreamReader` determina se o arquivo contém caracteres adicionais.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
