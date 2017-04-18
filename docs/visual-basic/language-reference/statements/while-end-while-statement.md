---
title: While... End While Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
dev_langs:
- VB
helpviewer_keywords:
- While statement, While...End While
- While statement
- While...End While statements
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f9b002557c7d9fff02988c87b0404b6286fc061d
ms.lasthandoff: 03/13/2017

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
|`statements`|Opcional. Uma ou mais instruções após `While`, que cada tempo de execução `condition` é `True`.|  
|`Continue While`|Opcional. Transfere o controle para a próxima iteração do `While` bloco.|  
|`Exit While`|Opcional. Transfere o controle do `While` bloco.|  
|`End While`|Necessário. Finaliza a definição do bloco `While`.|  
  
## <a name="remarks"></a>Comentários  
 Use um `While...End While` estrutura quando você desejar repetir um conjunto de declarações por um número indefinido de vezes, enquanto uma condição permanece `True`. Se você quiser mais flexibilidade com onde você testar a condição ou o resultado é testá-lo para, talvez você prefira a [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md). Se você quiser repetir as declarações um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.  
  
> [!NOTE]
>  O `While` palavra-chave também é usada a [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), o [cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) e [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Se `condition` é `True`, todos os do `statements` execução até que o `End While` declaração é encontrada. Controle retorna para o `While` instrução, e `condition` é verificada novamente. Se `condition` ainda é `True`, o processo é repetido. Se ele tiver `False`, controle passa para a instrução que segue o `End While` instrução.  
  
 O `While` instrução sempre verifica a condição antes de iniciar o loop. Loop continua mantendo a condição `True`. Se `condition` é `False` quando você entra no loop, ela não executa uma única vez.  
  
 O `condition` normalmente resultados de uma comparação de dois valores, mas ele podem ser qualquer expressão que é avaliada como um [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`). Esta expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.  
  
 Você pode aninhar `While` loops colocando um loop dentro de outro. Você também pode aninhar diferentes tipos de estruturas de controle uma dentro da outra. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Saída ao mesmo tempo  
 O [sair enquanto](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer outra maneira de sair de um `While` loop. `Exit While`transfere o controle para a instrução que segue imediatamente o `End While` instrução.  
  
 Você normalmente usa `Exit While` depois que alguma condição é avaliada (por exemplo, em um `If...Then...Else` estrutura). Você talvez queira encerrar um loop se você detectar uma condição que torna desnecessária ou impossível de se continuar iterando, como um valor errôneo ou uma solicitação de encerramento. Você pode usar `Exit While` quando você testa uma condição que pode causar uma *loop infinito*, que é um loop que pode executar um número extremamente grande ou mesmo infinito de vezes. Você pode usar `Exit While` para escapar do loop.  
  
 Você pode colocar qualquer número de `Exit While` instruções em qualquer lugar no `While` loop.  
  
 Quando usado dentro aninhados `While` loops, `Exit While` transfere o controle para fora do loop interno e para o próximo nível mais alto de aninhamento.  
  
 O `Continue While` instrução imediatamente transfere o controle para a próxima iteração do loop. Para obter mais informações, consulte [continuar instrução](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam a executar até o `index` variável é maior que 10.  
  
 [!code-vb[VbVbalrStatements&#171;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `Continue While` e `Exit While` instruções.  
  
 [!code-vb[VbVbalrStatements&#172;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A>método abre o arquivo e retorna um <xref:System.IO.StreamReader>que lê os caracteres.</xref:System.IO.StreamReader> </xref:System.IO.File.OpenText%2A> No `While` condição, o <xref:System.IO.StreamReader.Peek%2A>método o `StreamReader` determina se o arquivo contém caracteres adicionais.</xref:System.IO.StreamReader.Peek%2A>  
  
 [!code-vb[VbVbalrStatements&#173;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)
