---
title: "Diretiva #Const | Microsoft Docs"
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
  - "vb.#Const"
  - "#vb.Const"
  - "#Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Diretiva #Const"
  - "compilação condicional, Diretivas ()"
  - "diretiva Const (#Const)"
  - "instrução Const [Visual Basic], diretiva (#Const)"
  - "constantes, diretiva Const"
  - "constantes, declarando"
  - "declarando constantes, Diretiva #const"
  - "compilador do Visual Basic, diretivas de compilador"
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Diretiva #Const
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Define constantes condicionais de compilador para Visual Basic.  
  
## Sintaxe  
  
```  
#Const constname = expression  
```  
  
## Partes  
 `constname`  
 Obrigatório.  Nome da constante que está sendo definido.  
  
 `expression`  
 Obrigatório.  Literal, outra constante condicional de compilador, ou qualquer combinação que inclua qualquer ou todos os operadores aritméticos ou lógicos exceto `Is`.  
  
## Comentários  
 Constantes condicionais de compilador são sempre particulares ao arquivo no qual elas aparecem.  Você não pode criar constantes de compilador públicas usando a diretriz `#Const`; você as cria apenas na interface de usuário ou com a opção de compilador `/define`.  
  
 Você pode usar literais e constantes condicionais de compilador em `expression`.  Usar uma condição padrão definida com `Const` causa um erro.  Inversamente, você pode usar constantes definidas pela palavra\-chave `#Const` para compilação adicional.  Constantes também podem ser indefinidas, caso no qual elas possuem um valor de `Nothing`.  
  
## Exemplo  
 Este exemplo usa a diretiva `#Const`.  
  
 [!CODE [VbVbalrConditionalComp#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrConditionalComp#3)]  
  
## Consulte também  
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [Diretivas \#If...Then...\#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)