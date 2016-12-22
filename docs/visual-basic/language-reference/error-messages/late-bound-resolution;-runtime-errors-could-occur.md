---
title: "Resolu&#231;&#227;o de associa&#231;&#227;o tardia; poderiam ocorrer erros de tempo de execu&#231;&#227;o | Microsoft Docs"
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
  - "vbc42017"
  - "BC42017"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42017"
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Resolu&#231;&#227;o de associa&#231;&#227;o tardia; poderiam ocorrer erros de tempo de execu&#231;&#227;o
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um objeto é atribuído a uma variável declarada para ser do [Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Ao declarar uma variável como `Object`,o compilador deve executar *ligação tardia* ,o que causa operações extras em tempo de execução.  Isso também expõe sua aplicação a potenciais erros em tempo de execução.  Por exemplo, se você atribuir uma <xref:System.Windows.Forms.Form> à variável `Object` e, em seguida, tentar acessar a propriedade <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>, o tempo de execução gera uma <xref:System.MemberAccessException> porque a classe <xref:System.Windows.Forms.Form> não expõe uma propriedade `NameTable`.  
  
 Se você declarar a variável de um tipo específico, o compilador pode executar  *ligação antecipada* em tempo de compilação.  Isso resulta em melhor desempenho, acesso controlado aos membros do tipo específico e melhor legibilidade do seu código.  
  
 Por padrão, essa é uma mensagem de aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC42017  
  
### Para corrigir este erro  
  
-   Se possível, declare a variável de um tipo específico.  
  
## Consulte também  
 [Associação antecipada e tardia](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [Declaração de variável do objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)