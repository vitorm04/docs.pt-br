---
title: Como cortar e dimensionar imagens
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: d5acda50a1aa0f0cae6e77a748b011908fcc8c34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-crop-and-scale-images"></a>Como cortar e dimensionar imagens
O <xref:System.Drawing.Graphics> classe fornece vários <xref:System.Drawing.Graphics.DrawImage%2A> métodos, alguns dos quais têm parâmetros de retângulo de origem e de destino que você pode usar para cortar e dimensionar imagens.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo de disco Apple.gif. O código desenha a imagem inteira de maçã em seu tamanho original. O código, em seguida, chama o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto para desenhar uma parte da imagem apple em um retângulo de destino que é maior do que a imagem original da apple.  
  
 O <xref:System.Drawing.Graphics.DrawImage%2A> método determina qual parte da apple para desenhar examinando o retângulo de origem, que é especificado pela terceira, quarta, quinto e sexto argumentos. Nesse caso, a maçã é cortada para 75% de sua largura e 75 por cento de sua altura.  
  
 O <xref:System.Drawing.Graphics.DrawImage%2A> método determina onde desenhar o apple cortado e como fazer a apple cortada examinando o retângulo de destino, que é o tamanho especificado pelo segundo argumento. Nesse caso, o retângulo de destino é 30% a mais largo e 30 por cento mais alto que a imagem original.  
  
 A ilustração a seguir mostra a maçã original e a maçã dimensionada e cortada.  
  
 ![Cortar e dimensionar](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Certifique-se de substituir `Apple.gif` por um nome de arquivo de imagem e um caminho que sejam válidos no seu sistema.  
  
## <a name="see-also"></a>Consulte também  
 [Imagens, bitmaps e metarquivos](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
