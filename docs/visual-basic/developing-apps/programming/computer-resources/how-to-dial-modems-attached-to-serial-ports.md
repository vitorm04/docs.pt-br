---
title: "Como discar modems conectados a portas seriais no Visual Basic | Microsoft Docs"
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
  - "modens, discando"
  - "Objeto My.Computer.Ports"
  - "portas seriais, discando"
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como discar modems conectados a portas seriais no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como usar `My.Computer.Ports` para discar um modem em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Normalmente, o modem está conectado a uma das portas seriais no computador.  Para o aplicativo se comunicar com o modem, ele deve enviar comandos à porta serial apropriada.  
  
### Para discar um modem  
  
1.  Determine em qual porta serial o modem está conectado.  O exemplo pressupõe que o modem está na COM1.  
  
2.  Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta.  Para mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     O bloco `Using` permite que ao aplicativo feche a porta serial mesmo que se gere uma exceção.  Todo o código que manipula a porta serial deve aparecer dentro deste bloco ou em um bloco `Try...Catch...Finally`.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Defina a propriedade `DtrEnable` para indicar que o computador estará pronto para aceitar uma transmissão de entrada do modem.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Envie o comando de discagem e o número de telefone para o modem por meio de porta serial por meio do método <xref:System.IO.Ports.SerialPort.Write%2A>.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## Exemplo  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Este exemplo de código também está disponível como um trecho de código IntelliSense.  No selecionador de trechos de código, ele está localizado em **Connectivity and Networking**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
## Compilando o código  
 Este exemplo requer uma referência ao namespace <xref:System?displayProperty=fullName>.  
  
## Programação robusta  
 O exemplo supõe que o modem está conectado com a COM1.  É recomendável que seu código permita que o usuário selecione a porta serial desejada em uma lista de portas disponíveis.  Para mais informações, consulte [Como mostrar portas seriais disponíveis](../Topic/How%20to:%20Show%20Available%20Serial%20Ports%20in%20Visual%20Basic.md).  
  
 Este exemplo usa um bloco `Using` para se certificar de que o aplicativo fecha a porta mesmo se ele lançar uma exceção.  Para mais informações, consulte [Instrução Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 No exemplo, o aplicativo desconecta a porta serial após discar o modem.  Realisticamente, você desejará transferir dados a partir do modem e para o modem.  Para mais informações, consulte [Como receber cadeias de caracteres de portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [Como enviar cadeias de caracteres para portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [Como receber cadeias de caracteres de portas seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)   
 [Como mostrar portas seriais disponíveis](../Topic/How%20to:%20Show%20Available%20Serial%20Ports%20in%20Visual%20Basic.md)