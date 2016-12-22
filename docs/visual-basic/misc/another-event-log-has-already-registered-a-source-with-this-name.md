---
title: "Outro log de eventos j&#225; registrou uma fonte com este nome | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Outro log de eventos j&#225; registrou uma fonte com este nome
Foi feita uma tentativa para gravar uma entrada em um log de eventos onde a origem especificada é registrada com outro log de eventos.  
  
 Você deve definir o <xref:System.Diagnostics.EventLog.Source%2A> propriedade de seu <xref:System.Diagnostics.EventLog> instância do componente antes de seu componente grava uma entrada em um log. Quando isso acontece, o sistema verifica se a fonte especificada está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A> se necessário.  
  
### Para corrigir este erro  
  
1.  Remover a associação da fonte com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> ou o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> método.  
  
2.  Registre o código\-fonte com o novo log.  
  
## Consulte também  
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/pt-br/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/pt-br/948ff920-a739-4e66-a191-ee951512d42c)