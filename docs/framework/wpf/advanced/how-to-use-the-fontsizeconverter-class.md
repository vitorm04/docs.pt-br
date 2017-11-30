---
title: Como usar a classe FontSizeConverter
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcf2d7348ca5b6b9d3b2edc44f92afbd46d32594
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>Como usar a classe FontSizeConverter
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar uma instância de <xref:System.Windows.FontSizeConverter> e usá-lo para alterar o tamanho da fonte.  
  
 O exemplo define um método personalizado chamado `changeSize` que converte o conteúdo de um <xref:System.Windows.Controls.ListBoxItem>, conforme definido em uma separada [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] arquivo a uma instância de <xref:System.Double>e posteriormente em um <xref:System.String>. Esse método passa o <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.Windows.FontSizeConverter> objeto, que converte o <xref:System.Windows.Controls.ContentControl.Content%2A> de um <xref:System.Windows.Controls.ListBoxItem> para uma instância de <xref:System.Double>. Esse valor é passado, em seguida, como o valor da <xref:System.Windows.Controls.TextBlock.FontSize%2A> propriedade o <xref:System.Windows.Controls.TextBlock> elemento.  
  
 Este exemplo também define um segundo método personalizado que é chamado `changeFamily`. Este método converte o <xref:System.Windows.Controls.ContentControl.Content%2A> do <xref:System.Windows.Controls.ListBoxItem> para um <xref:System.String>e, em seguida, passa o valor para o <xref:System.Windows.Controls.TextBlock.FontFamily%2A> propriedade o <xref:System.Windows.Controls.TextBlock> elemento.  
  
 Este exemplo não é executado.  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.FontSizeConverter>
