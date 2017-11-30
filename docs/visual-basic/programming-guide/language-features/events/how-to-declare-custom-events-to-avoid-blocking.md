---
title: Como declarar eventos personalizados para evitar bloqueio (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a36c855efb67752674615a61f2fa701974ce5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>Como declarar eventos personalizados para evitar bloqueio (Visual Basic)
Há várias circunstâncias quando é importante que um manipulador de eventos não bloquear manipuladores de eventos subsequentes. Eventos personalizados permitem que o evento chame seus manipuladores de eventos de forma assíncrona.  
  
 Por padrão, o campo de repositório de backup para uma declaração de evento é um delegado multicast que serialmente combina todos os manipuladores de eventos. Isso significa que, se um manipulador levar muito tempo para concluir, ele bloqueia os outros manipuladores até que ela seja concluída. (Manipuladores de eventos bem comportados nunca devem executar operações longas ou possivelmente de bloqueio.)  
  
 Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar um evento personalizado para executar os manipuladores de eventos de forma assíncrona.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o `AddHandler` acessador adiciona o representante para cada manipulador do `Click` evento para um <xref:System.Collections.ArrayList> armazenados no `EventHandlerList` campo.  
  
 Quando o código dispara o `Click` evento, o `RaiseEvent` acessador chama todos os representantes de manipulador de eventos usando de forma assíncrona o <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> método. Esse método chama cada manipulador em um thread de trabalho e retorna imediatamente, portanto manipuladores não é possível bloquear um ao outro.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Collections.ArrayList>  
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>  
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Como declarar eventos personalizados para conservar memória](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
