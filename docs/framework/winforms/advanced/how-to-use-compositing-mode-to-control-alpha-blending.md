---
title: 'Como: usar o modo de composição para controlar a combinação alfa'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 15cb111a68cedaec011e88fa4916c292786d16b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210680"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Como: usar o modo de composição para controlar a combinação alfa
Pode haver ocasiões em que é útil criar um bitmap fora da tela com as seguintes características:  
  
-   Cores com valores alfabéticos inferiores a 255.  
  
-   As cores não têm combinação alfa umas com as outras ao criar o bitmap.  
  
-   Ao exibir o bitmap terminado, as cores no bitmap são combinadas em alfo com as cores da tela de fundo no dispositivo de vídeo.  
  
 Para criar esse bitmap, construa um espaço em branco <xref:System.Drawing.Bitmap> do objeto e, em seguida, construir um <xref:System.Drawing.Graphics> objeto baseado nesse bitmap. Definir o modo de composição do <xref:System.Drawing.Graphics> do objeto para <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma <xref:System.Drawing.Graphics> objeto com base em um <xref:System.Drawing.Bitmap> objeto. O código usa o <xref:System.Drawing.Graphics> objeto junto com dois pincéis semitransparentes (alfa = 160) para pintar o bitmap. O código preenche uma elipse vermelha e uma elipse verde usando os pincéis semitransparentes. A elipse verde se sobrepõe à vermelha, mas o verde não é combinado com o vermelho porque o modo de composição do <xref:System.Drawing.Graphics> objeto é definido como <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 O código desenha o bitmap na tela duas vezes: uma vez em uma tela de fundo branca e uma vez em uma tela de fundo multicolorida. Os pixels no bitmap que fazem parte das duas elipses têm um componente alfa de 160, de forma que as elipses são mescladas com as cores da tela de fundo na tela.  
  
 A ilustração a seguir mostra a saída do código de exemplo. Observe que as elipses são mescladas com a tela de fundo, mas elas não são mescladas uma com a outra.  
  
 ![Diagrama mostrando elipses combinada com a tela de fundo, não entre si.](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 O exemplo de código contém esta instrução:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Se desejar que as elipses sejam mescladas entre si e com a tela de fundo, altere essa instrução para o seguinte:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 A ilustração a seguir mostra a saída do código revisado.  
  
 ![Diagrama que mostra as elipses combinada juntos e em segundo plano.](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Drawing.Color.FromArgb%2A>
- [Combinação alfa em linhas e preenchimentos](alpha-blending-lines-and-fills.md)
