---
title: Como carregar e exibir metarquivos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: c2b0a89966100077d5a72edc11822c356d2de1b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-and-display-metafiles"></a>Como carregar e exibir metarquivos
O <xref:System.Drawing.Imaging.Metafile> classe que herde o <xref:System.Drawing.Image> da classe, fornece métodos para registrar, exibir e examinar as imagens de vetor.  
  
## <a name="example"></a>Exemplo  
 Para exibir uma imagem de vetor (metarquivo) na tela, é necessário um <xref:System.Drawing.Imaging.Metafile> objeto e um <xref:System.Drawing.Graphics> objeto. Passe o nome de um arquivo (ou um fluxo) para um <xref:System.Drawing.Imaging.Metafile> construtor. Depois de ter criado um <xref:System.Drawing.Imaging.Metafile> de objeto, passe que <xref:System.Drawing.Imaging.Metafile> o objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.  
  
 O exemplo cria um <xref:System.Drawing.Imaging.Metafile> objeto a partir de um arquivo EMF (metarquivo avançado) e, em seguida, desenha a imagem com seu canto superior esquerdo no (60, 10).  
  
 A ilustração a seguir mostra o metarquivo desenhado no local especificado.  
  
 ![Posição da imagem](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
