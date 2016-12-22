---
title: "Executando sons (Visual Basic) | Microsoft Docs"
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
  - "Objeto My.Computer.Audio, tarefas"
  - "reproduzindo sons"
  - "reproduzindo sons, Visual Basic"
  - "loops de som"
  - "sons, plano de fundo"
  - "sons, reproduzindo"
  - "sons do sistema"
  - "sons do sistema, reproduzindo"
ms.assetid: f0d9e4ab-57c7-47b6-86d3-99ff07078040
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Executando sons (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O objeto `My.Computer.Audio` fornece métodos para tocar sons.  
  
## Reproduzindo sons  
 Reproduzir no segundo plano permite o aplicativo executar outro código enquanto o som é tocado.  O método `My.Computer.Audio.Play` permite o aplicativo tocar somente um som de fundo ao mesmo tempo; quando o aplicativo executa um novo som de fundo, ele pára de reproduzir o som de fundo anterior.  Você também pode tocar um som e esperar a conclusão.  
  
 No exemplo a seguir, o `My.Computer.Audio.Play` método toca um som.  Quando `AudioPlayMode.WaitToComplete` for especificado, `My.Computer.Audio.Play` aguarda até que o som seja concluída antes de chamar o código continua.  Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som que está no seu computador.  
  
 [!code-vb[VbVbalrMyComputer#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_1.vb)]  
  
 No exemplo a seguir, o `My.Computer.Audio.Play` método toca um som.  Ao usar este exemplo, você deve garantir que os recursos de aplicativo incluem um arquivo de som que é chamado de cascata.  
  
 [!code-vb[VbVbalrMyComputer#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_2.vb)]  
  
## Tocando sons de loop.  
 No exemplo a seguir, o `My.Computer.Audio.Play` método toca o som especificado no plano de fundo quando `PlayMode.BackgroundLoop` é especificado.  Ao usar este exemplo, você deve garantir que o nome do arquivo se refere a um arquivo de som que está no seu computador.  
  
 [!code-vb[VbVbalrMyComputer#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_3.vb)]  
  
 No exemplo a seguir, o `My.Computer.Audio.Play` método toca o som especificado no plano de fundo quando `PlayMode.BackgroundLoop` é especificado.  Ao usar este exemplo, você deve garantir que os recursos de aplicativo incluem um arquivo de som que é chamado de cascata.  
  
 [!code-vb[VbVbalrMyComputer#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_4.vb)]  
  
 O exemplo de código anterior também está disponível como um trecho de código IntelliSense.  No seletor de trecho de código, ele está localizado no **Windows Forms Applications \> Sound**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
 Em geral, quando um aplicativo reproduzir um som em seqüência, ele deve interromper o som eventualmente.  
  
## Interrompendo a reprodução de sons em segundo plano  
 Use o método `My.Computer.Audio.Stop` para interromper o som do plano de fundo ou em loop executando atualmente no aplicativo.  
  
 Em geral, quando um aplicativo reproduz um som de looping, ele deve interromper o som em algum momento.  
  
 O exemplo a seguir pára um som que é executado em segundo plano.  
  
 [!code-vb[VbVbalrMyComputer#18](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_5.vb)]  
  
 O exemplo de código anterior também está disponível como um trecho de código IntelliSense.  No seletor de trecho de código, ele está localizado no **Windows Forms Applications \> Sound**.  Para mais informações, consulte [Trechos de código](/visual-studio/ide/code-snippets).  
  
## Reproduzir sons de sistema  
 Use o método `My.Computer.Audio.PlaySystemSound` para reproduzir o som de sistema especificado.  
  
 O método `My.Computer.Audio.PlaySystemSound` aceita como um parâmetro um dos membros da classe <xref:System.Media.SystemSound> compartilhados.  O som do sistema <xref:System.Media.SystemSounds.Asterisk%2A> geralmente indica erros.  
  
 O exemplo a seguir usa a `My.Computer.Audio.PlaySystemSound` método para reproduzir o som de um sistema.  
  
 [!code-vb[VbVbalrMyComputer#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/playing-sounds_6.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Audio>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.PlaySystemSound%2A>   
 <xref:Microsoft.VisualBasic.Devices.Audio.Stop%2A>   
 <xref:Microsoft.VisualBasic.AudioPlayMode>