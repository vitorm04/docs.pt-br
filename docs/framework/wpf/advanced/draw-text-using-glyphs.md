---
title: Desenhar texto usando glifos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebce286cd93355feac7e4675ef6b142862740a92
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="draw-text-using-glyphs"></a>Desenhar texto usando glifos
Este tópico explica como usar o nível inferior <xref:System.Windows.Documents.Glyphs> objeto para exibir o texto em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como definir propriedades para um <xref:System.Windows.Documents.Glyphs> objeto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. O <xref:System.Windows.Documents.Glyphs> objeto representa a saída de um <xref:System.Windows.Media.GlyphRun> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Os exemplos assumem que as fontes Arial, Courier New e Times New Roman estão instaladas na pasta C:\WINDOWS\Fonts no computador local.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Este exemplo mostra como definir outras propriedades de <xref:System.Windows.Documents.Glyphs> objetos no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipografia no WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
