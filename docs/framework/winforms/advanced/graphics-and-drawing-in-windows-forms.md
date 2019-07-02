---
title: Elementos gráficos e desenho no Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505547"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Elementos gráficos e desenho no Windows Forms
O common language runtime usa uma implementação avançada do Windows GDI Graphics Device Interface () chamado GDI+. Com o GDI+ você pode criar gráficos, desenhar texto e manipular imagens gráficas como objetos. GDI+ é projetado para oferecer desempenho e a facilidade de uso. Você pode usar GDI+ para renderizar imagens gráficas em controles e formulários do Windows. Embora você não pode usar o GDI+ diretamente em Web Forms, você pode exibir imagens gráficas por meio do controle Image do servidor Web.  
  
 Nesta seção, você encontrará tópicos que apresentam os conceitos básicos da programação GDI+. Embora não se destina a ser uma referência abrangente, esta seção inclui informações sobre o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, e <xref:System.Drawing.Color> objetos e explica como executar tarefas como desenhar formas, desenhando texto, ou exibindo imagens. Para obter mais informações, consulte [referência GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Se você deseja começar imediatamente, consulte [Introdução à programação de elementos gráficos](getting-started-with-graphics-programming.md). Ele apresenta tópicos sobre como usar código para desenhar linhas, formas, texto e muito mais em Windows Forms.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de elementos gráficos](graphics-overview-windows-forms.md)  
 Fornece uma introdução a classes gerenciadas relacionadas a elementos gráficos.  
  
 [Sobre o Código Gerenciado no GDI+](about-gdi-managed-code.md)  
 Fornece informações sobre as classes gerenciadas do GDI+.  
  
 [Usando Classes de Elementos Gráficos Gerenciadas](using-managed-graphics-classes.md)  
 Demonstra como a completa uma variedade de tarefas usando o GDI+ classes gerenciadas.  
  
## <a name="reference"></a>Referência  
 <xref:System.Drawing>  
 Fornece acesso à funcionalidade gráficas básicas GDI+.  
  
 <xref:System.Drawing.Drawing2D>  
 Fornece funcionalidade avançada bidimensional e de gráfico vetorial.  
  
 <xref:System.Drawing.Imaging>  
 Fornece a funcionalidade de imagem GDI+ avançada.  
  
 <xref:System.Drawing.Text>  
 Fornece funcionalidade GDI+ tipografia avançada. As classes nesse namespace podem ser usadas para criar e usar coleções de fontes.  
  
 <xref:System.Drawing.Printing>  
 Fornece funcionalidade de impressão.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Pintura e renderização de controle personalizado](../controls/custom-control-painting-and-rendering.md)  
 Detalhes sobre como fornecer código para pintar controles.
