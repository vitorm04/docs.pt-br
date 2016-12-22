---
title: "Instru&#231;&#227;o Resume | Microsoft Docs"
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
  - "vb.Resume"
  - "vb.ResumeNext"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Error, e instrução Resume"
  - "erros [Visual Basic], retomando após"
  - "execução"
  - "execução, retomando"
  - "Próxima instrução, Resume"
  - "instrução Resume Next"
  - "instrução Resume"
  - "instrução Resume, sintaxe"
  - "erros de tempo de execução, retomando após"
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Resume
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Continua a execução após a conclusão de uma rotina de tratamento de erros.  
  
 Sugerimos que você use manipulação de exceção estruturada no seu código sempre que possível, em vez de usar o tratamento de exceção não estruturada e o `On Error` e `Resume` instruções.  Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Sintaxe  
  
```  
Resume [ Next | line ]  
```  
  
## Partes  
 `Resume`  
 Obrigatório.  Se o erro ocorreu no mesmo procedimento como o manipulador de erro, a execução reinicia com a instrução que causou o erro.  Se o erro ocorreu em um procedimento chamado, a execução reinicia com a instrução que a última chamada fora do procedimento que contém a rotina de tratamento de erros.  
  
 `Next`  
 Opcional.  Se o erro ocorreu no mesmo procedimento como o manipulador de erro, a execução reinicia com a declaração imediatamente seguinte a instrução que causou o erro.  Se o erro ocorreu em um procedimento chamado, a execução reinicia com a declaração imediatamente seguinte a instrução que a última chamada fora do procedimento que contém a rotina de tratamento de erros \(ou `On Error Resume Next` instrução\).  
  
 `line`  
 Opcional.  A execução reinicia na linha especificada nas caixas necessário `line` argumento.  O `line` argumento é um rótulo de linha ou o número da linha e deve estar no mesmo procedimento que o manipulador de erro.  
  
## Comentários  
  
> [!NOTE]
>  Recomendamos que você use manipulação de exceção estruturada no seu código sempre que possível, em vez de usar o tratamento de exceção não estruturada e o `On Error` e `Resume` instruções.  Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Se você usar um `Resume` instrução em qualquer lugar diferente em uma rotina de tratamento de erros, um erro ocorre.  
  
 O `Resume` instrução não pode ser usada em qualquer procedimento que contém um `Try...Catch...Finally` instrução.  
  
## Exemplo  
 Este exemplo usa a `Resume` a instrução para terminar em um procedimento de tratamento de erros e, em seguida, continuar a execução com a instrução que causou o erro.  O número de erro 55 é gerado para ilustrar o uso da `Resume` instrução.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## Requisitos  
 **Namespace:** [VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library \(in Microsoft.VisualBasic.dll\)  
  
## Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)