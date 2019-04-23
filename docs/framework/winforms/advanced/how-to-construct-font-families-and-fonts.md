---
title: 'Como: construir fontes e famílias de fontes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 0a9dcd00d4bc3e64ae4fc9a1d4884fac18521825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181214"
---
# <a name="how-to-construct-font-families-and-fonts"></a>Como: construir fontes e famílias de fontes
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] agrupa fontes com a mesma face de tipo, mas diferentes estilos em famílias de fontes. Por exemplo, a família de fonte Arial contém as seguintes fontes:  
  
-   Arial Regular  
  
-   Arial Bold  
  
-   Arial Italic  
  
-   Arial Bold Italic  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] usa quatro estilos de famílias de formato: regular, negrito, itálico e negrito e itálico. Adjetivos como *estreito* e *arredondado* não são considerados estilos; em vez disso, eles são parte do nome da família. Por exemplo, Arial Narrow é uma família de fontes com os seguintes membros:  
  
-   Arial Narrow Regular  
  
-   Arial Narrow Bold  
  
-   Arial Narrow Italic  
  
-   Arial Narrow Bold Italic  
  
 Antes de você pode desenhar texto com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você precisa construir uma <xref:System.Drawing.FontFamily> objeto e um <xref:System.Drawing.Font> objeto. O <xref:System.Drawing.FontFamily> objeto Especifica a face de tipos (por exemplo, Arial) e o <xref:System.Drawing.Font> objeto Especifica o tamanho, estilo e unidades.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir constrói uma fonte Arial de estilo regular com um tamanho de 16 pixels. No código a seguir, o primeiro argumento passado para o <xref:System.Drawing.Font.%23ctor%2A> construtor é o <xref:System.Drawing.FontFamily> objeto. O segundo argumento especifica o tamanho da fonte medido em unidades identificadas pelo quarto argumento. O terceiro argumento identifica o estilo.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> é um membro do <xref:System.Drawing.GraphicsUnit> enumeração, e <xref:System.Drawing.FontStyle.Regular> é um membro do <xref:System.Drawing.FontStyle> enumeração.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Consulte também

- [Usando fontes e texto](using-fonts-and-text.md)
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
