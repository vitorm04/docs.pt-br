---
title: 'Como: girar, refletir e distorcer imagens'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 505028c491228ffdf9c11d0c71dcd5e1afdc5103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114027"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Como: girar, refletir e distorcer imagens
Você pode girar, refletir e distorcer uma imagem especificando pontos de destino para os cantos superior esquerdo, superior direito e inferior esquerdo da imagem original. Os três pontos de destino determinam uma transformação afim que mapeia a imagem retangular original para um paralelogramo.  
  
## <a name="example"></a>Exemplo  
 Por exemplo, suponha que a imagem original é um retângulo com o canto superior esquerdo em (0, 0), o canto superior direito em (100, 0) e o canto inferior esquerdo em (0, 50). Agora suponha que você mapeie os três pontos para pontos de destino da seguinte maneira.  
  
|Ponto original|Ponto de destino|  
|--------------------|-----------------------|  
|Superior esquerdo (0, 0)|(200, 20)|  
|Superior direito (100, 0)|(110, 100)|  
|Inferior esquerdo (0, 50)|(250, 30)|  
  
 A ilustração a seguir mostra a imagem original e a imagem mapeada para o paralelogramo. A imagem original foi distorcida, refletida, girada e movida. O eixo x ao longo da borda superior da imagem original é mapeado para a linha que percorre (200, 20) e (110, 100). O eixo y ao longo da borda esquerda da imagem original é mapeado para a linha que percorre (200, 20) e (250, 30).  
  
 ![A imagem original e a imagem mapeada para o paralelogramo.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-illustration.gif)  
  
 A ilustração a seguir mostra uma transformação semelhante aplicada a uma imagem fotográfica:  
  
 ![A imagem de uma Alpinista e a imagem mapeada para o paralelogramo.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-photo.png)  
  
 A ilustração a seguir mostra uma transformação semelhante aplicada a um metarquivo:  
  
 ![Ilustração de formas e texto e que é mapeada para o paralelogramo.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-metafile.png)  
  
 O exemplo a seguir produz as imagens mostradas na primeira ilustração.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `Stripes.bmp` pelo caminho até uma imagem válida no seu sistema.  
  
## <a name="see-also"></a>Consulte também

- [Trabalhando com imagens, bitmaps, ícones e metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
