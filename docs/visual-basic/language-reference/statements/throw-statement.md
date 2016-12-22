---
title: "Instru&#231;&#227;o Throw (Visual Basic) | Microsoft Docs"
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
  - "vb.Throw"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tratamento de exceção, Instrução throw"
  - "tratamento de exceção, não estruturados"
  - "instrução On Error, lançando exceções"
  - "tratamento estruturado de exceções, instruções throw"
  - "Instrução throw"
  - "Instrução throw, sobre instruções throw"
  - "lançando exceções"
  - "lançando exceções, Instrução throw"
  - "tratamento de exceções de try-catch, instruções throw"
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Throw (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lança uma exceção dentro de um procedimento.  
  
## Sintaxe  
  
```  
Throw [ expression ]  
```  
  
## Parte  
 `expression`  
 Fornece informações sobre a exceção a ser gerada.  Opcional quando residente em uma instrução `Catch`, necessária caso contrário.  
  
## Comentários  
 A instrução `Throw` gera uma exceção que você pode manipular com código de manipulação de exceção estruturado \(`Try`... `Catch`... `Finally`\) ou código de manipulação de exceção não estruturado \(`On Error GoTo`\).  Você pode usar a instrução `Throw` para interceptar erros em seu código, pois o Visual Basic move para a parte superior da pilha de chamadas até encontrar o código de manipulação de exceção apropriado.  
  
 Uma instrução `Throw` com nenhuma expressão somente pode ser usada em uma instrução `Catch`, na qual a exceção atualmente sendo tratada pela instrução `Catch` lança novamente a exceção.  
  
 A instrução `Throw` redefine o pilha de chamadas para a exceção `expression`.  Se `expression` não for fornecido, o pilha de chamadas é deixada inalterada.  Você pode acessar a pilha de chamadas para a exceção através da propriedade <xref:System.Exception.StackTrace%2A>.  
  
## Exemplo  
 O código a seguir utiliza a instrução `Throw` para acionar uma exceção:  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## Requisitos  
 **Namespace:** [VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Módulo:** `Interaction`  
  
 **Assembly:** Visual Basic Runtime Library \(in Microsoft.VisualBasic.dll\)  
  
## Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)