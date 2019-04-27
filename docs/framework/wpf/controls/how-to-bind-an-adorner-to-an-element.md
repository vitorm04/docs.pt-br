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
ms.openlocfilehash: b6909fec466c2b31a7f4156c43b21a0c724f0217
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018964"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Como: Associar um adorno a um elemento
Este exemplo mostra como programaticamente associar um adorno a um especificado <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Exemplo  
 Para associar um adorno a um determinado <xref:System.Windows.UIElement>, siga estas etapas:  
  
1. Chame o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para obter uma <xref:System.Windows.Documents.AdornerLayer> do objeto para o <xref:System.Windows.UIElement> a ser adornado. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> percorre a árvore visual, iniciando no local especificado **UIElement**e retorna a primeira camada de adorno que encontra. (Se nenhuma camada de adorno for encontrada, o método retornará nulo.)  
  
2. Chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao destino **UIElement**.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) para um <xref:System.Windows.Controls.TextBox> nomeado *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de adornos](adorners-overview.md)
