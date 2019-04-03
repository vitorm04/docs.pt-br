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
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843702"
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
|`condition`|Necessário. Expressão `Boolean`. Se `condition` está `Nothing`, Visual Basic trata isso `False`.|  
|`statements`|Opcional. Um ou mais instruções após `While`, que cada tempo de execução `condition` é `True`.|  
|`Continue While`|Opcional. Transfere o controle para a próxima iteração do `While` bloco.|  
|`Exit While`|Opcional. Transfere o controle do `While` bloco.|  
|`End While`|Necessário. Finaliza a definição do bloco `While`.|  
  
## <a name="remarks"></a>Comentários  
 Use uma `While...End While` estrutura quando desejar repetir um conjunto de declarações por um número indefinido de vezes, desde que uma condição permanece `True`. Se você quiser mais flexibilidade com onde você testar a condição ou o que resulta é testá-lo para, talvez você prefira o [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md). Se você quiser repetir as declarações de um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.  
  
> [!NOTE]
>  O `While` palavra-chave também é usado no [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), o [cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) e o [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Se `condition` está `True`, todos os da `statements` execução até que o `End While` instrução for encontrada. Controlar, em seguida, retorna para o `While` instrução, e `condition` é verificada novamente. Se `condition` ainda é `True`, o processo é repetido. Se ele tiver `False`, controle passa para a instrução que segue o `End While` instrução.  
  
 O `While` instrução sempre verifica a condição antes de iniciar o loop. Um loop continua enquanto a condição permaneça `True`. Se `condition` é `False` quando você entra pela primeira vez no loop, ele não será executado até mesmo uma vez.  
  
 O `condition` normalmente, os resultados de uma comparação entre dois valores, mas ele podem ser qualquer expressão que é avaliada como uma [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`). Esta expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.  
  
 Você pode aninhar `While` loops colocando um loop dentro de outra. Você também pode aninhar diferentes tipos de estruturas de controle dentro uns dos outros. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Saída ao mesmo tempo  
 O [sair enquanto](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer a outra maneira de se sair um `While` loop. `Exit While` transfere o controle para a instrução que segue imediatamente o `End While` instrução.  
  
 Normalmente, você usa `Exit While` depois que alguma condição é avaliada (por exemplo, em um `If...Then...Else` estrutura). Você talvez queira encerrar um loop se você detectar uma condição que torna desnecessária ou impossível continuar a iteração, como um valor errado ou uma solicitação de encerramento. Você pode usar `Exit While` quando você testa uma condição que poderia causar uma *um loop infinito*, que é um loop que possa ser executada um número muito grande ou mesmo infinito de vezes. Você pode usar `Exit While` para escapar do loop.  
  
 Você pode colocar qualquer número de `Exit While` as instruções no `While` loop.  
  
 Quando usado dentro aninhados `While` loops, `Exit While` transfere o controle para fora do loop interno e para o próximo nível mais alto de aninhamento.  
  
 O `Continue While` imediatamente transfere o controle para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam em execução até que o `index` variável é maior que 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `Continue While` e `Exit While` instruções.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A> abre o arquivo de método e retorna um <xref:System.IO.StreamReader> que lê os caracteres. No `While` condição, o <xref:System.IO.StreamReader.Peek%2A> método o `StreamReader` determina se o arquivo contém caracteres adicionais.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
