---
title: Como associar um adorno a um elemento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: fb419ee5a57e81e7e3bc72ae04fd200703b80cd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Como associar um adorno a um elemento
Este exemplo mostra como programaticamente associar um adorno a determinado <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Exemplo  
 Para associar um adorno a um determinado <xref:System.Windows.UIElement>, siga estas etapas:  
  
1.  Chamar o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para obter um <xref:System.Windows.Documents.AdornerLayer> de objeto para o <xref:System.Windows.UIElement> adornados. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> percorre a árvore visual, iniciando no elemento **UIElement**e retorna a primeira camada de adorno que encontrar. (Se nenhuma camada de adorno for encontrada, o método retornará nulo.)  
  
2.  Chamar o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao destino **UIElement**.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) a um <xref:System.Windows.Controls.TextBox> chamado *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de adornos](../../../../docs/framework/wpf/controls/adorners-overview.md)
