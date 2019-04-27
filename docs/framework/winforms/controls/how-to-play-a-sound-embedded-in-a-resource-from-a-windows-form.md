---
title: 'Como: Reproduzir um som inserido em um recurso de um Windows Form'
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
ms.openlocfilehash: 49235f9cb035c5a09c26b427f855fc00e818fe1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913348"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>Como: Reproduzir um som inserido em um recurso de um Windows Form
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
