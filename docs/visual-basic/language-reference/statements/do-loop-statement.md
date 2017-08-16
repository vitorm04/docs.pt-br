---
title: Fazer... Loop Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
dev_langs:
- VB
helpviewer_keywords:
- "conditional statements, Do…Loop"
- while statement, Do...Loop
- execution, conditional
- Do loops
- Until keyword, Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement
- Exit statement, in Do...Loop statements
- "loop structures, Do…Loop statements"
- do-while statements
- loops, exiting
- Loop keyword, Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: 37
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 96254ef47f1455f89df0e683dbd589d77af58c35
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="doloop-statement-visual-basic"></a>Instrução Do...Loop (Visual Basic)
Repete um bloco de instruções enquanto uma `Boolean` condição é `True` ou até que a condição se torne `True`.  
  
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
|`While`|Necessário a menos que `Until` seja usado. Repita o loop até `condition` é `False`.|  
|`Until`|Necessário a menos que `While` seja usado. Repita o loop até `condition` é `True`.|  
|`condition`|Opcional. Expressão `Boolean`. Se `condition` é `Nothing`, Visual Basic trata isso `False`.|  
|`statements`|Opcional. Uma ou mais declarações que são repetidas enquanto, ou até que, `condition` é `True`.|  
|`Continue Do`|Opcional. Transfere o controle para a próxima iteração do `Do` loop.|  
|`Exit Do`|Opcional. Transfere o controle do `Do` loop.|  
|`Loop`|Necessário. Finaliza a definição de `Do` loop.|  
  
## <a name="remarks"></a>Comentários  
 Use um `Do...Loop` estrutura quando quiser repetir um conjunto de declarações por um número indefinido de vezes, até que uma condição é satisfeita. Se você quiser repetir as declarações um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.  
  
 Você pode usar o `While` ou `Until` para especificar `condition`, mas não ambos.  
  
 Você pode testar `condition` somente uma vez, no início ou no final do loop. Se você testar `condition` no início do loop (no `Do` instrução), o loop não pode ser executado até mesmo uma vez. Se você testar no final do loop (no `Loop` instrução), o loop sempre é executado pelo menos uma vez.  
  
 A condição normalmente resulta de uma comparação entre dois valores, mas pode ser qualquer expressão que é avaliada como um [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`). Isso inclui os valores de outros tipos de dados, como tipos numéricos, que foram convertidos em `Boolean`.  
  
 Você pode aninhar `Do` loops colocando um loop dentro de outro. Você também pode aninhar diferentes tipos de estruturas de controle em si. Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
>  O `Do...Loop` estrutura lhe dá mais flexibilidade do que o [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) porque ela permite que você decida se deseja terminar o loop quando `condition` deixa de ser `True` ou quando ela for primeiro `True`. Ele também permite que você teste `condition` no início ou no final do loop.  
  
## <a name="exit-do"></a>Sair  
 O [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer uma maneira alternativa para encerrar um `Do…Loop`. `Exit Do`transfere o controle imediatamente para a instrução que segue o `Loop` instrução.  
  
 `Exit Do`é frequentemente usado após alguma condição é avaliada, por exemplo, em um `If...Then...Else` estrutura. Você talvez queira encerrar um loop se você detectar uma condição que torna desnecessária ou impossível de se continuar iterando, como um valor errôneo ou uma solicitação de encerramento. Um uso de `Exit Do` é testar uma condição que pode causar uma *loop infinito*, que é um loop que pode executar um número grande ou mesmo infinito de vezes. Você pode usar `Exit Do` para escapar do loop.  
  
 Você pode incluir qualquer número de `Exit Do` instruções em qualquer lugar em um `Do…Loop`.  
  
 Quando usado dentro aninhados `Do` loops, `Exit Do` transfere o controle para fora do loop interno e para o próximo nível mais alto de aninhamento.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, as instruções no loop continuam a executar até o `index` variável é maior que 10. O `Until` cláusula está no final do loop.  
  
 [!code-vb[VbVbalrStatements&#131;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa uma `While` cláusula em vez de um `Until` cláusula, e `condition` é testado no início do loop, em vez de no final.  
  
 [!code-vb[VbVbalrStatements&132;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `condition` interrompe o loop quando o `index` variável é maior que 100. O `If` instrução loop, no entanto, faz o `Exit Do` instrução para interromper o loop quando a variável de índice for maior que 10.  
  
 [!code-vb[VbVbalrStatements&#133;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto. O <xref:System.IO.File.OpenText%2A>método abre o arquivo e retorna um <xref:System.IO.StreamReader>que lê os caracteres.</xref:System.IO.StreamReader> </xref:System.IO.File.OpenText%2A> No `Do...Loop` condição, o <xref:System.IO.StreamReader.Peek%2A>método o `StreamReader` determina se há quaisquer caracteres adicionais.</xref:System.IO.StreamReader.Peek%2A>  
  
 [!code-vb[VbVbalrStatements&#134;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)

