---
title: 'Como: Rolar o conteúdo usando a interface IScrollInfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051241"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>Como: Rolar o conteúdo usando a interface IScrollInfo
Este exemplo mostra como rolar conteúdo usando o <xref:System.Windows.Controls.Primitives.IScrollInfo> interface.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra os recursos do <xref:System.Windows.Controls.Primitives.IScrollInfo> interface. O exemplo cria um <xref:System.Windows.Controls.StackPanel> elemento no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que está aninhado em uma pasta pai <xref:System.Windows.Controls.ScrollViewer>. Os elementos filho do <xref:System.Windows.Controls.StackPanel> pode ser rolado logicamente usando os métodos definidos pela <xref:System.Windows.Controls.Primitives.IScrollInfo> interface e conversão para a instância do <xref:System.Windows.Controls.StackPanel> (`sp1`) no código.  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 Cada <xref:System.Windows.Controls.Button> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo aciona um método personalizado associado que controla o comportamento de rolagem em <xref:System.Windows.Controls.StackPanel>. O exemplo a seguir mostra como usar o <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> e <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> métodos; também genericamente mostra como usar todos os métodos de posicionamento que o <xref:System.Windows.Controls.Primitives.IScrollInfo> classe define.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [Visão geral de ScrollViewer](scrollviewer-overview.md)
- [Tópicos de instruções](scrollviewer-how-to-topics.md)
- [Visão geral de painéis](panels-overview.md)
