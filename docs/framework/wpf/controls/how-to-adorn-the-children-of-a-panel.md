---
title: Como adornar os filhos de um painel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 4babbf1df57f340a3f6be218f213ad1c868ec9f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-adorn-the-children-of-a-panel"></a>Como adornar os filhos de um painel
Este exemplo mostra como programaticamente associar um adorno aos filhos de um <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Exemplo  
 Para associar um adorno aos filhos de um <xref:System.Windows.Controls.Panel>, siga estas etapas:  
  
1.  Declarar um novo <xref:System.Windows.Documents.AdornerLayer> objeto e a chamada a `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método para encontrar uma camada de adorno para o elemento cujos filhos serão adornados.  
  
2.  Enumerar todos os filhos do elemento pai e chamada de <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar um adorno a cada elemento filho.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) aos filhos de um <xref:System.Windows.Controls.StackPanel> chamado *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de adornos](../../../../docs/framework/wpf/controls/adorners-overview.md)
