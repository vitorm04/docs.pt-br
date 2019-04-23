---
title: 'Como: Fazer Loop de um Som Tocado em um Formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
ms.openlocfilehash: a74acbbbcb5646a35de54a6000a0feae30f145a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188507"
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a>Como: Fazer Loop de um Som Tocado em um Formulário do Windows
O exemplo de código a seguir toca um som repetidamente. Quando o código a `stopPlayingButton_Click` manipulador de eventos é executado, nenhum som é interrompido em reprodução no momento. Se nenhum som estiver em execução, nada acontece.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies Sistema e System.Windows.Forms.  
  
-   Se você substituir o nome de arquivo `"c:\Windows\Media\chimes.wav"` com um nome de arquivo válido.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="robust-programming"></a>Programação robusta  
 Operações de arquivo devem ser incluídas dentro de blocos de tratamento de exceção apropriados.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome do caminho está malformado. Por exemplo, ele contém caracteres que não são válidos ou é somente espaço em branco (<xref:System.ArgumentException> classe).  
  
-   O caminho é somente leitura (<xref:System.IO.IOException> classe).  
  
-   É o nome do caminho `Nothing` (<xref:System.ArgumentNullException> classe).  
  
-   O nome do caminho é muito longo (<xref:System.IO.PathTooLongException> classe).  
  
-   O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).  
  
-   O caminho é apenas um dois-pontos ":" (<xref:System.NotSupportedException> classe).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic. Verifique todas as entradas antes de usar os dados no seu aplicativo.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Media.SoundPlayer.PlayLooping%2A>
- [Como: Reproduzir um som de um formulário do Windows](how-to-play-a-sound-from-a-windows-form.md)
- [Visão geral da classe SoundPlayer](soundplayer-class-overview.md)
