---
title: "Como usar os métodos de rolagem de conteúdo do ScrollViewer"
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
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc9b79ae9b8078bbdc4c41fb0c952237f86fcac8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>Como usar os métodos de rolagem de conteúdo do ScrollViewer
Este exemplo mostra como usar os métodos de rolagem de <xref:System.Windows.Controls.ScrollViewer> elemento. Esses métodos fornecem rolagem incremental do conteúdo, por linha ou por página, em um <xref:System.Windows.Controls.ScrollViewer>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um <xref:System.Windows.Controls.ScrollViewer> chamado `sv1`, que hospeda um filho <xref:System.Windows.Controls.TextBlock> elemento. Porque o <xref:System.Windows.Controls.TextBlock> é maior do que o pai <xref:System.Windows.Controls.ScrollViewer>, barras de rolagem aparecem para habilitar a rolagem. <xref:System.Windows.Controls.Button>elementos que representam os diversos métodos de rolagem são encaixados à esquerda em uma função <xref:System.Windows.Controls.StackPanel>. Cada <xref:System.Windows.Controls.Button> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo chama um método personalizado relacionado que controla o comportamento de rolagem no <xref:System.Windows.Controls.ScrollViewer>.  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 O exemplo a seguir usa o <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> e <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> métodos.  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
