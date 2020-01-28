---
title: Gráficos e desenho
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746408"
---
# <a name="graphics-and-drawing-in-windows-forms"></a>Elementos gráficos e desenho no Windows Forms
O Common Language Runtime usa uma implementação avançada da GDI (Windows Graphics Device Interface) chamada GDI+. Com o GDI+, você pode criar gráficos, desenhar texto e manipular imagens gráficas como objetos. O GDI+ foi projetado para oferecer desempenho e facilidade de uso. Você pode usar o GDI+ para renderizar imagens gráficas em Windows Forms e controles. Embora não seja possível usar o GDI+ diretamente no Web Forms, você pode exibir imagens gráficas por meio do controle Image do servidor Web.  
  
 Nesta seção, você encontrará tópicos que apresentam os conceitos básicos da programação GDI+. Embora não se deva ser uma referência abrangente, esta seção inclui informações sobre os objetos <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>e <xref:System.Drawing.Color> e explica como executar tarefas como desenhar formas, desenhar texto ou exibir imagens. Para obter mais informações, consulte [referência de GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).  
  
 Se você deseja começar imediatamente, consulte [Introdução à programação de elementos gráficos](getting-started-with-graphics-programming.md). Ele apresenta tópicos sobre como usar código para desenhar linhas, formas, texto e muito mais em Windows Forms.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de elementos gráficos](graphics-overview-windows-forms.md)  
 Fornece uma introdução a classes gerenciadas relacionadas a elementos gráficos.  
  
 [Sobre o Código Gerenciado no GDI+](about-gdi-managed-code.md)  
 Fornece informações sobre as classes GDI+ gerenciadas.  
  
 [Usando Classes de Elementos Gráficos Gerenciadas](using-managed-graphics-classes.md)  
 Demonstra como concluir uma variedade de tarefas usando as classes gerenciadas do GDI+.  
  
## <a name="reference"></a>Referência  
 <xref:System.Drawing>  
 Fornece acesso à funcionalidade gráfica básica do GDI+.  
  
 <xref:System.Drawing.Drawing2D>  
 Fornece funcionalidade avançada bidimensional e de gráfico vetorial.  
  
 <xref:System.Drawing.Imaging>  
 Fornece a funcionalidade avançada de geração de imagens do GDI+.  
  
 <xref:System.Drawing.Text>  
 Fornece a funcionalidade de tipografia de GDI+ avançada. As classes nesse namespace podem ser usadas para criar e usar coleções de fontes.  
  
 <xref:System.Drawing.Printing>  
 Fornece funcionalidade de impressão.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Pintura e renderização de controle personalizado](../controls/custom-control-painting-and-rendering.md)  
 Detalhes sobre como fornecer código para pintar controles.
