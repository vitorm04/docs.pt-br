---
title: "Como melhorar o desempenho evitando o dimensionamento automático"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f49fc4b1e59879b9ecc67295610187fa2e5e80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Como melhorar o desempenho evitando o dimensionamento automático
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pode ajustar a escala automaticamente de uma imagem à medida que você a desenha, o que poderia diminuir o desempenho. Como alternativa, você pode controlar o dimensionamento da imagem, passando as dimensões do retângulo de destino para o <xref:System.Drawing.Graphics.DrawImage%2A> método.  
  
 Por exemplo, a seguinte chamada para o <xref:System.Drawing.Graphics.DrawImage%2A> método Especifica um canto superior esquerdo do (50, 30), mas não especifica um retângulo de destino.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Embora essa é a versão mais fácil do <xref:System.Drawing.Graphics.DrawImage%2A> método em termos de número de argumentos necessários, não é necessariamente o mais eficiente. Se a resolução usada pelo [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] (geralmente 96 pontos por polegada) é diferente do que a resolução armazenada na <xref:System.Drawing.Image> objeto, em seguida, o <xref:System.Drawing.Graphics.DrawImage%2A> método dimensionará a imagem. Por exemplo, suponha que um <xref:System.Drawing.Image> objeto tem uma largura de 216 pixels e um valor armazenado resolução horizontal de 72 pontos por polegada. Como 216/72 é 3, <xref:System.Drawing.Graphics.DrawImage%2A> dimensionará a imagem para que ele tenha uma largura de 3 polegadas em uma resolução de 96 pontos por polegada. Ou seja, <xref:System.Drawing.Graphics.DrawImage%2A> exibirá uma imagem que tem uma largura de 96 x 3 = 288 pixels.  
  
 Mesmo se a resolução da tela for diferente de 96 pontos por polegada, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] provavelmente ajustará a escala da imagem como se a resolução de tela fosse de 96 pontos por polegada. Isso ocorre porque um [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> objeto está associado um contexto de dispositivo e quando [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] consultas o contexto de dispositivo para a resolução da tela, o resultado geralmente é 96, independentemente da resolução da tela real. Você pode evitar o dimensionamento automático, especificando o retângulo de destino no <xref:System.Drawing.Graphics.DrawImage%2A> método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir desenha a mesma imagem duas vezes. No primeiro caso, a largura e altura do retângulo de destino não são especificados, e a escala da imagem é ajustada automaticamente. No segundo caso, a largura e altura (medidas em pixels) do retângulo de destino são especificadas como iguais à largura e altura da imagem original. A ilustração a seguir mostra a imagem renderizada duas vezes.  
  
 ![Textura em escala](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua Texture.jpg por um nome e caminho de imagem válidos no seu sistema.  
  
## <a name="see-also"></a>Consulte também  
 [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
