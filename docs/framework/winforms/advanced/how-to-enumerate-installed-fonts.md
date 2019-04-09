---
title: 'Como: enumerar as fontes instaladas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: 92f27399cce9e03a4679c8a34fbdafcf28c32252
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155006"
---
# <a name="how-to-enumerate-installed-fonts"></a>Como: enumerar as fontes instaladas
O <xref:System.Drawing.Text.InstalledFontCollection> herda o <xref:System.Drawing.Text.FontCollection> classe base abstrata. Você pode usar um <xref:System.Drawing.Text.InstalledFontCollection> objeto para enumerar as fontes instaladas no computador. O <xref:System.Drawing.Text.FontCollection.Families%2A> propriedade de um <xref:System.Drawing.Text.InstalledFontCollection> objeto é uma matriz de <xref:System.Drawing.FontFamily> objetos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lista os nomes de todas as famílias de fontes instaladas no computador. O código recupera o <xref:System.Drawing.FontFamily.Name%2A> propriedade de cada <xref:System.Drawing.FontFamily> objeto na matriz retornada pelo <xref:System.Drawing.Text.FontCollection.Families%2A> propriedade. Como os nomes da família são recuperados, eles são concatenados à lista de formulário uma separada por vírgulas. Em seguida, a <xref:System.Drawing.Graphics.DrawString%2A> método da <xref:System.Drawing.Graphics> classe desenha a lista separada por vírgulas em um retângulo.  
  
 Se você executar o código de exemplo, a saída será semelhante ao mostrado na ilustração a seguir:  
  
 ![Captura de tela que mostra as famílias de fontes instaladas.](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>. Além disso, você deve importar o <xref:System.Drawing.Text> namespace.  
  
## <a name="see-also"></a>Consulte também

- [Usando fontes e texto](using-fonts-and-text.md)
