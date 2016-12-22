---
title: "A propriedade &#39;&lt;propertyname&gt;&#39; n&#227;o retorna um valor em todos os caminhos de c&#243;digo | Microsoft Docs"
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
  - "bc42107"
  - "vbc42107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42107"
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A propriedade &#39;&lt;propertyname&gt;&#39; n&#227;o retorna um valor em todos os caminhos de c&#243;digo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A propriedade '\<propertyname\> ' não retorna um valor em todos os caminhos de código.Uma exceção de referência nula pode ocorrer no tempo de execução quando o resultado é usado.  
  
 Um procedimento de propriedade `Get` tem, pelo menos, um caminho possível pelo seu código que não retorna um valor.  
  
 Você pode retornar um valor a partir de um procedimento de propriedade `Get` de uma das seguintes maneiras:  
  
-   Atribua o valor ao nome da propriedade e, então, execute uma instrução `Exit Property`.  
  
-   Atribua o valor ao nome da propriedade e, então, execute a instrução `End Get`.  
  
-   Incluir o valor em um [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Se o controle passar para `Exit Property` ou `End Get` e você não tiver atribuído qualquer valor para o nome da propriedade, o procedimento `Get` retorna o valor padrão do tipo de dados da propriedade.  Para obter mais informações, consulte "comportamento" no [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Por padrão, essa é uma mensagem de aviso.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC42107  
  
### Para corrigir este erro  
  
-   Verifique sua lógica de Fluxo de Controle e certifique\-se de que você atribuiu um valor de antes cada instrução que produz um retorno.  
  
     É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar a instrução `Return` sempre.  Se você fizer isso, a última instrução antes de `End Get` deve ser uma instrução `Return`.  
  
## Consulte também  
 [Procedimentos de propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)