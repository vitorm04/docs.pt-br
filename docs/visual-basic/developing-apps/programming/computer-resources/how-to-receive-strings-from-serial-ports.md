---
title: "Como receber cadeias de caracteres de portas seriais no Visual Basic | Microsoft Docs"
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
  - "Objeto My.Resources"
  - "portas seriais, recuperando cadeias de caracteres"
  - "cadeias de caracteres {Visual Basic], recuperando de portas seriais"
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como receber cadeias de caracteres de portas seriais no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como usar `My.Computer.Ports` para receber cadeias de caracteres de portas seriais do computador no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Para receber cadeias de caracteres da porta serial  
  
1.  Inicialize a cadeia de caracteres de retorno.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Determine qual porta serial deve fornecer as cadeias de caracteres.  Este exemplo assume que é a `COM1`.  
  
3.  Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.  Para mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     O bloco `Try...Catch...Finally` permite que ao aplicativo feche a porta serial mesmo que se gere uma exceção.  Todo o código que manipula a porta serial deve aparecer dentro desse bloco.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Crie um loop `Do` para ler linhas do texto até que não haja mais linhas disponíveis.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Use o método <xref:System.IO.Ports.SerialPort.ReadLine%2A> para ler a próxima linha de texto disponível a partir de porta serial.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Use uma instrução `If` para determinar se o método <xref:System.IO.Ports.SerialPort.ReadLine%2A> retorna `Nothing` \(significando que não há mais texto disponível\).  Se ele retornar `Nothing`, saia do loop `Do`.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Adicione um bloco `Else` para a instrução `If` para tratar o caso se a cadeia de caracteres é realmente lida.  O bloco acrescenta a cadeia de caracteres a partir de porta serial para a cadeia de caracteres de retorno.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Retorne a cadeia de caracteres.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## Exemplo  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador de trechos de código, ele está localizado em **Connectivity and Networking**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
## Compilando o código  
 Este exemplo assume que o computador está utilizando a `COM1`.  
  
## Programação robusta  
 Este exemplo assume que o computador está utilizando a `COM1`.  Para obter mais flexibilidade, o código deve permitir que o usuário selecione a porta serial desejada de uma lista de portas disponíveis.  Para mais informações, consulte [Como mostrar portas seriais disponíveis](../Topic/How%20to:%20Show%20Available%20Serial%20Ports%20in%20Visual%20Basic.md).  
  
 Este exemplo usa um `Try...Catch...Finally` bloco para certificar\-se de que o aplicativo fecha a porta e capturar quaisquer exceções de tempo limite.  Para mais informações, consulte [Instrução Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [Como discar modems conectados a portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [Como enviar cadeias de caracteres para portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [Como mostrar portas seriais disponíveis](../Topic/How%20to:%20Show%20Available%20Serial%20Ports%20in%20Visual%20Basic.md)