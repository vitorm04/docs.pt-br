---
title: "Como registrar mensagens em log quando o aplicativo é iniciado ou desligado (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event
- event logs, startup
- Shutdown event
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 94842349ae1c0fa3ccbdb2279b05a0faeb2f5d30
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>Como registrar mensagens em log quando o aplicativo é iniciado ou encerrado (Visual Basic)
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log as informações sobre eventos que ocorrem em seu aplicativo. Este exemplo mostra como usar o método `My.Application.Log.WriteEntry` com os eventos `Startup` e `Shutdown` para gravar informações de rastreamento.  
  
### <a name="to-access-the-applications-event-handler-code"></a>Para acessar o código do manipulador de eventos do aplicativo  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, escolha **Propriedades**.  
  
2.  Clique na guia **Aplicativo**.  
  
3.  Clique no botão **Exibir Eventos de Aplicativo** para abrir o Editor de Códigos.  
  
     Isso abrirá o arquivo ApplicationEvents.vb.  
  
### <a name="to-log-messages-when-the-application-starts"></a>Para registrar mensagens em log quando o aplicativo é iniciado  
  
1.  Abra o arquivo ApplicationEvents.vb no Editor de Códigos. No menu **Geral**, escolha **Eventos MyApplication**.  
  
2.  No menu **Declarações**, escolha **Inicialização**.  
  
     A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> antes da execução do aplicativo principal.  
  
3.  Adicione o método `My.Application.Log.WriteEntry` ao manipulador de eventos `Startup`.  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>Para registrar mensagens em log quando o aplicativo é desligado  
  
1.  Abra o arquivo ApplicationEvents.vb no Editor de Códigos. No menu **Geral**, escolha **Eventos MyApplication**.  
  
2.  No menu **Declarações**, escolha **Desligamento**.  
  
     A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> após a execução do aplicativo principal, mas antes de desligar.  
  
3.  Adicione o método `My.Application.Log.WriteEntry` ao manipulador de eventos `Shutdown`.  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Você pode usar o **Designer de Projeto** para acessar os eventos do aplicativo no Editor de Códigos. Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Página de Aplicativo, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)   
 [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
