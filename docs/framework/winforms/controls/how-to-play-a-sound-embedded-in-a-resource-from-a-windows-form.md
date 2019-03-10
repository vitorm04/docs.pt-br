---
title: 'Como: Reproduzir um som inserido em um recurso de um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: f52cac4ca16adee232fae6fe2c1540bf5d3cb8cf
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708178"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Como: Reproduzir um som inserido em um recurso de um formulário do Windows
Você pode usar o <xref:System.Media.SoundPlayer> classe para tocar um som de um recurso inserido.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.Sound#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
 Importando o <xref:System.Media?displayProperty=nameWithType> namespace.  
  
 Incluindo o arquivo de som como um recurso inserido em seu projeto.  
  
 Substituindo "\<AssemblyName >" com o nome do assembly no qual o arquivo de som é inserido. Não inclua o sufixo ". dll".  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Media.SoundPlayer>
- [Como: Reproduzir um som de um formulário do Windows](how-to-play-a-sound-from-a-windows-form.md)
- [Como: Loop de um som tocado em um formulário do Windows](how-to-loop-a-sound-playing-on-a-windows-form.md)
