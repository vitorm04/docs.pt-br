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
ms.openlocfilehash: 9f46a6ec65faef4448bdd25e30a6cc0c605cd0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whileend-while-statement-visual-basic"></a>Instrução While...End While (Visual Basic)
Executa uma série de instruções desde que uma determinada condição é `True`.  
  
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
|`condition`|Necessário. Expressão `Boolean`. Se `condition` é `Nothing`, Visual Basic trata isso `False`.|  
|`statements`|Opcional. Um ou mais instruções após `While`, qual executar sempre `condition` é `True`.|  
|`Continue While`|Opcional. Transfere o controle para a próxima iteração do `While` bloco.|  
|`Exit While`|Opcional. Transfere o controle do `While` bloco.|  
|`End While`|Necessário. Finaliza a definição do bloco `While`.|  
  
## <a name="remarks"></a>Comentários  
 Use um `While...End While` estrutura quando quiser repetir um conjunto de declarações por um número indefinido de vezes, enquanto uma condição permanece `True`. Se você quiser mais flexibilidade com a qual você testar a condição ou o resultado que você testá-lo para, talvez você prefira o [fazer... Loop instrução](../../../visual-basic/language-reference/statements/do-loop-statement.md). Se você deseja repetir as instruções de um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.  
  
> [!NOTE]
>  O `While` palavra-chave também é usada a [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), o [ignorar cláusula While](../../../visual-basic/language-reference/queries/skip-while-clause.md) e [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Se `condition` é `True`, todos os do `statements` execução até que o `End While` instrução for encontrada. Controle retorna para o `While` instrução, e `condition` é verificada novamente. Se `condition` ainda é `True`, o processo é repetido. Se ele tiver `False`, controle passa para a instrução que segue o `End While` instrução.  
  
 O `While` instrução sempre verifica a condição antes de iniciar o loop. Loop continua mantendo a condição `True`. Se `condition` é `False` quando você insere o loop pela primeira vez, ele não é executado até mesmo uma vez.  
  
 O `condition` geralmente os resultados de uma comparação de dois valores, mas ele podem ser qualquer expressão que é avaliada como um [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`). Esta expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.  
  
 Você pode aninhar `While` loops colocando um loop dentro de outra. Você também pode aninhar diferentes tipos de estruturas de controle dentro de uma outra. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Saída ao mesmo tempo  
 O [sair enquanto](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer a outra forma de sair de um `While` loop. `Exit While` transfere o controle para a instrução que segue imediatamente o `End While` instrução.  
  
 Você normalmente usa `Exit While` depois que alguma condição é avaliada (por exemplo, em um `If...Then...Else` estrutura). Você talvez queira encerrar um loop se você detectar uma condição que facilita o desnecessária ou impossível continuar iterando, como um valor errado ou uma solicitação de encerramento. Você pode usar `Exit While` quando você testa uma condição que pode causar uma *loop infinito*, que é um loop que pode executar um número muito grande ou mesmo infinito de vezes. Você pode usar `Exit While` para escapar do loop.  
  
 Você pode colocar qualquer número de `Exit While` instruções em qualquer lugar no `While` loop.  
  
 Quando usado dentro aninhados `While` loops, `Exit While` transfere controle fora do loop interno e para o próximo nível mais alto de aninhamento.  
  
 O `Continue While` instrução imediatamente transfere o controle para a próxima iteração do loop. Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam em execução até que o `index` variável é maior que 10.  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `Continue While` e `Exit While` instruções.  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A> método abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres. No `While` condição, o <xref:System.IO.StreamReader.Peek%2A> método o `StreamReader` determina se o arquivo contém caracteres adicionais.  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de Loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
