---
title: "Como registrar em log as exce&#231;&#245;es no Visual Basic | Microsoft Docs"
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
  - "exceções, log"
  - "exceções, acompanhando"
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como registrar em log as exce&#231;&#245;es no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar os objetos `My.Application.Log` e `My.Log` para criar um log de informações sobre exceções que ocorrem em seu aplicativo.  Esses exemplos mostram como usar o método `My.Application.Log.WriteException` para registrar exceções que você tratou explicitamente com catch e exceções que não estão tratadas.  
  
 Para registrar informações de rastreamento, use o método `My.Application.Log.WriteEntry`.  Para mais informações, consulte <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.  
  
### Para registrar uma exceção manipulada  
  
1.  Crie o método que irá gerar as informações da exceção.  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  Use um bloco `Try...Catch` para capturar a exceção.  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  Coloque o código que poderá gerar uma exceção no bloco `Try`.  
  
     Tire os comentários das linhas `Dim` e `MsgBox` para causar uma exceção <xref:System.NullReferenceException>.  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  No bloco `Catch`, use o método `My.Application.Log.WriteException` para gravar as informações de exceção.  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     O exemplo a seguir mostra o código completo para registrar uma exceção manipulada.  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### Para registrar uma exceção não tratada  
  
1.  Tenha um projeto selecionado no **Solution Explorer**.  No menu **Project**, escolha **Properties**.  
  
2.  Clique na guia **Application**.  
  
3.  Clique no botão **View Application Events** para abrir o Editor de Código.  
  
     Isso abre o arquivo ApplicationEvents.vb.  
  
4.  Deixe o arquivo ApplicationEvents.vb aberto no Editor do Código.  No menu **General**, escolha **MyApplication Events**.  
  
5.  No menu **Declarations**, escolha **UnhandledException**.  
  
     Gera a aplicativo do <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> evento antes do aplicativo principal executar.  
  
6.  Adicione o método `My.Application.Log.WriteException` para o manipulador de eventos `UnhandledException`.  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     O exemplo a seguir mostra o código completo para registrar uma exceção não tratada.  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Trabalhando com logs de aplicativo](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Como gravar mensagens de log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [Instruções passo a passo: determinando onde My.Application.Log grava informações](../Topic/Walkthrough:%20Determining%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)   
 [Instruções passo a passo: alterando onde My.Application.Log grava informações](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)