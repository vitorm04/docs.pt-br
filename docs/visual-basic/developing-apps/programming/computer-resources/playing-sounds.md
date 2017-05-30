---
title: Reproduzindo sons (Visual Basic) | Microsoft Docs
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
- system sounds, playing
- system sounds
- playing sounds, Visual Basic
- sound loops
- My.Computer.Audio object, tasks
- sounds, playing
- sounds, background
- playing sounds
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: 21
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
ms.openlocfilehash: c9790c9bcd8731546b5d5e1e4aba7ba6f93fe5b1
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="playing-sounds-visual-basic"></a>Executando sons (Visual Basic)
O objeto `My.Computer.Audio` fornece métodos para reproduzir sons.  
  
## <a name="playing-sounds"></a>Executando sons  
 A reprodução em segundo plano permite que o aplicativo execute outro código enquanto o som é reproduzido. O método `My.Computer.Audio.Play` permite que o aplicativo para reproduza apenas um som de tela de fundo de cada vez. Quando o aplicativo reproduz um novo som de tela de fundo, ele para de reproduzir o som de tela de fundo anterior. Você também pode reproduzir um som e aguardar sua conclusão.  
  
 No exemplo a seguir, o método `My.Computer.Audio.Play` toca um som. Quando `AudioPlayMode.WaitToComplete` for especificado, `My.Computer.Audio.Play` aguardará até que o som seja concluído antes de o código de chamada continuar. Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som .wav no seu computador  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 No exemplo a seguir, o método `My.Computer.Audio.Play` toca um som. Ao usar este exemplo, você deve garantir que os recursos do aplicativo incluem um arquivo de som .wav chamado Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## <a name="playing-looping-sounds"></a>Reproduzindo sons em loop  
 No exemplo a seguir, o método `My.Computer.Audio.Play` toca o som especificado na tela de fundo quando `PlayMode.BackgroundLoop` é especificado. Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som .wav no seu computador.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 No exemplo a seguir, o método `My.Computer.Audio.Play` toca o som especificado na tela de fundo quando `PlayMode.BackgroundLoop` é especificado. Ao usar este exemplo, você deve garantir que os recursos do aplicativo incluem um arquivo de som .wav chamado Waterfall.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 O exemplo de código anterior também está disponível como um trecho de código do IntelliSense. No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Sons**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
 Em geral, quando um aplicativo reproduz um som em loop, ele deve interromper o som eventualmente.  
  
## <a name="stopping-the-playing-of-sounds-in-the-background"></a>Parando a reprodução de sons na tela de fundo  
 Use o método `My.Computer.Audio.Stop` para parar o som do aplicativo em loop ou na tela de fundo sendo reproduzido no momento.  
  
 Em geral, quando um aplicativo reproduz um som em loop, ele deve interromper o som em algum momento.  
  
 O exemplo a seguir interrompe um som que está sendo reproduzido na tela de fundo.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 O exemplo de código anterior também está disponível como um trecho de código do IntelliSense. No seletor de trecho de código, ele está localizado em **Aplicativos do Windows Forms > Sons**. Para obter mais informações, consulte [Trechos de Código](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
## <a name="playing-system-sounds"></a>Reproduzindo sons do sistema  
 Use o método `My.Computer.Audio.PlaySystemSound` para reproduzir o som do sistema especificado.  
  
 O método `My.Computer.Audio.PlaySystemSound` utiliza como parâmetro um dos membros compartilhados da classe <xref:System.Media.SystemSound>. O som do sistema <xref:System.Media.SystemSounds.Asterisk%2A> geralmente indica erros.  
  
 O exemplo a seguir usa o método `My.Computer.Audio.PlaySystemSound` para reproduzir um som do sistema.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>
