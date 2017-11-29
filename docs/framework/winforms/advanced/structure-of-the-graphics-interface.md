---
title: "Estrutura da interface gráfica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd1da930df151869ea3e891da7057f44ed0a4603
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-of-the-graphics-interface"></a>Estrutura da interface gráfica
A interface da classe gerenciada para [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] contém cerca de 60 classes, 50 enumerações e 8 estruturas. O <xref:System.Drawing.Graphics> classe é a essência do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funcionalidade; ela é a classe que realmente desenha linhas, curvas, ilustrações, imagens e texto.  
  
## <a name="important-classes"></a>Classes importantes  
 Muitas classes trabalhar junto com o <xref:System.Drawing.Graphics> classe. Por exemplo, o <xref:System.Drawing.Graphics.DrawLine%2A> método recebe um <xref:System.Drawing.Pen> objeto, que contém atributos (cor, largura, estilo de traço e assim por diante) da linha a ser desenhada. O <xref:System.Drawing.Graphics.FillRectangle%2A> método pode receber um ponteiro para um <xref:System.Drawing.Drawing2D.LinearGradientBrush> objeto, que funciona com o <xref:System.Drawing.Graphics> objeto para preencher um retângulo com uma cor gradualmente alteração. <xref:System.Drawing.Font>e <xref:System.Drawing.StringFormat> objetos influenciam o modo de um <xref:System.Drawing.Graphics> objeto Desenha texto. Um <xref:System.Drawing.Drawing2D.Matrix> objeto armazena e manipula as transformações de mundo de um <xref:System.Drawing.Graphics> objeto, que é usado para girar, dimensionar e inverter as imagens.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]fornece várias estruturas (por exemplo, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, e <xref:System.Drawing.Size>) para organizar os dados de gráficos. Além disso, determinadas classes servem principalmente como tipos de dados estruturados. Por exemplo, o <xref:System.Drawing.Imaging.BitmapData> classe é um auxiliar a <xref:System.Drawing.Bitmap> classe e o <xref:System.Drawing.Drawing2D.PathData> classe é um auxiliar de <xref:System.Drawing.Drawing2D.GraphicsPath> classe.  
  
 O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] define várias enumerações, que são coleções de constantes relacionadas. Por exemplo, o <xref:System.Drawing.Drawing2D.LineJoin> enumeração contém os elementos <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, e <xref:System.Drawing.Drawing2D.LineJoin.Round>, que especifica os estilos que podem ser usados para unir duas linhas.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de elementos gráficos](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [Sobre o Código Gerenciado no GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Usando Classes de Elementos Gráficos Gerenciadas](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
