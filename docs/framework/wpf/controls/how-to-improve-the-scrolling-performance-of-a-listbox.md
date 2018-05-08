---
title: Como melhorar o desempenho de rolagem de um ListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>Como melhorar o desempenho de rolagem de um ListBox
Se um <xref:System.Windows.Controls.ListBox> contém muitos itens, a resposta de interface do usuário pode ser lenta quando o usuário rola o <xref:System.Windows.Controls.ListBox> usando a roda do mouse ou arrastando o controle deslizante de uma barra de rolagem. Você pode melhorar o desempenho do <xref:System.Windows.Controls.ListBox> quando o usuário rolar definindo o `VirtualizingStackPanel.VirtualizationMode` anexado a propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
  
## <a name="description"></a>Descrição  
O exemplo a seguir cria um <xref:System.Windows.Controls.ListBox> e define o `VirtualizingStackPanel.VirtualizationMode` anexado a propriedade <xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType> para melhorar o desempenho durante a rolagem.  
  
## <a name="code"></a>Código  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 O exemplo a seguir mostra os dados que usa o exemplo anterior.  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
