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
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424812"
---
# <a name="how-to-load-and-display-metafiles"></a>Como carregar e exibir metarquivos
A classe <xref:System.Drawing.Imaging.Metafile>, que herda da classe <xref:System.Drawing.Image>, fornece métodos para gravar, exibir e examinar imagens vetoriais.  
  
## <a name="example"></a>Exemplo  
 Para exibir uma imagem vetorial (metarquivo) na tela, você precisa de um objeto <xref:System.Drawing.Imaging.Metafile> e um objeto <xref:System.Drawing.Graphics>. Passe o nome de um arquivo (ou um fluxo) para um Construtor <xref:System.Drawing.Imaging.Metafile>. Depois de criar um objeto <xref:System.Drawing.Imaging.Metafile>, passe esse objeto <xref:System.Drawing.Imaging.Metafile> para o método <xref:System.Drawing.Graphics.DrawImage%2A> de um objeto <xref:System.Drawing.Graphics>.  
  
 O exemplo cria um objeto <xref:System.Drawing.Imaging.Metafile> de um arquivo EMF (metarquivo avançado) e, em seguida, desenha a imagem com seu canto superior esquerdo em (60, 10).  
  
 A ilustração a seguir mostra o metarquivo desenhado no local especificado.  
  
 ![Captura de tela mostrando a posição da imagem.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do manipulador de eventos de <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Consulte também

- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
