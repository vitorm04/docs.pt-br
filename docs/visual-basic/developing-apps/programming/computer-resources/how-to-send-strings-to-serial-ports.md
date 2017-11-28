---
title: Como enviar cadeias de caracteres para portas seriais no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95c67b344572d21f418cbc14d350e6ff28611bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Como enviar cadeias de caracteres para portas seriais no Visual Basic
Este tópico descreve como usar o `My.Computer.Ports` para enviar cadeias de caracteres para as portas seriais do computador no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="example"></a>Exemplo  
 Este exemplo envia uma cadeia de caracteres para a porta serial COM1. Talvez você precise usar uma porta serial diferente em seu computador.  
  
 Use o método `My.Computer.Ports.OpenSerialPort` para obter uma referência para a porta. Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 O bloco `Using` permite que o aplicativo feche a porta serial mesmo que ele gere uma exceção. Todo o código que manipula a porta serial deve aparecer dentro deste bloco ou em um bloco `Try...Catch...Finally`.  
  
 O método <xref:System.IO.Ports.SerialPort.WriteLine%2A> envia os dados à porta serial.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Este exemplo pressupõe que o computador esteja usando a `COM1`.  
  
## <a name="robust-programming"></a>Programação robusta  
 Este exemplo pressupõe que o computador esteja usando a `COM1`. Para obter mais flexibilidade, o código deve permitir que o usuário selecione a porta serial desejada na lista de portas disponíveis. Para obter mais informações, consulte [Como mostrar portas seriais disponíveis](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Este exemplo usa um bloco `Using` para garantir que o aplicativo feche a porta mesmo que ele lance uma exceção. Para obter mais informações, consulte [Instrução using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Como Discar Modems Conectados a Portas Seriais](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Como Mostrar Portas Seriais Disponíveis](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
