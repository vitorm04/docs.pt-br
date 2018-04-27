---
title: Como executar um som em loop em um Windows Form
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6b4e910f30a5d125fd1ec234e896828738f62c4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Como executar um som em loop em um Windows Form
O exemplo de código a seguir toca um som repetidamente. Quando o código de `stopPlayingButton_Click` manipulador de eventos é executado, qualquer som no momento será interrompido. Se nenhum som é reproduzido, nada acontecerá.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
-   Se você substituir o nome de arquivo `"c:\Windows\Media\chimes.wav"` com um nome de arquivo válido.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Programação robusta  
 Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do caminho está malformado. Por exemplo, ele contém caracteres que não são válidos ou é somente espaço em branco (<xref:System.ArgumentException> classe).  
  
-   O caminho é somente leitura (<xref:System.IO.IOException> classe).  
  
-   O nome do caminho é `Nothing` (<xref:System.ArgumentNullException> classe).  
  
-   O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).  
  
-   O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).  
  
-   O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic. Verifique todas as entradas antes de usar os dados no seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [Como reproduzir um som de um Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [Visão geral da classe SoundPlayer](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
