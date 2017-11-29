---
title: "Como alterar a propriedade TextWrapping de forma programática"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 74ddcf55c8918602ecac866913f2007da143f443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>Como alterar a propriedade TextWrapping de forma programática
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como alterar o valor de <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> propriedade programaticamente.  
  
 Três <xref:System.Windows.Controls.Button> elementos são colocados dentro de um <xref:System.Windows.Controls.StackPanel> elemento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Cada <xref:System.Windows.Controls.Primitives.ButtonBase.Click> evento para um <xref:System.Windows.Controls.Button> corresponde a um manipulador de eventos no código. Os manipuladores de eventos usam o mesmo nome que o <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> valor aplicá-las `txt2` quando o botão é clicado. Além disso, o texto em `txt1` (um <xref:System.Windows.Controls.TextBlock> não mostra o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) é atualizada para refletir a alteração na propriedade.  
  
 [!code-xaml[TextWrapProperty#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>  
 <xref:System.Windows.TextWrapping>
