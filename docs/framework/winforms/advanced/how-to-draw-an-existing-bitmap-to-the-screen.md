---
title: 'Como: Desenhar um Bitmap existente na tela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: d2e06aa382bc2b01a4308f99735ca533e7a9a3ea
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653815"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>Como: Desenhar um Bitmap existente na tela
É possível desenhar facilmente uma imagem existente na tela. Primeiro você precisa criar uma <xref:System.Drawing.Bitmap> objeto usando o construtor de bitmap que usa um nome de arquivo <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>. Este construtor aceita imagens com vários formatos de arquivo diferentes, incluindo BMP, GIF, JPEG, PNG e TIFF. Depois que você criou o <xref:System.Drawing.Bitmap> de objeto, passá-lo <xref:System.Drawing.Bitmap> do objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.  
  
## <a name="example"></a>Exemplo  
 Este exemplo cria um <xref:System.Drawing.Bitmap> objeto de um arquivo JPEG e, em seguida, desenha o bitmap com seu canto superior esquerdo em (60, 10).  
  
 A ilustração a seguir mostra o bitmap desenhado no local especificado:  
  
 ![Captura de tela que mostra uma imagem em uma posição especificada.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
