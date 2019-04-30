---
title: 'Como: obter métricas de fontes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 24cada3962339cae0608bbe01e070a0b8e256e73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948197"
---
# <a name="how-to-obtain-font-metrics"></a>Como: obter métricas de fontes
O <xref:System.Drawing.FontFamily> classe fornece os seguintes métodos que recuperam várias métricas de uma combinação de estilo/família específica:  
  
- <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
- <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 Os números retornados por esses métodos são em unidades de design de fonte, portanto, eles são independentes do tamanho e das unidades de um determinado <xref:System.Drawing.Font> objeto.  
  
 A ilustração a seguir mostra as diversas métricas.  
  
 ![Texto de fontes](./media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exibe as métricas para o estilo normal da família de fontes Arial. O código também cria uma <xref:System.Drawing.Font> objeto (com base na família Arial) com 16 pixels de tamanho e exibe as métricas (em pixels) para esse determinado <xref:System.Drawing.Font> objeto.  
  
 A ilustração a seguir mostra a saída do código de exemplo.  
  
 ![Texto de fontes](./media/csfontstext8.png "csFontsText8")  
  
 Observe as duas primeiras linhas de saída na ilustração anterior. O <xref:System.Drawing.Font> objeto retorna um tamanho de 16 e o <xref:System.Drawing.FontFamily> object retorna uma altura de 2.048. Esses dois números (16 e 2.048) são a chave para a conversão entre unidades de design de fonte e as unidades (em pixels nesse caso) do <xref:System.Drawing.Font> objeto.  
  
 Por exemplo, você pode converter o ascendente de unidades de design em pixels da seguinte maneira:  
  
 ![Texto de fontes](./media/fontstext9.png "FontsText9")  
  
 O código a seguir posiciona o texto verticalmente, definindo o <xref:System.Drawing.PointF.Y%2A> membro de dados de um <xref:System.Drawing.PointF> objeto. A coordenada y é aumentada em `font.Height` para cada nova linha de texto. O <xref:System.Drawing.Font.Height%2A> propriedade de um <xref:System.Drawing.Font> object retorna o espaçamento entre linhas (em pixels) para esse determinado <xref:System.Drawing.Font> objeto. Neste exemplo, o número retornado por <xref:System.Drawing.Font.Height%2A> é 19. Observe que esse é o mesmo número (arredondado para um número inteiro) obtido ao converter a métrica de espaçamento entre linhas em pixels.  
  
 Observe que a altura em (também chamada de tamanho ou tamanho em) não é a soma do ascendente e do descendente. A soma do ascendente e do descendente é chamada a altura da célula. A altura da célula menos o entrelinhamento interno é igual à altura em. A altura da célula mais o entrelinhamento externo é igual ao espaçamento entre linhas.  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Usando fontes e texto](using-fonts-and-text.md)
