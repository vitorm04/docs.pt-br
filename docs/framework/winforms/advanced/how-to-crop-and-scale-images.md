---
title: 'Como: Cortar e dimensionar imagens'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: ff0567dca0fd86736e02a9dd827ec15df8bf2df8
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654491"
---
# <a name="how-to-crop-and-scale-images"></a>Como: Cortar e dimensionar imagens
O <xref:System.Drawing.Graphics> classe fornece vários <xref:System.Drawing.Graphics.DrawImage%2A> métodos, alguns deles têm parâmetros de retângulo de origem e destino que você pode usar para recortar e dimensionar imagens.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói um <xref:System.Drawing.Image> objeto do arquivo de disco GIF. O código desenha a imagem inteira de maçã em seu tamanho original. O código, em seguida, chama o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto para desenhar uma parte da imagem de maçã em um retângulo de destino que é maior do que a imagem de maçã original.  
  
 O <xref:System.Drawing.Graphics.DrawImage%2A> método determina qual parte da maçã desenhar olhando no retângulo de origem, que é especificado pelo terceiro, quarto, quintas e sexto argumentos. Nesse caso, a maçã é cortada para 75% de sua largura e 75 por cento de sua altura.  
  
 O <xref:System.Drawing.Graphics.DrawImage%2A> método determina onde desenhar a maçã cortada e o tamanho máximo para tornar a maçã cortada olhando no retângulo de destino, que é especificado pelo segundo argumento. Nesse caso, o retângulo de destino é 30% a mais largo e 30 por cento mais alto que a imagem original.  
  
 A ilustração a seguir mostra a maçã original e a maçã dimensionada e cortada.  
  
 ![Captura de tela de uma imagem original e a mesma imagem cortada.](./media/how-to-crop-and-scale-images/original-image-cropped-image.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Certifique-se de substituir `Apple.gif` por um nome de arquivo de imagem e um caminho que sejam válidos no seu sistema.  
  
## <a name="see-also"></a>Consulte também
- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
