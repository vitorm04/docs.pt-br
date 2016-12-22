---
title: "Registrando informa&#231;&#245;es em log a partir do aplicativo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "aplicativos [Visual Basic], registrando informações de"
  - "exemplos [Visual Basic], registrando informações de aplicativo"
  - "Objeto de log"
  - "log"
  - "Objeto My.Application.Log"
  - "Objeto My.Log"
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Registrando informa&#231;&#245;es em log a partir do aplicativo (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta seção contém os tópicos que abordam como registrar informações de seu aplicativo usando o objeto `My.Application.Log` ou `My.Log` e como estender os recursos de log do aplicativo.  
  
 O objeto `Log` fornece métodos para gravar informações nos ouvintes de log do aplicativo, e a propriedade avançada `TraceSource` do objeto de `Log` fornece informações de configuração detalhadas.  O objeto `Log` é configurado pelo arquivo de configuração do aplicativo.  
  
 O objeto `My.Log` está disponível somente para aplicativos ASP.NET.  Para aplicativos cliente, use `My.Application.Log`.  Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## Tarefas  
  
|Para|Consulte|  
|----------|--------------|  
|Escrever informações de evento em logs do aplicativo.|[Como gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Escrever informações de exceção em logs do aplicativo.|[Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Gravar informações de rastreamento aos logs do aplicativo quando o aplicativo é iniciado e desligado.|[Como registrar mensagens em log quando o aplicativo é iniciado ou encerrado](../Topic/How%20to:%20Log%20Messages%20When%20the%20Application%20Starts%20or%20Shuts%20Down%20\(Visual%20Basic\).md)|  
|Configurar `My.Application.Log` para gravar informações em um arquivo de texto.|[Como gravar informações de evento em um arquivo de texto](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Configurar `My.Application.Log` para gravar informações em um log de eventos.|[Como gravar em um log de eventos do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Alterar onde `My.Application.Log` grava as informações.|[Instruções passo a passo: alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Determinar onde `My.Application.Log` grava as informações.|[Instruções passo a passo: determinando onde My.Application.Log grava informações](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)|  
|Criar um ouvinte de log personalizado para `My.Application.Log`.|[Instruções passo a passo: criando ouvintes de log personalizados](../Topic/Walkthrough:%20Creating%20Custom%20Log%20Listeners%20\(Visual%20Basic\).md)|  
|Filtrar a saída de logs de `My.Application.Log`.|[Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Solucionando problemas: ouvintes de Log](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)