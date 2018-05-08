---
title: Como executar um som inserido em um recurso a partir de um Windows Form
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
ms.openlocfilehash: c9dc8499e2d12ed17f9b409a805148d08da894fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Como executar um som inserido em um recurso a partir de um Windows Form
Você pode usar o <xref:System.Media.SoundPlayer> classe tocar um som de um recurso inserido.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
 Importando o <xref:System.Media?displayProperty=nameWithType> namespace.  
  
 Incluindo o arquivo de som como um recurso inserido em seu projeto.  
  
 Substituindo "\<AssemblyName >" com o nome do assembly no qual é incorporado no arquivo de som. Não inclua o sufixo ". dll".  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Media.SoundPlayer>  
 [Como reproduzir um som de um Windows Form](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [Como executar um loop de um som tocado em um Windows Form](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
