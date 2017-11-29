---
title: "Registrando informações em log a partir do aplicativo (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e52aaf4c26b4fa60ee04d7df6aa96980ebbf491
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="logging-information-from-the-application-visual-basic"></a>Registrando informações em log a partir do aplicativo (Visual Basic)
Esta seção contém tópicos que abordam como registrar informações em log do aplicativo usando os objetos `My.Application.Log` ou `My.Log` e como estender os recursos de registro em log do aplicativo.  
  
 O objeto `Log` fornece métodos para gravar informações nos ouvintes de log do aplicativo e a propriedade avançada `TraceSource` do objeto `Log` fornece informações detalhadas de configuração. O objeto `Log` será configurado pelo arquivo de configuração de aplicativo.  
  
 O objeto `My.Log` está disponível somente para aplicativos do ASP.NET. Para aplicativos cliente, use `My.Application.Log`. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log>.  
  
## <a name="tasks"></a>Tarefas  
  
|Para|Consulte|  
|--------|---------|  
|Gravar informações de evento em logs do aplicativo.|[Como gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|Gravar informações de exceção em logs do aplicativo.|[Como registrar em log as exceções](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|Gravar informações de rastreamento em logs do aplicativo quando o aplicativo for inicializado e desligado.|[Como registrar mensagens em log quando o aplicativo é iniciado ou encerrado](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|Configure `My.Application.Log` para gravar informações em um arquivo de texto.|[Como gravar informações de evento em um arquivo de texto](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|Configure `My.Application.Log` para gravar informações em um log de eventos.|[Como gravar em um log de eventos do aplicativo](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|Altere o local em que `My.Application.Log` grava as informações.|[Instruções passo a passo: alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|Determine o local em que `My.Application.Log` grava as informações.|[Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|Crie um ouvinte de log personalizado para `My.Application.Log`.|[Instruções passo a passo: criando ouvintes de log personalizados](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|Filtre a saída dos logs `My.Application.Log`.|[Instruções passo a passo: filtrando a saída de My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Solução de problemas: ouvintes de Log](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
