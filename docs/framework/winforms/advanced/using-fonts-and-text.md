---
title: Usando fontes e texto
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769403"
---
# <a name="using-fonts-and-text"></a>Usando fontes e texto
Há diversas classes oferecidas por [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] para desenhar textos no Windows Forms. O [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> classe tem várias <xref:System.Drawing.Graphics.DrawString%2A> métodos que permitem que você especifique vários recursos de texto, como local, delimitadora retângulo, fonte e formato. Além disso, você pode desenhar e medir texto com [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] usando o estático <xref:System.Windows.Forms.TextRenderer.DrawText%2A> e <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> métodos oferecidos pelo `TextRenderer` classe. Os métodos [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] também permitem especificar localização, fonte e formato. É possível escolher [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] ou [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] para renderização de texto; entretanto, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] geralmente oferece melhor desempenho e medição de texto mais precisa. Outras classes que contribuem para renderização de texto incluem `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, e `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Construir fontes e famílias de fontes](how-to-construct-font-families-and-fonts.md)  
 Mostra como criar objetos `Font` e `FontFamily`.  
  
 [Como: Desenhar texto em um local especificado](how-to-draw-text-at-a-specified-location.md)  
 Descreve como desenhar texto em um local especificado [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Como: Desenhar texto encapsulado em um retângulo](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Explica como desenhar texto em um retângulo usando [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md)  
 Demonstra como usar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] para desenhar texto.  
  
 [Como: Alinhar um texto desenhado](how-to-align-drawn-text.md)  
 Mostra como formatar texto [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] e [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Como: Criar texto Vertical](how-to-create-vertical-text.md)  
 Descreve como desenhar um texto alinhado verticalmente com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Como: Definir paradas de tabulação em um texto desenhado](how-to-set-tab-stops-in-drawn-text.md)  
 Mostra como desenhar textos com paradas de tabulação com [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Como: Enumerar as fontes instaladas](how-to-enumerate-installed-fonts.md)  
 Explica como listar os nomes das fontes instaladas.  
  
 [Como: Criar uma coleção de fontes privada](how-to-create-a-private-font-collection.md)  
 Descreve como criar um <xref:System.Drawing.Text.PrivateFontCollection> objeto.  
  
 [Como: Obter métricas de fontes](how-to-obtain-font-metrics.md)  
 Mostra como obter métricas de fonte, como subida e descida de células.  
  
 [Como: Usar suavização com texto](how-to-use-antialiasing-with-text.md)  
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
