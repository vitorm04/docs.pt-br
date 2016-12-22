---
title: "A vari&#225;vel &#39;&lt;variablename&gt;&#39; &#233; usada antes de receber um valor | Microsoft Docs"
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
  - "vbc42104"
  - "BC42104"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42104"
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A vari&#225;vel &#39;&lt;variablename&gt;&#39; &#233; usada antes de receber um valor
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A variável '\<variablename\> ' é usada antes que ele foi atribuído um valor.Uma exceção de referência nula pode ocorrer durante a execução.  
  
 Um aplicativo tem pelo menos um caminho possível pelo seu código que lê uma variável antes que qualquer valor seja atribuído a ela.  
  
 Se ainda não se atribuiu um valor a uma variável, ela armazena o valor padrão do seu tipo de dado.  Para um tipo de dado de referência, o valor padrão é [nada](../../../visual-basic/language-reference/nothing.md).  Ao ler uma variável de referência que tem valor `Nothing` pode causar <xref:System.NullReferenceException> em algumas circunstâncias.  
  
 Por padrão, essa é uma mensagem de aviso.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC42104  
  
### Para corrigir este erro  
  
-   Verifique sua lógica de Fluxo de Controle e certifique\-se de que a variável tem um valor válido antes de transmitir o controle para qualquer instrução que a lê.  
  
-   Uma maneira para garantir que a variável sempre tenha um valor válido é inicializá\-la como parte da sua declaração.  Consulte "Inicialização" no [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## Consulte também  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Solucionando problemas de variáveis](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)