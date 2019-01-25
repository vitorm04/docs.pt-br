---
title: 'Como: Carregar e exibir metarquivos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: d0835d7f2c5ffea44f22661a765ab16b1d0130c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619552"
---
# <a name="how-to-load-and-display-metafiles"></a>Como: Carregar e exibir metarquivos
O <xref:System.Drawing.Imaging.Metafile> classe, que herda o <xref:System.Drawing.Image> de classe, que fornece métodos para gravar, exibir e examinar imagens vetoriais.  
  
## <a name="example"></a>Exemplo  
 Para exibir uma imagem de vetor (metarquivo) na tela, você precisa de uma <xref:System.Drawing.Imaging.Metafile> objeto e um <xref:System.Drawing.Graphics> objeto. Passe o nome de um arquivo (ou um fluxo) para um <xref:System.Drawing.Imaging.Metafile> construtor. Depois de criar uma <xref:System.Drawing.Imaging.Metafile> de objeto, passá-lo <xref:System.Drawing.Imaging.Metafile> do objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.  
  
 O exemplo cria um <xref:System.Drawing.Imaging.Metafile> objeto a partir de um arquivo EMF (metarquivo avançado) e, em seguida, desenha a imagem com seu canto superior esquerdo em (60, 10).  
  
 A ilustração a seguir mostra o metarquivo desenhado no local especificado.  
  
 ![Posição da imagem](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
