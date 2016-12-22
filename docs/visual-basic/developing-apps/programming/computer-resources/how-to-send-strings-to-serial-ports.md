---
title: "Como enviar cadeias de caracteres para portas seriais no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Objeto My.Computer.Ports"
  - "portas, enviando cadeias de caracteres para"
  - "portas seriais, enviando cadeias de caracteres para"
  - "cadeias de caracteres {Visual Basic], enviando para portas seriais"
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como enviar cadeias de caracteres para portas seriais no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como usar `My.Computer.Ports` para enviar sequências de caracteres para portas seriais do computador em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] .  
  
## Exemplo  
 Este exemplo envia uma sequência de caracteres para a porta serial Com1.  Você talvez precise usar uma porta serial diferente no seu computador.  
  
 Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.  Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 O bloco `Using` permite que ao aplicativo feche a porta serial mesmo que se gere uma exceção.  Todo o código que manipula a porta serial deve aparecer dentro deste bloco ou em um bloco `Try...Catch...Finally`.  
  
 O método <xref:System.IO.Ports.SerialPort.WriteLine%2A> envia os dados para a porta serial.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## Compilando o código  
  
-   Este exemplo assume que o computador está utilizando a `COM1`.  
  
## Programação robusta  
 Este exemplo assume que o computador está utilizando `COM1`; para maior flexibilidade, o código deveria permitir ao usuário que selecionasse a porta serial desejada em uma lista de portas disponíveis.  Para obter mais informações, consulte [Como mostrar portas seriais disponíveis](../Topic/How%20to:%20Show%20Available%20Serial%20Ports%20in%20Visual%20Basic.md).  
  
 Este exemplo usa um bloco `Using` para se certificar de que o aplicativo fecha a porta mesmo se ele lançar uma exceção.  Para obter mais informações, consulte [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [Como discar modems conectados a portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [Como mostrar portas seriais disponíveis](../Topic/How%20to:%20Show%20Available%20Serial%20Ports%20in%20Visual%20Basic.md)