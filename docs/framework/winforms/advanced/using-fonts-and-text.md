---
title: Usando fontes e texto
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18dde7265a07eb45e0211a882b19acc6342e924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="using-fonts-and-text"></a>Usando fontes e texto
Há diversas classes oferecidas por [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] para desenhar textos no Windows Forms. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> classe tem várias <xref:System.Drawing.Graphics.DrawString%2A> métodos que permitem que você especifique vários recursos de texto, como local, delimitadora retângulo, fonte e formato. Além disso, você pode desenhar e medir o texto com [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] usando estático <xref:System.Windows.Forms.TextRenderer.DrawText%2A> e <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> métodos oferecidos pelo `TextRenderer` classe. Os métodos [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] também permitem especificar localização, fonte e formato. É possível escolher [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] ou [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderização de texto; entretanto, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] geralmente oferece melhor desempenho e medição de texto mais precisa. Outras classes que contribuem para a renderização de texto incluem `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, e `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como construir fontes e famílias de fontes](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Mostra como criar objetos `Font` e `FontFamily`.  
  
 [Como desenhar texto em um local especificado](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Descreve como desenhar texto em um local especificado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Como desenhar texto ajustado um retângulo](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Explica como desenhar texto em um retângulo usando [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Como desenhar texto com o GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Demonstra como usar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] para desenhar texto.  
  
 [Como alinhar um texto desenhado](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Mostra como formatar texto [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Como criar texto vertical](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Descreve como desenhar um texto alinhado verticalmente com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Como definir paradas de tabulação em um texto desenhado](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Mostra como desenhar textos com paradas de tabulação com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Como enumerar as fontes instaladas](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Explica como listar os nomes das fontes instaladas.  
  
 [Como criar uma coleção de fontes privada](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Descreve como criar um <xref:System.Drawing.Text.PrivateFontCollection> objeto.  
  
 [Como obter métricas de fontes](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Mostra como obter métricas de fonte, como subida e descida de células.  
  
 [Como usar suavização com texto](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 Explica como usar a suavização ao desenhar texto.  
  
## <a name="reference"></a>Referência  
 <xref:System.Drawing.Font>  
 Descreve essa classe e contém links para todos os seus membros.  
  
 <xref:System.Drawing.FontFamily>  
 Descreve essa classe e contém links para todos os seus membros.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Descreve essa classe e contém links para todos os seus membros.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Descreve essa classe e contém links para todos os seus membros.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Descreve essa classe e contém links para todos os seus membros.
