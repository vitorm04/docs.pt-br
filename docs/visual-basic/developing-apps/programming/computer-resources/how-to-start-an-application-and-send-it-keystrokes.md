---
title: "Como iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic) | Microsoft Docs"
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
  - "pressionamentos de tecla, enviando"
  - "processos, iniciando e enviando pressionamentos de tecla"
  - "Exemplos de SendKeys.SendWait"
  - "Exemplo de comando Shell [Visual Basic]"
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo usa a função `Shell` para iniciar o aplicativo calculadora e, em seguida, multiplica dois números enviando pressionamentos de tecla usando o método `My.Computer.Keyboard.SendKeys`.  
  
## Exemplo  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## Programação robusta  
 Uma exceção  <xref:System.ArgumentException> é lançada se um aplicativo com o identificador do processo solicitado não puder ser encontrado.  
  
## Segurança do .NET Framework  
 A chamada para a função `Shell` requer confiança total \(classe <xref:System.Security.SecurityException> \).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>