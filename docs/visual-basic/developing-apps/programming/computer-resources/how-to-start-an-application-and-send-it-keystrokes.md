---
title: Como iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 716c88153ad01c7b225f31948c8aaaa2694dc512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582142"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Como iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic)
Este exemplo usa a função `Shell` para iniciar o aplicativo Calculadora e, em seguida, multiplica dois números enviando pressionamentos de tecla usando o método `My.Computer.Keyboard.SendKeys`.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Uma exceção <xref:System.ArgumentException> será gerada se um aplicativo com o identificador do processo solicitado não for localizado.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A chamada para a função `Shell` exige confiança total (classe <xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
