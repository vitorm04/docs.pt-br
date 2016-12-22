---
title: "Instru&#231;&#227;o While...End While (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.While"
  - "vb.While...EndWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução While"
  - "instrução While, While...End While"
  - "instruções While...End While"
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o While...End While (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Executa uma série de instruções enquanto uma condição determinada é `True`.  
  
## Sintaxe  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`condition`|Obrigatório.  Expressão de`Boolean` .  Se `condition` é `Nothing`, Visual Basic trata isso como `False`.|  
|`statements`|Opcional.  Uma ou mais instruções depois de `While`, que executam sempre `condition` são `True`.|  
|`Continue While`|Opcional.  Transfere controle para a próxima iteração do bloco de `While` .|  
|`Exit While`|Opcional.  Transfere controle fora do bloco de `While` .|  
|`End While`|Obrigatório.  Finaliza a definição do bloco `While`.|  
  
## Comentários  
 Use uma estrutura de `While...End While` quando você desejar repetir um conjunto de instruções um número indefinido de vezes, enquanto uma condição permanece `True`.  Se você deseja mais flexibilidade com onde você testa a condição ou resultado que você testa pelo, você pode preferir [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).  Se você desejar repetir as instruções um número definido de vezes, [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.  
  
> [!NOTE]
>  A palavra\-chave de `While` também é usado em [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), em [Ignorar cláusula While](../../../visual-basic/language-reference/queries/skip-while-clause.md) e em [Cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Se `condition` é `True`, qualquer `statements` é executado até que a declaração de `End While` seja encontrada.  O controle retorna à declaração de `While` , e `condition` é verificado novamente.  Se `condition` é ainda `True`, o processo é repetido.  Se é `False`, o controle passa para a declaração que segue a declaração de `End While` .  
  
 A declaração de `While` sempre verifica a condição antes de iniciar o loop.  Loop continua quando a condição permanece `True`.  Se `condition` é `False` quando você inserir o primeiro loop, não executa mesmo uma vez.  
  
 `condition` normalmente resulta de uma comparação entre dois valores, mas pode ser qualquer expressão avaliada como [Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md) um valor \(`True` ou `False`\).  Esta expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que é convertido para `Boolean`.  
  
 Você pode aninhar loop de `While` colocando um loop dentro de outro.  Você também pode aninhar diferentes tipos de estruturas de controle uma dentro da outra.  Para mais informações, consulte [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## Quando deixar  
 A declaração de [Quando deixar](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer uma outra maneira para sair de um loop de `While` .  De`Exit While` transfere controle imediatamente para a declaração que segue a declaração de `End While` .  
  
 Você normalmente usa `Exit While` após alguma condição é avaliada \(por exemplo, em um estrutura de `If...Then...Else` \).  Você pode querer sair de um loop se você detectar uma condição que se faz desnecessária ou impossível de se continuar iterando, como um valor errôneo ou uma exigência de finalização.  Você pode usar `Exit While` quando você testar para uma condição que pode causar *um loop interminável*, que é um loop que é um número extremamente grande ou mesmo infinito de vezes.  Você pode usar `Exit While` para escapar o loop.  
  
 Você pode colocar qualquer número de declarações de `Exit While` em qualquer lugar no loop de `While` .  
  
 Quando usado dentro de loops aninhados de `While` , transfere controle de `Exit While` fora do loop mais interno e no de alto nível de aninhamento.  
  
 Declaração de `Continue While` do transfere controle imediatamente para a próxima iteração do loop.  Para mais informações, consulte [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## Exemplo  
 Em o exemplo, as instruções no loop continuam a ser executado até que a variável de `index` é maior que 10.  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## Exemplo  
 O exemplo a seguir ilustra o uso das instruções de `Continue While` e de `Exit While` .  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## Exemplo  
 O exemplo a seguir lê todas as linhas em um arquivo de texto.  O método de <xref:System.IO.File.OpenText%2A> abre o arquivo e retorna <xref:System.IO.StreamReader> que lê caracteres.  Em a condição de `While` , o método de <xref:System.IO.StreamReader.Peek%2A> de `StreamReader` determina se o arquivo contém caracteres adicionais.  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## Consulte também  
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)