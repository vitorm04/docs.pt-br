---
title: 'Como: Iniciar um aplicativo e enviar pressionamentos de tecla a ele (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 9519fd85177d5d2adf97b54652c19330954edadf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815960"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Como: Iniciar um aplicativo e enviar pressionamentos de tecla a ele (Visual Basic)
Este exemplo usa a função `Shell` para iniciar o aplicativo Calculadora e, em seguida, multiplica dois números enviando pressionamentos de tecla usando o método `My.Computer.Keyboard.SendKeys`.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Uma exceção <xref:System.ArgumentException> será gerada se um aplicativo com o identificador do processo solicitado não for localizado.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A chamada para a função `Shell` exige confiança total (classe <xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
