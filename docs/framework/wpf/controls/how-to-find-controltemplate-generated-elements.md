---
title: Como localizar elementos gerados por ControlTemplate
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ControlTemplates [WPF], finding elements
- finding ControlTemplate elements [WPF]
ms.assetid: d7b25447-ceff-4bb4-9be5-fd7c40ef00af
ms.openlocfilehash: 3d3032326a0cedc01b4a7ec8e6546044353d6b4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-controltemplate-generated-elements"></a>Como localizar elementos gerados por ControlTemplate
Este exemplo mostra como localizar elementos que são gerados por um <xref:System.Windows.Controls.ControlTemplate>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um estilo que cria um simples <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Button> classe:  
  
 [!code-xaml[FindGeneratedItems#CT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#ct)]  
  
 Para localizar um elemento dentro do modelo depois que o modelo foi aplicado, você pode chamar o <xref:System.Windows.FrameworkTemplate.FindName%2A> método o <xref:System.Windows.Controls.Control.Template%2A>. O exemplo a seguir cria uma caixa de mensagem que mostra o valor atual da largura do <xref:System.Windows.Controls.Grid> dentro do modelo de controle:  
  
 [!code-csharp[FindGeneratedItems#CTFindElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#ctfindelement)]
 [!code-vb[FindGeneratedItems#CTFindElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#ctfindelement)]  
  
## <a name="see-also"></a>Consulte também  
 [Localizar elementos gerados por DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Namescopes XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)  
 [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)
