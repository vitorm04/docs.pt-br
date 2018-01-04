---
title: Como associar dados a um InkCanvas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c8c4f558386edd8da213f8a8af75b6a4c6a98b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Como associar dados a um InkCanvas
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como associar o <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriedade de um <xref:System.Windows.Controls.InkCanvas> para outro <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 O exemplo a seguir demonstra como associar o <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedade para uma fonte de dados.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 O exemplo a seguir declara duas <xref:System.Windows.Controls.InkCanvas> objetos em XAML e estabelece a associação de dados entre eles e outras fontes de dados.  A primeira <xref:System.Windows.Controls.InkCanvas>, chamado `ic`, está associado a duas fontes de dados.  O <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> e <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriedades `ic` estão associados a <xref:System.Windows.Controls.ListBox> objetos, que por sua vez são associados a matrizes definidas em XAML.  O <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, e <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriedades do segundo <xref:System.Windows.Controls.InkCanvas> são vinculados ao primeiro <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
