---
title: Como usar uma matriz de cores para definir valores alfa em imagens
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
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba7a016c96556f2719d4a247c93df7ac698b24fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>Como usar uma matriz de cores para definir valores alfa em imagens
O <xref:System.Drawing.Bitmap> classe (que herda do <xref:System.Drawing.Image> classe) e o <xref:System.Drawing.Imaging.ImageAttributes> classe fornecem funcionalidade para obter e definir valores de pixel. Você pode usar o <xref:System.Drawing.Imaging.ImageAttributes> classe para modificar o alpha valores para uma imagem inteira ou você pode chamar o <xref:System.Drawing.Bitmap.SetPixel%2A> método o <xref:System.Drawing.Bitmap> classe para modificar valores em pixel individuais.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Drawing.Imaging.ImageAttributes> classe tem várias propriedades que você pode usar para modificar imagens durante o processamento. No exemplo a seguir, um <xref:System.Drawing.Imaging.ImageAttributes> objeto é usado para definir todos os valores alfa 80 por cento dos quais eram eles. Isso é feito inicializando uma matriz de cores e configurando o valor de escala alfa na matriz para 0,8. O endereço da matriz de cores é passado para o <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> método do <xref:System.Drawing.Imaging.ImageAttributes> objeto e o <xref:System.Drawing.Imaging.ImageAttributes> objeto é passado para o <xref:System.Drawing.Graphics.DrawString%2A> método o <xref:System.Drawing.Graphics> objeto.  
  
 Durante o processamento, os valores alfa no bitmap são convertidos em 80 por cento do que eram. Isso resulta em uma imagem que é combinada com a tela de fundo. Como mostra a ilustração a seguir, a imagem de bitmap é transparente; é possível ver a linha preta sólida através dela.  
  
 ![Combinação alfa usando uma matriz](../../../../docs/framework/winforms/advanced/media/image2.png "image2")  
  
 Nos pontos em que a imagem está sobre a parte branca da tela de fundo, ela é combinada com a cor branca. Nos pontos em que imagem cruza a linha preta, ela é combinada a cor preta.  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos Gráficos e Desenho nos Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Combinação Alfa em Linhas e Preenchimentos](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
