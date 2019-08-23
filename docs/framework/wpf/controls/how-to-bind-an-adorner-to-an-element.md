---
title: 'Como: Associar um adorno a um elemento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923491"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Como: Associar um adorno a um elemento
Este exemplo mostra como associar programaticamente um adorno a um <xref:System.Windows.UIElement>especificado.  
  
## <a name="example"></a>Exemplo  
 Para associar um adorno a um específico <xref:System.Windows.UIElement>, siga estas etapas:  
  
1. Chame o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para obter um <xref:System.Windows.Documents.AdornerLayer> objeto para o <xref:System.Windows.UIElement> a ser adornado. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>percorre a árvore visual, começando no **UIElement**especificado e retorna a primeira camada de adorno encontrada. (Se nenhuma camada de adorno for encontrada, o método retornará nulo.)  
  
2. Chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao **UIElement**de destino.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) a um <xref:System.Windows.Controls.TextBox> *myTextBox*nomeado.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de adornos](adorners-overview.md)
