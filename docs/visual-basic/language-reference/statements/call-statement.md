---
title: "Instru&#231;&#227;o Call (Visual Basic) | Microsoft Docs"
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
  - "vb.Call"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Call"
  - "procedimentos, instrução Call"
  - "procedimentos, Chamando "
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Call (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Transfere o controle para uma `Function`, `Sub`, ou um procedimento de biblioteca de vínculo dinâmico \(DLL\).  
  
## Sintaxe  
  
```  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## Partes  
 `procedureName`  
 Necessário.  Nome do procedimento para chamar.  
  
 `argumentList`  
 Opcional.  Lista de variáveis ou expressões representando os argumentos que são passados para o procedimento quando ele é chamado.  Múltiplos argumentos são separados por vírgulas.  Se você incluir `argumentList`, coloque\-o entre parênteses.  
  
## Comentários  
 Você pode usar o `Call` palavra\-chave quando você chamar um procedimento.  Para a maioria das chamadas de procedimento, não é necessário usar essa palavra\-chave.  
  
 Você normalmente usa o `Call` palavra\-chave quando a expressão de chamada não iniciar com um identificador.  Usar o `Call` palavra\-chave para outros usos não é recomendado.  
  
 Se o procedimento retorna um valor de `Call` instrução descarta.  
  
## Exemplo  
 O código a seguir mostra dois exemplos onde a `Call` palavra\-chave é necessária para chamar um procedimento.  Nos dois exemplos, a expressão de chamada não começa com um identificador.  
  
 [!code-vb[VbVbalrStatements#97](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/call-statement_1.vb)]  
  
## Consulte também  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)