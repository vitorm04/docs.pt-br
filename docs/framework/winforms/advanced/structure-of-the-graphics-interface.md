---
title: Estrutura da interface gráfica
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: 9dfffe8ea3f76d89823dfe2ef6bd0e4f3accf8f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956475"
---
# <a name="structure-of-the-graphics-interface"></a>Estrutura da interface gráfica
A interface da classe gerenciada para [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contém cerca de 60 classes, 50 enumerações e 8 estruturas. O <xref:System.Drawing.Graphics> classe é a essência do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funcionalidade; é a classe que realmente desenha linhas, curvas, figuras, imagens e texto.  
  
## <a name="important-classes"></a>Classes importantes  
 Muitas classes trabalham em conjunto com o <xref:System.Drawing.Graphics> classe. Por exemplo, o <xref:System.Drawing.Graphics.DrawLine%2A> método recebe um <xref:System.Drawing.Pen> objeto, que retém os atributos (cor, largura, estilo de traço e assim por diante) da linha a ser desenhada. O <xref:System.Drawing.Graphics.FillRectangle%2A> método pode receber um ponteiro para uma <xref:System.Drawing.Drawing2D.LinearGradientBrush> objeto, que funciona com o <xref:System.Drawing.Graphics> objeto para preencher um retângulo com uma cor que muda gradualmente. <xref:System.Drawing.Font> e <xref:System.Drawing.StringFormat> objetos influenciam a maneira como um <xref:System.Drawing.Graphics> objeto Desenha texto. Um <xref:System.Drawing.Drawing2D.Matrix> objeto armazena e manipula a transformação global de um <xref:System.Drawing.Graphics> objeto, que é usado para girar, dimensionar e Inverter imagens.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fornece várias estruturas (por exemplo, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, e <xref:System.Drawing.Size>) para organizar os dados de gráficos. Além disso, determinadas classes servem principalmente como tipos de dados estruturados. Por exemplo, o <xref:System.Drawing.Imaging.BitmapData> classe é um auxiliar para o <xref:System.Drawing.Bitmap> classe e o <xref:System.Drawing.Drawing2D.PathData> classe é um auxiliar para o <xref:System.Drawing.Drawing2D.GraphicsPath> classe.  
  
 O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] define várias enumerações, que são coleções de constantes relacionadas. Por exemplo, o <xref:System.Drawing.Drawing2D.LineJoin> enumeração contém os elementos <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, e <xref:System.Drawing.Drawing2D.LineJoin.Round>, que especificam os estilos que podem ser usados para unir duas linhas.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de elementos gráficos](graphics-overview-windows-forms.md)
- [Sobre o Código Gerenciado no GDI+](about-gdi-managed-code.md)
- [Usando Classes de Elementos Gráficos Gerenciadas](using-managed-graphics-classes.md)
