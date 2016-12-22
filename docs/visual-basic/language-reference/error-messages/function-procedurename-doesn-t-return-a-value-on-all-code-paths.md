---
title: "A fun&#231;&#227;o &#39;&lt;procedurename&gt;&#39; n&#227;o retorna um valor em todos os caminhos de c&#243;digo | Microsoft Docs"
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
  - "bc42105"
  - "vbc42105"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42105"
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A fun&#231;&#227;o &#39;&lt;procedurename&gt;&#39; n&#227;o retorna um valor em todos os caminhos de c&#243;digo
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Função '\<procedurename\> ' não retorna um valor em todos os caminhos de código.Está faltando uma instrução 'Return'?  
  
 A `Function` procedimento tem pelo menos um caminho possível através de seu código que não retorna um valor.  
  
 Você pode retornar um valor de um `Function` procedimento em qualquer uma das seguintes maneiras:  
  
-   Incluir o valor em um [Instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Atribuir o valor para o `Function` procedimento de nome e executar um `Exit Function` instrução.  
  
-   Atribuir o valor para o `Function` procedimento de nome e executar o `End Function` instrução.  
  
 Se passa o controle para `Exit Function` ou `End Function` e você não tiver atribuído qualquer valor para o nome do procedimento, o procedimento retorna o valor padrão do tipo de dados de retorno.  Para obter mais informações, consulte "Comportamento" em [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Por padrão, este mensagem é um aviso.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:** BC42105  
  
### Para corrigir este erro  
  
-   Verifique sua lógica de Fluxo de Controle e certifique\-se de que você atribuiu um valor de antes cada instrução que produz um retorno.  
  
     É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar a instrução `Return` sempre.  Se você fizer isso, a última instrução antes de `End Function` deve ser uma instrução `Return`.  
  
## Consulte também  
 [Procedimentos de função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)