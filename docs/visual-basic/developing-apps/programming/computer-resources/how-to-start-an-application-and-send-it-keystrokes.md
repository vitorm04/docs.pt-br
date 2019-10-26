---
title: 'Como: iniciar um aplicativo e enviá-lo com pressionamentos de tecla-Visual Basic'
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919386"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>Como: iniciar um aplicativo e enviar pressionamentos de tecla (Visual Basic)

Este exemplo usa o método <xref:Microsoft.VisualBasic.Interaction.Shell%2A> para iniciar o aplicativo do bloco de notas e, em seguida, imprime uma frase, enviando pressionamentos de teclas usando o método [My. Computer. Keyboard. SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) .

## <a name="example"></a>Exemplo

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a>Programação robusta

Uma exceção <xref:System.ArgumentException> será gerada se um aplicativo com o identificador de processo solicitado não puder ser encontrado.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework

A chamada para a função `Shell` exige confiança total (classe <xref:System.Security.SecurityException>).

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
