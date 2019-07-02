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
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505112"
---
# <a name="using-fonts-and-text"></a>Usando fontes e texto
Há diversas classes oferecidas por GDI+ e GDI para desenhar texto em formulários do Windows. O GDI+ <xref:System.Drawing.Graphics> classe tem várias <xref:System.Drawing.Graphics.DrawString%2A> métodos que permitem que você especifique vários recursos de texto, como local, delimitadora retângulo, fonte e formato. Além disso, você pode desenhar e medir texto com GDI usando estático <xref:System.Windows.Forms.TextRenderer.DrawText%2A> e <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> métodos oferecidos pelo `TextRenderer` classe. Os métodos GDI também permitem que você especifique a localização, fonte e formato. Você pode escolher GDI ou GDI+ para renderização de texto; No entanto, a GDI geralmente oferece um melhor desempenho e medição de texto mais precisa. Outras classes que contribuem para renderização de texto incluem `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, e `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Construir fontes e famílias de fontes](how-to-construct-font-families-and-fonts.md)  
 Mostra como criar objetos `Font` e `FontFamily`.  
  
 [Como: Desenhar texto em um local especificado](how-to-draw-text-at-a-specified-location.md)  
 Descreve como desenhar texto em um determinado local usando GDI+ e GDI.  
  
 [Como: Desenhar texto encapsulado em um retângulo](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Explica como desenhar texto em um retângulo usando GDI+ e GDI.  
  
 [Como: Desenhar texto com GDI](how-to-draw-text-with-gdi.md)  
 Demonstra como usar GDI para desenhar texto.  
  
 [Como: Alinhar um texto desenhado](how-to-align-drawn-text.md)  
 Mostra como formatar texto GDI+ e GDI.  
  
 [Como: Criar texto Vertical](how-to-create-vertical-text.md)  
 Descreve como desenhar texto alinhado verticalmente com o GDI+.  
  
 [Como: Definir paradas de tabulação em um texto desenhado](how-to-set-tab-stops-in-drawn-text.md)  
 Mostra como desenhar textos com paradas de tabulação com o GDI+.  
  
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
