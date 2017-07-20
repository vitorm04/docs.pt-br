---
title: "Como Registrar em Log as Exceções no Visual Basic | Microsoft Docs"
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
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8a5233f5e39c5e6c423a453cd241be40877d2ba8
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-log-exceptions-in-visual-basic"></a>Como registrar em log as exceções no Visual Basic
É possível usar os objetos `My.Application.Log` e `My.Log` para registrar em log informações sobre exceções que ocorrem em um aplicativo. Esses exemplos mostram como usar o método `My.Application.Log.WriteException` para registrar em log exceções capturadas explicitamente e exceções sem tratamento.  
  
 Para registrar informações de rastreamento de registros em log, use o método `My.Application.Log.WriteEntry`. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### <a name="to-log-a-handled-exception"></a>Registrar em log uma exceção manipulada  
  
1.  Crie o método que gerará as informações de exceção.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  Use um bloco `Try...Catch` para capturar a exceção.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  Coloque o código que poderá gerar uma exceção no bloco `Try`.  
  
     Remova a marca de comentário das linhas `Dim` e `MsgBox` para lançar uma exceção <xref:System.NullReferenceException>.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  No bloco `Catch`, use o método `My.Application.Log.WriteException` para gravar as informações de exceção.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     O exemplo a seguir mostra o código completo para registrar em log uma exceção manipulada.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a>Registrar em log uma exceção sem tratamento  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, escolha **Propriedades**.  
  
2.  Clique na guia **Aplicativo**.  
  
3.  Clique no botão **Exibir Eventos de Aplicativo** para abrir o Editor de Códigos.  
  
     Isso abrirá o arquivo ApplicationEvents.vb.  
  
4.  Abra o arquivo ApplicationEvents.vb no Editor de Códigos. No menu **Geral**, escolha **Eventos MyApplication**.  
  
5.  No menu **Declarações**, escolha **UnhandledException**.  
  
     A aplicativo gera o evento <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> antes da execução do aplicativo principal.  
  
6.  Adicione o método `My.Application.Log.WriteException` ao manipulador de eventos `UnhandledException`.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     O exemplo a seguir mostra o código completo para registrar em log uma exceção sem tratamento.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Trabalhando com Logs de Aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Como Gravar Mensagens de Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [Instruções passo a passo: determinando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)   
 [Instruções passo a passo: alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
