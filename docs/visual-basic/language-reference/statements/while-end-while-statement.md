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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965807"
---
# <a name="whileend-while-statement-visual-basic"></a>Instrução While...End While (Visual Basic)
Executa uma série de instruções desde que uma determinada condição seja `True`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`condition`|Necessário. Expressão `Boolean`. Se `condition` `False`for `Nothing`, Visual Basic tratará como.|  
|`statements`|Opcional. Uma ou mais instruções a `While`seguir, que são executadas `condition` toda `True`vez são.|  
|`Continue While`|Opcional. Transfere o controle para a próxima iteração do `While` bloco.|  
|`Exit While`|Opcional. Transfere o `While` controle do bloco.|  
|`End While`|Necessário. Finaliza a definição do bloco `While`.|  
  
## <a name="remarks"></a>Comentários  
 Use uma `While...End While` estrutura quando você quiser repetir um conjunto de instruções um número indefinido de vezes, desde que uma condição permaneça `True`. Se você quiser mais flexibilidade com o local em que você testa a condição ou o resultado para o qual você o testa, talvez prefira o [... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md). Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) é geralmente uma opção melhor.  
  
> [!NOTE]
> A `While` palavra-chave também é usada no... [ Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), a [cláusula Skip while](../../../visual-basic/language-reference/queries/skip-while-clause.md) e a [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Se `condition` `statements` `End While` for `True`, toda a execução até que a instrução seja encontrada. Em seguida, o `While` controle retorna à instrução e `condition` é verificado novamente. Se `condition` ainda`True`for, o processo será repetido. Se for `False`, o controle passará para a instrução que segue `End While` a instrução.  
  
 A `While` instrução sempre verifica a condição antes de iniciar o loop. O loop continua enquanto a condição permanece `True`. Se `condition` for`False` , quando você inserir o loop pela primeira vez, ele não será executado mesmo uma.  
  
 Normalmente `condition` , os resultados de uma comparação de dois valores, mas podem ser qualquer expressão avaliada como um valor de [tipo de dados](../../../visual-basic/language-reference/data-types/boolean-data-type.md) booliano `False`(`True` ou). Essa expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.  
  
 Você pode aninhar `While` loops colocando um loop dentro de outro. Você também pode aninhar diferentes tipos de estruturas de controle entre si. Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Sair enquanto  
 A instrução [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer outra maneira de sair de `While` um loop. `Exit While`transfere imediatamente o controle para a instrução que `End While` segue a instrução.  
  
 Normalmente, você `Exit While` usa depois que alguma condição é avaliada (por exemplo `If...Then...Else` , em uma estrutura). Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento. Você pode usar `Exit While` ao testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número muito grande ou mesmo infinito de vezes. Em seguida, você `Exit While` pode usar para escapar o loop.  
  
 Você pode inserir qualquer número de `Exit While` instruções `While` em qualquer lugar no loop.  
  
 Quando usado em loops `While` aninhados `Exit While` , o transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.  
  
 A `Continue While` instrução transfere imediatamente o controle para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam a ser executadas até que `index` a variável seja maior que 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso das `Continue While` instruções `Exit While` e.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A> método abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres. Na condição, o <xref:System.IO.StreamReader.Peek%2A> método de `StreamReader` determina se o arquivo contém caracteres adicionais. `While`  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
